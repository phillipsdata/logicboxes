# LogicBoxes API #

LogicBoxes is a domain registrar/hosting platform. This API is a wrapper for the [LogicBoxes web API](http://manage.logicboxes.com/kb/answer/744), each command is mapped one-to-one with a Class and Method. For example, [registering a domain](http://manage.logicboxes.com/kb/answer/752) requires the domains/register.json API command, which is executed via LogicboxesDomains::register().

The LogicBoxes platform is used by many different resellers, all of which are fully compatible with this integration. These include, but are not limited to:

- [Directi](http://manage.directi.com/kb/answer/744)
- [LogicBoxes](http://manage.logicboxes.com/kb/answer/744)
- [NetEarthOne](http://manage.netearthone.com/kb/answer/744)
- [Resell.biz](http://cp.us2.net/kb/answer/744)
- [ResellerClub](http://manage.resellerclub.com/kb/answer/744)


## Requirements ##

* PHP 5.1.3 or greater

### Using the API ###

```php
<?php
require_once "logicboxes_api.php";

$user = "YOUR_USER_ID";
$key = "YOUR_API_KEY";
$sandbox = true; // true for testing, false for live

$api = new LogicboxesApi($user, $key, $sandbox);

// Create a new instance of the command class we want to use
$api->loadCommand("logicboxes_domains");
$domains = new LogicboxesDomains($api);

$vars = array('domain-name' => array("mydomain"), 'tlds' => array("com"));

print_r($domains->available($vars)->response());
?>
```