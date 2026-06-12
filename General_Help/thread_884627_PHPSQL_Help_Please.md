---
title: "PHP/SQL Help Please"
date: 2008-08-09
forum: General Help
---

### Post by Pioneer5000 on 2008-08-09
I Keep getting this error, can anyone help me out with this?


Fatal error: require() [function.require]: Failed opening required '1' (include_path='.:/usr/share/php:/usr/share/pear') in mydirectory/to/files on line 3.

I have got through Package Manager and installed php_pear but that didnt seem to help.

---

### Post by ProbablyX on 2008-08-09
Hello Pioneer5000,

What is on your line 3? 
Also does the directory /usr/share/pear exist?

---

### Post by Pioneer5000 on 2008-08-09
(include_path='.:/usr/share/php:/usr/share/pear')

usr/share/php  does exist but
usr/share/pear does not

how do i install or well what do i put in there?

---

### Post by nimbrant on 2008-08-09
can you post what you have for line 3 in your code.
it sounds like there is a problem finding the file you are trying to require.
the problem might not be with your include_path, but the path you are using in the require line.

---

### Post by Pioneer5000 on 2008-08-10
```


require($_SERVER = ("/home/bob/Website/Testwebsite/htdocs")."/Config/config.php");
	$connection = @mysql_connect($db_host, $db_user, $db_password);
	mysql_select_db ($db_name, $connection);

ive tried using

require '/home/bob/Website/Testwebsite/htdocs/Config/config.php';

and 

require $_SERVER['DOCUMENT_ROOT'] . '/Config/config.php'; 


```

nothing seems to be working? and if you havnt guessed it im new to all this but i have got it working before... dont know why its not working now but this was a while ago i have since formated hdd and reinstalled everything.

This is the error im getting at the momment:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '')' at line 1

---

### Post by nimbrant on 2008-08-10
im not sure what you are trying to do with this
> require($_SERVER = ("/home/bob/Website/Testwebsite/htdocs")."/Config/config.php");

but i would stick with the full absolute path until you get it working.
What is the error you get when you use this require line?
> require '/home/bob/Website/Testwebsite/htdocs/Config/config.php';

I assume your db variables are set in config.php, so if that file does not get included then you will definitely be getting mysql errors.

---

### Post by Pioneer5000 on 2008-08-11
Im using the line you stated above 
```
require '/home/bob/Website/Testwebsite/htdocs/Config/config.php'; 
```
and this is the error im getting:


[I]You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '')' at line 1
[/I]


Line 1 only has <?  opening php tag?


This is odd dont know why its doing this and im sure ive spelt path correctly and path exists...

---

### Post by nimbrant on 2008-08-11
the error does not seem to indicate a problem with the path.

is it possible for you to post more of your code including the config.php?

if you have error logging turned on, you may also want to take a look at your apache error log, which may give a more useful error message.

---

### Post by Pioneer5000 on 2008-08-12
PHP part of script:
```

<?php

	include '/home/bob/Website/Testwebsite/htdocs/Config/config.php'; 
	$connection = @mysql_connect($db_host, $db_user, $db_password);
	mysql_select_db ($db_name, $connection);
	
	
	$name = $_POST[text_name];
	$completed = $_POST[text_address];
	$comments =$_POST[text_comments];
	
	$query = "INSERT INTO default2 (autoID, date, completed, comments) VALUES (NULL, '$name','$address','$comments)";
	mysql_query ($query, $connection) or die (mysql_error());
	
?>


```

Config:

```

<?php

		$db_host = "localhost";
		$db_user = "default";
		$db_password = "default";
		$db_name = "default1";


?>

```

---

### Post by Pioneer5000 on 2008-08-12
```


$query = "INSERT INTO default2 (autoID, date, completed, comments) VALUES (NULL, '$name','$address','$comments)";
	mysql_query ($query, $connection) or die (mysql_error());


```

seems to be causing the error.

---

### Post by nimbrant on 2008-08-12
try adding a single quote ' after $comments in your $query line

---

