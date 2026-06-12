---
title: "[SOLVED] Bamboo Invoice???"
date: 2008-08-02
forum: General Help
---

### Post by uzzo2 on 2008-08-02
Was wondering if anyone here has any experience with this invoicing program. it runs off of a localhost server, so i've installed xampp sucessfully and created the database for it at myphpadmin. but i'm not quite sure how and it what order to upload the bamboo files to the database. i keep getting errors when trying to upload them, thanks in advance for any advice.

---

### Post by uzzo2 on 2008-08-02
here's one of the errors i'm getting when trying to upload to the database.
anyone got any ideas?
SQL query:

<?php if (!defined('BASEPATH')) exit('No direct script access allowed');

MySQL said: Documentation
#1064 - You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '<?php  
if (!defined('BASEPATH')) exit('No direct script access allowed')' at line 1

---

### Post by gkestrel on 2008-08-10
Hi Uzzo2

I have successfully installed bambooinvoice on Gutsy, I only wanted to use it on a local machine so i dont have any experience of uploading it to a website. I also used the mysql database.  The way i did it was to download bambooinvoice and extract it using achive manager to a folder named bambooinvoice. Next i made a new folder in /var/www/mycompanyname/ then i copied the bambooinvoice folder into the new folder that i just made.

I then  edited the following two files in the
 /var/www/mycompanyname/bambooinvoice/bamboo_system_files/application/config/

/var/www/mycompanyname/bambooinvoice/bamboo_system_files/application/config/config.php and edited the following line

$config['index_page'] = "http://localhost/bambooinvoice/index.php"; 
to
$config['index_page'] = "http://localhost/mycompanyname/bambooinvoice/index.php"; 
and then saved the file.

I then edited /var/www/mycompanyname/bambooinvoice/bamboo_system_files/application/config/database.php
and edited the following three lines

$db['default']['hostname'] = "localhost";
$db['default']['username'] = "";
$db['default']['password'] = "";
to
$db['default']['hostname'] = "localhost";
$db['default']['username'] = "myusername";
$db['default']['password'] = "mypassword"; 
and then saved the file.

Next i made a new database called bambooinvoice.
Finally i opened firefox and browsed to
[http://localhost/mycompanyname/bambooinvoice/](http://localhost/mycompanyname/bambooinvoice/)

Note if you get errors here your settings in the two config files need checking and altering if needed.

  If your settings are correct you should see a webpage saying bambooinvoice is not installed yet and do you want to install it. Just install bambooinvoice and fill in any details needed for username and password. bambooinvoice is then installed and ready for use. Just log in and use the program. Hope this helps you out, if you get stuck just ask and i will do my best to help you further.

---

### Post by michaelzap on 2008-08-10
I'm actually going to try out Bamboo on our web server this week. It looks really nice, and I have yet to find a decent invoicing program for Linux. The error that you received is strange (since that's not an SQL query but rather PHP code), which makes me think that the files have not been copied correctly and you should verify that first.

---

### Post by uzzo2 on 2008-08-16
> **gkestrel said:**
> Hi Uzzo2

I have successfully installed bambooinvoice on Gutsy, I only wanted to use it on a local machine so i dont have any experience of uploading it to a website. I also used the mysql database.  The way i did it was to download bambooinvoice and extract it using achive manager to a folder named bambooinvoice. Next i made a new folder in /var/www/mycompanyname/ then i copied the bambooinvoice folder into the new folder that i just made.

I then  edited the following two files in the
 /var/www/mycompanyname/bambooinvoice/bamboo_system_files/application/config/

/var/www/mycompanyname/bambooinvoice/bamboo_system_files/application/config/config.php and edited the following line

$config['index_page'] = "http://localhost/bambooinvoice/index.php"; 
to
$config['index_page'] = "http://localhost/mycompanyname/bambooinvoice/index.php"; 
and then saved the file.

I then edited /var/www/mycompanyname/bambooinvoice/bamboo_system_files/application/config/database.php
and edited the following three lines

$db['default']['hostname'] = "localhost";
$db['default']['username'] = "";
$db['default']['password'] = "";
to
$db['default']['hostname'] = "localhost";
$db['default']['username'] = "myusername";
$db['default']['password'] = "mypassword"; 
and then saved the file.

Next i made a new database called bambooinvoice.
Finally i opened firefox and browsed to
[http://localhost/mycompanyname/bambooinvoice/](http://localhost/mycompanyname/bambooinvoice/)

Note if you get errors here your settings in the two config files need checking and altering if needed.

  If your settings are correct you should see a webpage saying bambooinvoice is not installed yet and do you want to install it. Just install bambooinvoice and fill in any details needed for username and password. bambooinvoice is then installed and ready for use. Just log in and use the program. Hope this helps you out, if you get stuck just ask and i will do my best to help you further.

this sounds like the same procedure that i went through, here's the link from the forum where a guy was trying to help me there. can you look at it and see if that's the same procedure as you listed here. thanks for the help.
[http://forums.bambooinvoice.org/index.php/forums/viewthread/402/](http://forums.bambooinvoice.org/index.php/forums/viewthread/402/)

---

### Post by michaelzap on 2008-08-16
I recently installed Bamboo Invoice on a remote server (not Ubuntu, but Linux). I didn't have any issues following the install instructions. Basically you just need to copy the PHP files to their proper location, set permissions for a few directories (as indicated in the instructions), create a new database, edit the config file to match your context, and use the installer script to do the rest (create database tables and data, etc.).

At what point exactly are you having trouble, and what is the error that you're receiving?

---

### Post by uzzo2 on 2008-08-16
> **michaelzap said:**
> I recently installed Bamboo Invoice on a remote server (not Ubuntu, but Linux). I didn't have any issues following the install instructions. Basically you just need to copy the PHP files to their proper location, set permissions for a few directories (as indicated in the instructions), create a new database, edit the config file to match your context, and use the installer script to do the rest (create database tables and data, etc.).

At what point exactly are you having trouble, and what is the error that you're receiving?

i'm having trouble uploading the files to the database. one of the errors is listed above

---

### Post by michaelzap on 2008-08-16
> **uzzo2 said:**
> i'm having trouble uploading the files to the database. one of the errors is listed above

Given the error that you posted and that this is the second time that you've used the phrase "upload the files to the database", I have to wonder if you're not trying to copy the PHP code into the database?

If so, that's not at all what you need to do. The files get copied to a directory in your web root, not entered into your database.

The installation instructions are pretty clear and specific, so try following them step-by-step and indicating where you have trouble and what you were trying to do when it happened.

---

### Post by uzzo2 on 2008-08-16
> **michaelzap said:**
> Given the error that you posted and that this is the second time that you've used the phrase "upload the files to the database", I have to wonder if you're not trying to copy the PHP code into the database?

If so, that's not at all what you need to do. The files get copied to a directory in your web root, not entered into your database.

The installation instructions are pretty clear and specific, so try following them step-by-step and indicating where you have trouble and what you were trying to do when it happened.

i was trying to upload the bambooinvoice files to the localhost database, is that not what you're supposed to do?

---

### Post by uzzo2 on 2008-08-16
ok, i tried it over again following gkestrels method. i got to the part about making a new folder in var. for some reason, it won't give the option to create a new folder there.

---

### Post by gkestrel on 2008-08-17
In order to be able to make a folder in the /var/www/ folder you need to use the terminal and type 

sudo mkdir /var/www/mycompanyname

or you can use nautilus as root by typing in a terminal

 gksudo nautilus

this will allow you to make a folder in /var/www/ and also make it easy to copy the bamboo invoice files into the folder you made.

To edit the fies you need to be sudo also

sudo gedit /var/www/mycompanyname/bambooinvoice/bamboo_system_files/application/config/config.php

and 

sudo gedit /var/www/mycompanyname/bambooinvoice/bamboo_system_files/application/config/database.php

Sorry about not making it clear you would need root permission to make the folder and to be able to edit the files in my previous post. Just try it again and let us know if you hit any problems and we will do our best to help you out.

---

### Post by uzzo2 on 2008-08-18
> **gkestrel said:**
> In order to be able to make a folder in the /var/www/ folder you need to use the terminal and type 

sudo mkdir /var/www/mycompanyname

or you can use nautilus as root by typing in a terminal

 gksudo nautilus

this will allow you to make a folder in /var/www/ and also make it easy to copy the bamboo invoice files into the folder you made.

To edit the fies you need to be sudo also

sudo gedit /var/www/mycompanyname/bambooinvoice/bamboo_system_files/application/config/config.php

and 

sudo gedit /var/www/mycompanyname/bambooinvoice/bamboo_system_files/application/config/database.php

Sorry about not making it clear you would need root permission to make the folder and to be able to edit the files in my previous post. Just try it again and let us know if you hit any problems and we will do our best to help you out.

that's ok, thanks for trying to help me, i did everything that you told me to the best of my knowledge and here's what's happening now
Not Found

The requested URL /lakecountry/bambooinvoice was not found on this server.
Apache/2.2.9 (Unix) DAV/2 mod_ssl/2.2.9 OpenSSL/0.9.8h PHP/5.2.6 mod_apreq2-20051231/2.6.0 mod_perl/2.0.4 Perl/v5.10.0 Server at localhost Port 80

---

### Post by gkestrel on 2008-08-18
I seem to remember having a simalar problem when i set it up. After rechecking what edits i put in to the file

/var/www/mycompanyname/bambooinvoice/bamboo_system_files/application/config/config.php

i found i had made a note that i had commented out the following line

//$config['base_url']	= "http://www.bambooinvoice.org/";

by adding the two // in front of it and then it worked for me. I was then able to get to the index page and install it. Try that first and let us know if it does not work.

---

### Post by uzzo2 on 2008-08-18
> **gkestrel said:**
> I seem to remember having a simalar problem when i set it up. After rechecking what edits i put in to the file

/var/www/mycompanyname/bambooinvoice/bamboo_system_files/application/config/config.php

i found i had made a note that i had commented out the following line

//$config['base_url']	= "http://www.bambooinvoice.org/";

by adding the two // in front of it and then it worked for me. I was then able to get to the index page and install it. Try that first and let us know if it does not work.

ok, tried that and i'm still getting the same thing, not found on the server. i'll paste the config.php file i edited, maybe i've done something wrong there.

//$config['base_url']	= "http://localhost/bambooinvoice/";
$config['index_page'] = "http://localhost/lakecountry/bambooinvoice/index.php";

---

### Post by gkestrel on 2008-08-20
Ok i have copied and pasted the only the first part of the config.php file that i modified, so you can compare it to yours 

<?php  

if (!defined('BASEPATH')) exit('No direct script access allowed');



/*

|--------------------------------------------------------------------------

| Base Site URL

|--------------------------------------------------------------------------

|

| URL to your Code Igniter root. Typically this will be your base URL,

| WITH a trailing slash:

|

|	[http://www.your-site.com/](http://www.your-site.com/)

|

*/

//$config['base_url']	= "http://localhost/bambooinvoice/";

// This should be a full address, with a slash.  For example, here's what

// I use on bambooinvoice.org:

//$config['base_url']	= "http://www.bambooinvoice.org/";
// added this to the file;

//$config['base_url']	= "http://localhost/mycompanyname/";

/*

|--------------------------------------------------------------------------

| Index File

|--------------------------------------------------------------------------

|

| Typically this will be your index.php file, unless you've renamed it to

| something else. If you are using mod_rewrite to remove the page set this

| variable so that it is blank.

|

*/

$config['index_page'] = "http://localhost/mycompanyname/bambooinvoice/index.php";






here is a copy of my database file

<?php  if (!defined('BASEPATH')) exit('No direct script access allowed');

/*

| -------------------------------------------------------------------

| DATABASE CONNECTIVITY SETTINGS

| -------------------------------------------------------------------

| This file will contain the settings needed to access your database.

|

| For complete instructions please consult the "Database Connection"

| page of the User Guide.

|

| -------------------------------------------------------------------

| EXPLANATION OF VARIABLES

| -------------------------------------------------------------------

|

|	['hostname'] The hostname of your database server.

|	['username'] The username used to connect to the database

|	['password'] The password used to connect to the database

|	['database'] The name of the database you want to connect to

|	['dbdriver'] The database type. ie: mysql.  Currently supported:

				 mysql, mysqli, postgre, odbc, mssql

|	['dbprefix'] You can add an optional prefix, which will be added

|				 to the table name when using the  Active Record class

|	['pconnect'] TRUE/FALSE - Whether to use a persistent connection

|	['db_debug'] TRUE/FALSE - Whether database errors should be displayed.

|	['active_r'] TRUE/FALSE - Whether to load the active record class

|	['cache_on'] TRUE/FALSE - Enables/disables query caching

|	['cachedir'] The path to the folder where cache files should be stored

|

| The $active_group variable lets you choose which connection group to

| make active.  By default there is only one group (the "default" group).

|

*/



$active_group = "default";



$db['default']['hostname'] = "localhost";
$db['default']['username'] = "my mysql username here";

$db['default']['password'] = "my sql password here ";
/*

|	$db['default']['username'] = "root";

|	$db['default']['password'] = "root";
*/

$db['default']['database'] = "bambooinvoice";

$db['default']['dbdriver'] = "mysql";

$db['default']['dbprefix'] = "bamboo_";

$db['default']['active_r'] = TRUE;

$db['default']['pconnect'] = TRUE;

$db['default']['db_debug'] = FALSE;

$db['default']['cache_on'] = FALSE;

$db['default']['cachedir'] = "";





?>

compare it to yours and make any needed changes.

Now a few questions, what happens when you browse to

[http://localhost/](http://localhost/) 

can you see the companyname that you entered into the config file, if yes what happens if you click on the company name, do you see your bamboo invoice folder, if yes what happens when you click on the bamboo invoice folder. if so what happens when you click on it. Finally have you set up 
your database and added yourself as a database user, and set a password.

Try that first and let me know how you go on.

---

### Post by uzzo2 on 2008-08-20
> In order to be able to make a folder in the /var/www/ folder you need to use the terminal and type

sudo mkdir /var/www/mycompanyname

one thing i didn't mention and i don't know if it's important or not. i couldn't use slashes when naming the file in var. consequently i didn't use the www either in front of the company name.

---

### Post by uzzo2 on 2008-08-20
> 
Now a few questions, what happens when you browse to

[http://localhost/](http://localhost/)

can you see the companyname that you entered into the config file, if yes what happens if you click on the company name, do you see your bamboo invoice folder, if yes what happens when you click on the bamboo invoice folder. if so what happens when you click on it. Finally have you set up
your database and added yourself as a database user, and set a password.

all i get to when i go to my localhost is pretty much a blank screen with xampp and logo and several links at the bottom for different languages/countries.
as far as setting up a username, i didn't do any of that setting up xampp. maybe i've missed something altogether.

---

### Post by gkestrel on 2008-08-22
Hi there sorry for the delay in getting back to you I was working away and only just got back.  Ok it was not until i read your last reply i remembered that you were using xammp and that makes things a little different to set up. In order to check how things will work for you i thought i had better set up xampp myself and see how it all works,

I followed the following howto to set up xammp

[http://ubuntuforums.org/showthread.php?t=223410](http://ubuntuforums.org/showthread.php?t=223410)

if you are seeing the xammp page with the language options it means its all set up correctly.

did you set up the security for xammp if not in the terminal type

sudo /opt/lampp/lampp security

and set up your passwords, dont forget to type yes when asked to do so on some of the questions or you will not be able to set your passwords.

Next i used the following community howto for apache mysql php 

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

the only difference is with xammp you have to access mysql slightly differently

sudo /opt/lampp/bin/mysql -u root -p

it may ask for your sudo password first if so enter it.
it will ask you to enter the password you set for root mysql user in the lamp security  then you will see the mysql prompt

mysql>

I will run through each command you need to enter, just copy and paste them into the terminal directly after the mysql prompt.

first we create a database called bambooinvoice with

create database bambooinvoice;

you should see		Query OK, 0 rows affected and then the mysql prompt again.

next we need to create a new user with all privileges with

GRANT ALL PRIVILEGES ON *.* TO 'yourusername'@'localhost' IDENTIFIED BY 'yourpassword' WITH GRANT OPTION;

you should see		Query OK, 0 rows affected and then the mysql prompt again.

not quite shure wether the next bit is needed or not but i did

GRANT ALL PRIVILEGES ON *.* TO 'bamboouser'@'localhost' IDENTIFIED BY 'yourpassword' WITH GRANT OPTION;

you should see		Query OK, 0 rows affected and then the mysql prompt again.

to exit mysql type quit at the mysql prompt and you will be returned to the normal user prompt.

now to set up bambooinvoice. First in your home folder create a folder called 

public_html

inside this folder make a folder called

yourcompanyname

extract the bambooinvoice_086.zip into the yourcompanyname folder, to make things easier i renamed the bambooinvoice_086 folder to bamboinvoice.

next open the bambooinvoice folder and go to the  bambooinvoice/bamboo_system_files/application/config/ folder

Now we need to edit config.php 

change the two lines you see below, then save the file

$config['base_url']	= "http://localhost/graham/mycompanyname/bambooinvoice/";
$config['index_page'] = "index.php"; 

Next we need to edit database.php

find the section listed below make the changes to the username and password, then save the file.

$active_group = "default";



$db['default']['hostname'] = "localhost";

$db['default']['username'] = "your mysql username here";

$db['default']['password'] = "your mysql password here";

$db['default']['database'] = "bambooinvoice";

$db['default']['dbdriver'] = "mysql";

$db['default']['dbprefix'] = "bamboo_";

$db['default']['active_r'] = TRUE;

$db['default']['pconnect'] = TRUE;

$db['default']['db_debug'] = FALSE;

$db['default']['cache_on'] = FALSE;

$db['default']['cachedir'] = "";


Next open a terminal and enter the following two commands to make the invoices_temp folder and the /img/logo folder writable

sudo chmod 0777 /home/username/public_html/mycompanyname/bambooinvoice/invoices_temp

sudo chmod 0777 /home/username/public_html/mycompanyname/bambooinvoice/img/logo

if you want to use your own logo first rename logo.jpg to logo.jpg.old then copy your logo into the /img/logo folder and rename it to logo.jpg

Now we must link the public_html folder to lampps htdocs with the following command

sudo ln -s ~/public_html /opt/lampp/htdocs/$USER

Finally we can browse to 

[http://localhost/yourusername](http://localhost/yourusername)

you should now see the folder mycompanyname - left click on it - you should now see the bambooinvoice folder - left click on it and you should see a page saying bambooinvoice is not installed yet and do you want to install it. Answer the questions and install it - then log in and the program is ready to use.

hope this helps you.

---

### Post by uzzo2 on 2008-08-23
> Finally we can browse to

[http://localhost/yourusername](http://localhost/yourusername)
ok, when i go here it actually has 2 links, a bambooinvoice_086 link that was modified on 7/9/08 (must have been when i set the original database up) and a public_html link that i created per your instructions.
when i click on the bambooinvoice_086 link i get this.

An Error Was Encountered

Bamboo could not connect to your database with the information provided in bamboo_system_files/application/config/database.php

now when i click on the public_html link, i then see my lakecountry link, lakecountry being the company name. i then click on that link and see the bambooinvoice link and after left clicking on that i get this.
Not Found

The requested URL /phil/lakecountry/bambooinvoice/index.php/install/not_installed was not found on this server.
at this point i am wondering if computer homicide is actually a jailable offense...LOL
thanks for all the help just the same.

---

### Post by gkestrel on 2008-08-23
Just need to check a few things first before we go any further. When i browse to [http://localhost/myusername](http://localhost/myusername)

 i see the folder mycompanyname, if i then click on that i then see bambooinvoice, and if i click on that i see the install page.

So I need to know where you made the folder mycompanyname first of all.

The last instructions that i gave you were made for using xampp, so first go over each step one by one until you reach the browse to [http://localhost/yourusername/](http://localhost/yourusername/) 

it cant hurt to double check that you did not miss any steps just to be on the safe side.

The error message you are getting just means that the two lines in the config.php file need altering until it can find the install.php file correctly.

Look carefully at both the error message line on the displayed web page and the address bar in your web browser, and you should get a clue as to were it is looking, for example I found that i was getting an address like this

/localhost/username/http://localhost/username/mycompanyname/babooinvoice/

notice it was saying /localhost/username in front of the http bit and that was what needed to be removed out of the config file.

so play around with the two lines below, but make a note first of what they are saying before making any changes so you can go back to the original version if need be.

this is what my xammp version config.php file looks like

$config['base_url'] = "http://localhost/graham/mycompanyname/bambooinvoice/";
$config['index_page'] = "index.php";

if you still get no further after checking each step one by one and changing the settings in config.php and database.php then please copy and paste the contents of each file here for me to have a look at for you.

---

### Post by uzzo2 on 2008-08-23
i FINALLY figured it out with your help, the problem was here.

$config['base_url'] = "http://localhost/phil/mycompanyname/bambooinvoice/";
it should have been,

$config['base_url'] = "http://localhost/phil/public_html/mycompanyname/bambooinvoice/";
and voila, just like that,it's DONE, thanks a heap and sorry to be such a PITA.

---

### Post by gkestrel on 2008-08-23
Glad to hear its working for you, I was very pleased to be able to help you out. Hope you find bambooinvoice useful i have finished testing it out and am going to be using it for real.

---

### Post by uzzo2 on 2008-08-23
> **gkestrel said:**
> Glad to hear its working for you, I was very pleased to be able to help you out. Hope you find bambooinvoice useful i have finished testing it out and am going to be using it for real.
thanks again, i am hoping that i will eventually get to the other side of the learning curve with linux/ubuntu. then i will be able to give advice rather than having to ask for it. :):):)

---

