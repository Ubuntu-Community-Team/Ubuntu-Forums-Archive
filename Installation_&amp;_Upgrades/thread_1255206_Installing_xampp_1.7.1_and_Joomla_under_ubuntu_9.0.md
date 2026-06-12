---
title: "Installing xampp 1.7.1 and Joomla under ubuntu 9.04 Linux."
date: 2009-09-01
forum: Installation &amp; Upgrades
---

### Post by johnocon999 on 2009-09-01
[SIZE=4]**Installing xampp 1.7.1 and Joomla under ubuntu 9.04 Linux.**[/SIZE] (by johnocon999)


[SIZE=3]**Installing xampp**[/SIZE]
-----------------
1: Download xampp 1.7.1 for Linux to your desktop. **[SIZE=4]NB: IT MUST BE XAMPP 1.7.1[/SIZE]**  Download from here - [http://sourceforge.net/projects/xampp/files/XAMPP Linux/]("http://sourceforge.net/projects/xampp/files/XAMPP%20Linux/")

2: Extract to /opt folder in your **system files area**. The best method of doing this is to do it through the console. You seem to get more permission problems when you dont do it through the console. (I tried it a thousand times from the desktop without complete success. It will extract but will not run without errors).

Use the following command - **sudo tar xvfz xamp-linux-1.7.1.tar.gz -C /opt**

3: To start the server do the following in your console.  **sudo /opt/lampp/lampp start**

4: All services should start.  
-To stop the server running **sudo /opt/lampp/lampp stop**  
-or to restart if its already running **sudo /opt/lampp/lampp restart**

5: To check your installation open browser window and type **[http://localhost]("http://localhost/")** (If the installation was successful you should see xampp main page. Choose your language. Check to see all is working correctly. Check to see that you can enter the myphpadmin section of xampp and create a database without any errors. Hopefully success!


**[SIZE=3]Installing vsftpd (ftp server)[/SIZE]**
------------------
I know ftphd comes with xampp. But I found it easier to configure vsftpd (as I am a novice)
1: Open System > Administrator > Symantic packet manager and search for and install vsftphd
2: To configure vsftpd open the following file **/etc/vsftpd.conf** to change the default settings.

---------------------------------------------------------------------------------------------------------------------
When you open the file just remove the hash symbol from infront of the following commands
**#Local_enable=yes**  (by uncommenting this you will be able to log into ftp using your linux username and password)
**#write_enable=yes**  (will allow you to download and upload files)
---------------------------------------------------------------------------------------------------------------------

The configuration file consists of many configuration parameters. The information about each parameter is available in the configuration file. Alternatively, you can refer to the man page, man 5 vsftpd.conf for details of each parameter.

To run the vsftpd daemon use the following command:

 **sudo /etc/init.d/vsftpd start **

Hopefully success.


**[SIZE=3]Installing Joomla[/SIZE]**
-----------------

1: Download latest version of Joomla from joomla.org

2: The Joomla archive you just downloaded will have to be extracted to the** /opt/lampp/htdocs/** folder. Open up console window and type **sudo nautilus**. Now go to the **opt/lampp/lampp/htdocs** and Create a folder called **myjoomlasite**. Right click on folder and set permissions **OWNER ROOT CREATE AND DELETE FILES, GROUP ROOT CREATE AND DELETE FILES Allowing executing - NO**. If you are not able to extract to this folder after changing the permissions. Open the sharing tab and SHARE the folder. You should now be able to extract the archives contents to Myjoomlasite.

3: To see if your installation was successful so far, open browser window and type **[http://localhost/myjoomlasite](http://localhost/myjoomlasite)** and press return. Hopefully you will be brought to the index.php page and be able to start setting up your joomla site. NB: Make sure no sql errors are displayed at the top of the page.

4: Before proceeding anymore open your xampp server **[http://localhost/xampp](http://localhost/xampp)**, click on **myphpadmin **and create a mysql database to use with your site. setup a user name for the database under the privileges section and grant all privileges click go. Your database should now be setup.

5: Go back to your joomla setup and continue with the following steps

-** select language** >next
-** pre installation **check (this checks if all the minimum system requirements are met) >next
-** Licence** >next
- **Database** (enter database details)
      Database type: MYSQL 
    Host:Localhost 
    Database Username:
    Password:
    Database Name: (what u called your joomla database)
        >next.
-** FTP LAYER** has to be setup if you wish to add components to joomla under linux. We have already setup vsftpd so this should be a breeze. You will be required to enter a USERNAME,PASSWORD AND FTP PATH. Username is your linux username:**** password is your linux username password) In order to get the ftp path click Auto find path. Hopefully your path will have being found eg /myjoomlasite
>next

- **CONFIGURATION **   - by default the username is admin.  And the password is the password you set. The rest is self explanatory
>next

- Before you do anything else you must remove the installation directory from your myjoomlasite folder. Go to **/opt/lampp/lampp/htdocs/myjoomlasite **and delete the installation directory.

*you should now be able to login into your sites administrator section.*  To view your site go to **[http://localhost/myjoomlasite](http://localhost/myjoomlasite)**

Hope this tutorial has being of use.   I was hours trying to work this out as Im new to Linux (only a week). And I love it!

---

### Post by gnuyoga on 2009-09-01
Well written, 

But if i use ubuntu i would still prefer everything to be done the apt-get way instead of spending time downloading the source and doing the traditional way.

---

### Post by johnocon999 on 2009-09-01
Thanks for the advice. will take it on board.

---

### Post by Sairin_Lote on 2009-09-05
on the 4th step of Joomla! installation (Database) i get this error : 
> Unable to connect to the database:Could not connect to MySQL

although i created a database 

anyone who might now what should i do?
thank you in advance


EDIT: solved it.

i had spelled wrongly some account names:/ sorry for this

---

### Post by johnocon999 on 2009-09-05
> **Sairin_Lote said:**
> on the 4th step of Joomla! installation (Database) i get this error : 


although i created a database 

anyone who might now what should i do?
thank you in advance


EDIT: solved it.

i had spelled wrongly some account names:/ sorry for this


Hope you've succeeded with your installation :guitar:

---

### Post by cariboo on 2009-09-05
Thanks for the tutorial, but I and I'm sure quite a lot of others would rather use packages from the repositories, that way we get security updates with out having to reinstall every time there is a new version.

To install the LAMP stack go to System-->Administration-->Synaptic Package Manager-->Edit-->Mark Packages by task, and select LAMP from the menu and click apply.

---

### Post by johnocon999 on 2009-09-05
> **cariboo907 said:**
> Thanks for the tutorial, but I and I'm sure quite a lot of others would rather use packages from the repositories, that way we get security updates with out having to reinstall every time there is a new version.

To install the LAMP stack go to System-->Administration-->Synaptic Package Manager-->Edit-->Mark Packages by task, and select LAMP from the menu and click apply.

Hi. I know you can do things using the repositories but sometimes the versions in the repositories are the newest versions and are not compatible with other applications that you wish to use them alongside with.  This is why I downloaded an older version of Xampp to use with Joomla.  The current version will not work as it has a newer version of PHP packaged in it. I know what your saying about package manager and the security updates, its great the way it works like that.

I also installed quanta +.    I installed this from Synaptic manager. When you have it installed and run it you will get 2 warnings at the start saying the following

Some applications required for full functionality are missing:

- KImageMapEditor [[http://www.nongnu.org/kimagemap/]](http://www.nongnu.org/kimagemap/]) - editing HTML image maps will not be available;
- Cervisia [[http://www.kde.org/apps/cervisia]](http://www.kde.org/apps/cervisia]) - CVS management plugin will not be available.

The funny thing is both were installed by synaptic and you get the following errors. Why you may ask?  Well I can only answer for Cervisia at the moment.  Synaptic installs the latest version of cervisia which has being developed using a newer version of kde.  Quanta +  will not recognise it because it uses an older version of KDE.  Will put up a post when I finally solve the problem. Quanta + is a good program though,  dont get me wrong.

Anyway must dash. Pasta is done!
Over and Out:guitar:

---

### Post by josephe on 2009-09-05
Great tutorial and all was going very well when I removed my root user access from mysql, I now cannot get back into SQL even though I did create a user with all priviledges before I took out root.

How do I either reset the users to default or log into mysql as a different person

Appreciate any help

Joseph

---

### Post by johnocon999 on 2009-09-06
> **josephe said:**
> Great tutorial and all was going very well when I removed my root user access from mysql, I now cannot get back into SQL even though I did create a user with all priviledges before I took out root.

How do I either reset the users to default or log into mysql as a different person

Appreciate any help

Joseph

Well Josephe.
I had the exact same problem.  When you got everything running properly you decided to try and make the server more secure by removing the root user from the database. What I really should have done was just change the password for the root user.   As Im only 2 weeks using this operating system permissions was what drove me demented.  So when this problem happened to me I just uninstalled the whole lot and installed it again to get my root user back. 

I will have a fool around at this today and see if I can come up with an answer for you.  
Later
Over and Out Johno

---

### Post by josephe on 2009-09-06
Hey Johno
 
Thanks for the prompt reply, glad to see I'm not the only one being driven a bit crazy by this. I have been putting off the uninstall as a last resort, but I think you're right that its prob the easier route to go.
 
Will let you know how that goes.
 
Joseph

---

### Post by josephe on 2009-09-07
One more thing Johnno,
How do I uninstall please?  can't find LAMP or LAMPP in package manager

Thanks

Joseph

---

### Post by johnocon999 on 2009-09-08
> **josephe said:**
> One more thing Johnno,
How do I uninstall please?  can't find LAMP or LAMPP in package manager

Thanks

Joseph

well Joseph.
sorry was away for a couple of days. To uninstall lampp use the following command from the console.

rm -rf /opt/lampp


This will remove joomla as well as its installed in the htdocs folder under lampp.  After deleting restart your machine.  I know its not windows but it helped me.

---

### Post by josephe on 2009-09-10
Hi there

Ok, so far so good, managed to get a site up so thanks for all the help with that,
BUT when I try to change certain elements of the template I get 
"the parameter file /templates/ja_purity/params.ini is [COLOR=red]unwritable[/COLOR]!	"
and

Operation Failed!: failed to open file /opt/lampp/htdocs/myjoomlasite/templates/ja_purity/params.ini for writing.

I presume this is something to do with the access to the /opt folder, but I'm not sure how to fix it, any ideas??


Thanks


Joseph

---

### Post by johnocon999 on 2009-09-10
> **josephe said:**
> Hi there

Ok, so far so good, managed to get a site up so thanks for all the help with that,
BUT when I try to change certain elements of the template I get 
"the parameter file /templates/ja_purity/params.ini is [COLOR=red]unwritable[/COLOR]!    "
and

Operation Failed!: failed to open file /opt/lampp/htdocs/myjoomlasite/templates/ja_purity/params.ini for writing.

I presume this is something to do with the access to the /opt folder, but I'm not sure how to fix it, any ideas??


Thanks


Joseph


Well Joseph. Heres the solution.

[SIZE=3]**Firstly set the permissions on your myjoomlasite folder by doing the following.**[/SIZE]
-------------------------------------------------------------------------------
1: open console and type command **SUDO NAUTILUS**
2: If it requests your password, so be it.
3: Your file browser should now appear on the screen
4: Open file system** /opt/lampp/htdocs/myjoomlasite**
5: Right click on the **MyJoomlaSite** folder and select permissions.  For the owner select your "**username**" and for Folder Access "**create and delete files**" and for file access select "**read and write**".  Click **apply permissions** to enclosed folder.  Hopefully that will fix the writing problem but not the ftp problem.


[SIZE=3]**Secondly you will have to enter your ftp details in your configuration.php file**[/SIZE]
-------------------------------------------------------------------------------

1: Its located in the following directory **File system/opt/lampp/htdocs/myjoomlasite/configuration.php.**
You will have to enter the ftp details in this file as it seems they are not added by Joomla.  I just discovered I had this problem as well.

Find the following lines in your file.  The only thing you should have to change is give ftp your linux **username and linux password**,  and enter the directory structure required to find your ftp folder. It should be the following **/opt/lampp/htdocs/myjoomlasite**

var $ftp_host = '127.0.0.1';
var $ftp_port = '21';
var $ftp_user = '[COLOR=Red]your linux username[/COLOR]';
var $ftp_pass = '[COLOR=Red]your linux password[/COLOR]';
var $ftp_root = '[COLOR=Red]/opt/lampp/htdocs/myjoomlasite[/COLOR]';
var $ftp_enable = '1';
var $force_ssl = '0';


That should solve your problems. 
Over and Out JohnO:guitar:

---

### Post by josephe on 2009-09-10
Hi Johno
 
Thanks for yet another step along my road to Joomla master status 
I actually started doing the first part of what you suggest but I think I did something wrong cause it did'nt change anything, but I did not do the ftp part, so that prob didn't help.
 
O ja one more question, if I want to set up another site with Joomla, I guess I repeat the install process in another folder under Lampp, so "mysecondjoomlasite"?
 
Have a good weekend
 
Joseph

---

### Post by johnocon999 on 2009-09-11
Sound. I will do. Indian on the way.
Yes Joseph just repeat the process for another joomla site.

Have a good weekend yerself.:popcorn:

---

### Post by hotstepperk on 2009-09-12
Hey. 

Im using your tutorial now, but on the sourceforge site, there's a newer version of Xampp. In your tutorial you clearly state that one should only use the version number 1.7.1. why is that?

---

### Post by johnocon999 on 2009-09-12
> **hotstepperk said:**
> Hey. 

Im using your tutorial now, but on the sourceforge site, there's a newer version of Xampp. In your tutorial you clearly state that one should only use the version number 1.7.1. why is that?


The reason I use that is its the version that works with Joomla 1.5

Newer versions of xampp are packaged with newer version of PHP which is not supported by Joomla 1.5

best of luck
Over and Out Johno:guitar:

---

### Post by hotstepperk on 2009-09-12
ok then. in the installation, after i installed xampp, the localhost site kept sending me back a test page for the apache web server, as oposed to the xampp main page. i had previously installed lamp using synaptic using cariboo907's instructions.from terminal, is says another web server daemon and MySql daemon are running. Help!!

---

### Post by johnocon999 on 2009-09-12
> **hotstepperk said:**
> ok then. in the installation, after i installed xampp, the localhost site kept sending me back a test page for the apache web server, as oposed to the xampp main page. i had previously installed lamp using synaptic using cariboo907's instructions.from terminal, is says another web server daemon and MySql daemon are running. Help!!
[B]
Try the following[/B]
-----------------------

1: firstly you should go back to package manager and uninstall the lamp you installed using package manager. Find the package and mark it for uninstallaton.  When its uninstalled see if you can view your xampp main page in the browser. [B][http://localhost](http://localhost)
[/B]
2: If that does not work try restarting your xampp server using the following command in the terminal 
**sudo /opt/lampp/lampp restart**    Now try and view in the browser again** [http://localhost](http://localhost)**

3: If that does not work I would remove the xampp installation also using the following command   
   ** rm -rf /opt/lampp **

4: Restart Linux and following the instructions to install xampp again.  Go to the terminal and start your server [B]sudo /opt/lampp/lampp start

[/B]5: Hopefully that shoud do it. check your browser once again at [http://localhost/](http://localhost/)

Over and Out
JohnO

---

### Post by hotstepperk on 2009-09-12
ok. its worked fine up until the pre-installation check for joomla, where there configuration.php is not writable and two of the recommended settings (Safe Mode and Register Globals) are both on. any way I can amend this?

---

### Post by hotstepperk on 2009-09-12
managed to sort that out, now i'd like to know why Autofind ftp path isn't working. it keeps saying the XML response that was returned from the server is invalid.i've kept the username and password of that i use to log into ubuntu.

---

### Post by hotstepperk on 2009-09-12
ok, fixed the last two issues. the latter  of which was caused because i had renamed the "configuration.php-dis" file to "configuration.php" 

Now, i cant get the autofind ftp path link to work, saying "Unable to auto-detect the FTP root folder." I'm really starting to get frustrated with this single part of the installation bugging me. I've put my username and password the ones I use to login. Anything i'm not doing?

---

### Post by johnocon999 on 2009-09-12
> **hotstepperk said:**
> ok, fixed the last two issues. the latter  of which was caused because i had renamed the "configuration.php-dis" file to "configuration.php" 

Now, i cant get the autofind ftp path link to work, saying "Unable to auto-detect the FTP root folder." I'm really starting to get frustrated with this single part of the installation bugging me. I've put my username and password the ones I use to login. Anything i'm not doing?

try manually typing in the path to see if that works eg /myjoomlasite

---

### Post by hotstepperk on 2009-09-13
Tried that, still tells me
 "The FTP settings are not valid or your FTP server is not compatible with Joomla!:
Could not access the specified FTP directory."

what happens if I just clicked on next and finished the installation? how would I be able to verify if FTP is working, and if its not, how to get it working once i'm done with the installation?

---

### Post by johnocon999 on 2009-09-13
> **hotstepperk said:**
> Tried that, still tells me
 "The FTP settings are not valid or your FTP server is not compatible with Joomla!:
Could not access the specified FTP directory."

what happens if I just clicked on next and finished the installation? how would I be able to verify if FTP is working, and if its not, how to get it working once i'm done with the installation?


Did you install vsftp as I explained?
**[SIZE=3]Installing vsftpd (ftp server)[/SIZE]**
------------------
I know ftphd comes with xampp. But I found it easier to configure vsftpd (as I am a novice)
1: Open System > Administrator > Symantic packet manager and search for and install vsftphd
2: To configure vsftpd open the following file **/etc/vsftpd.conf** to change the default settings.

---------------------------------------------------------------------------------------------------------------------
[SIZE=5]**This is extremely important**[/SIZE]
When you open the file just remove the hash symbol from infront of the following commands
**#Local_enable=yes**  (by uncommenting this you will be able to log into ftp using your linux username and password)
**#write_enable=yes**  (will allow you to download and upload files)
---------------------------------------------------------------------------------------------------------------------

The configuration file consists of many configuration parameters. The information about each parameter is available in the configuration file. Alternatively, you can refer to the man page, man 5 vsftpd.conf for details of each parameter.

To run the vsftpd daemon use the following command:

 **sudo /etc/init.d/vsftpd start **

Just double check it and see.

---

### Post by hotstepperk on 2009-09-14
I've followed the tutorial to the letter, but its still not working. If i just input the root path (/myjoomlasite) and click on next without verifing the link, will it still work?

---

### Post by johnocon999 on 2009-09-14
your guess is as good as mine.  I didnt come across the problem.

---

### Post by hotstepperk on 2009-09-15
Do i REALLY need FTP then? :)

---

### Post by johnocon999 on 2009-09-16
> **hotstepperk said:**
> Do i REALLY need FTP then? :)

you will need it if you intend to install modules or components in joomla. eg. virtue mart

---

### Post by hotstepperk on 2009-09-19
FINALLY GO IT WORKING!!

it refused to connect using vsftpd but with proftp (i think its called, the one that comes with xampp) it worked like a charm. I've just managed to install a template now. much thanks for the tutorial, though confirm on the vsftpd part. Cheers!  :KS :KS

---

### Post by johnocon999 on 2009-09-20
> **hotstepperk said:**
> FINALLY GO IT WORKING!!

it refused to connect using vsftpd but with proftp (i think its called, the one that comes with xampp) it worked like a charm. I've just managed to install a template now. much thanks for the tutorial, though confirm on the vsftpd part. Cheers!  :KS :KS


Great stuff.:guitar:

---

### Post by VioletsPie on 2009-10-05
all I get is 'It worked!' 

how do I uninstall LAMPP?

edit: well i followed the wikidirections and had to agree for it to take out a massive amount of kde apps. oh well

---

