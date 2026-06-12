---
title: "I can't find Ubuntu Lamp under packages - Please Help?"
date: 2009-09-10
forum: Installation &amp; Upgrades
---

### Post by cazzy on 2009-09-10
Hello,
 
I want to install Lamp (Apache, PHP, MySQL) on my Ubuntu Jaunty Desktop Edition 32 bit PC. 
 
There are many tutorials online showing how to do the installation, but I am unable to ascertain the size of the LAMP package. I have been to [http://packages.ubuntu.com](http://packages.ubuntu.com) but I am unable to find the relevant package.
 
My mobile internet connection is not always reliable and I pay for every MegaByte, therefore I do need to ascertain the size of the relevant package before downloading.
 
Questions:
1) Where can I go to find out the size of the Lamp Package that is retrieved from the repository and installed via Synaptic?
2) (My Linux computer is not connected to the internet due to modem driver issues.) If possible, I would prefer to download the Lamp Package from the internet ( [http://packages.ubuntu.com](http://packages.ubuntu.com) ) using my Windows PC, and then write the appropriate Lamp Package to CD. Is this possible? If so, can somebody please provide me with the url where I can download the package?
 
I look forward to your help.
 
Thank you.
 
Best Regards,
Cazzy

---

### Post by AlexanderDGreat on 2009-09-10
Hello, not to be disrespectful, but if you will have problems connecting to the internet in your Ubuntu machine, believe me, it's an uphill road ahead of you.

I read somewhere here the question is Ubuntu for you? And one of the requirements is constant connection to the internet.

Kind regards. =)

---

### Post by cazzy on 2009-09-11
> **AlexanderDGreat said:**
> Hello, not to be disrespectful, but if you will have problems connecting to the internet in your Ubuntu machine, believe me, it's an uphill road ahead of you.

I read somewhere here the question is Ubuntu for you? And one of the requirements is constant connection to the internet.

Kind regards. =)
Hi, 
 
Thanks for your input.
 
I am still unable to locate the size for the lamp server. If anybody can assist then I would be most appreciative.
 
Thanks.
Regards,
Cazzy

---

### Post by ahbart on 2009-09-11
There was a Lamp dummy package in the repository long time ago. 
Now you just have to select apache2, php5 and mysql-server in synaptic.

What you could do is select the packages you want to install in synaptic. Than go to file (still within synaptic) and select create download script. 
I'm not sure if you can use that under windows though. But maybe you can boot from a live disk on a pc with a broadband connection and run the download script from there.

---

### Post by AlexanderDGreat on 2009-09-12
Yup, here's what I did before:

L - Linux
A - installed apache2
M - installed mysql-server
P - installed php5

via Synaptic

Sorry, I don't know about the LAMP, but you can always go here: [http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html) (not tried yet though)

---

### Post by rob-ward on 2009-09-12
If I try to install LAMP on my machine(new install this week)  then this is the result

rob@rob-netbook:~$ sudo apt-get install apache2 php5 mysql-server libapache2-mod-auth-mysql php5-mysql phpmyadmin 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  apache2-mpm-prefork apache2-utils apache2.2-common dbconfig-common
  libapache2-mod-php5 libapr1 libaprutil1 libdbd-mysql-perl libdbi-perl
  libgd2-xpm libhtml-template-perl libmcrypt4 libnet-daemon-perl
  libplrpc-perl libpq5 libt1-5 mysql-client-5.0 mysql-server-5.0
  mysql-server-core-5.0 php5-common php5-gd php5-mcrypt
Suggested packages:
  apache2-doc apache2-suexec apache2-suexec-custom virtual-mysql-client
  mysql-client postgresql-client php-pear dbishell libgd-tools
  libipc-sharedcache-perl libmcrypt-dev mcrypt mysql-doc-5.0 tinyca mailx
The following packages will be REMOVED
  libgd2-noxpm
The following NEW packages will be installed
  apache2 apache2-mpm-prefork apache2-utils apache2.2-common dbconfig-common
  libapache2-mod-auth-mysql libapache2-mod-php5 libapr1 libaprutil1
  libdbd-mysql-perl libdbi-perl libgd2-xpm libhtml-template-perl libmcrypt4
  libnet-daemon-perl libplrpc-perl libpq5 libt1-5 mysql-client-5.0
  mysql-server mysql-server-5.0 mysql-server-core-5.0 php5 php5-common
  php5-gd php5-mcrypt php5-mysql phpmyadmin
0 upgraded, 28 newly installed, 1 to remove and 0 not upgraded.
Need to get 45.1MB of archives.
After this operation, 139MB of additional disk space will be used.
Do you want to continue [Y/n]? 


Basically you need to download 45meg and it will use 139 meg, you may be better trying to find somewhere that you can download the packages on someone elses web connection and then install them on your machine.

Hope that helps.

---

### Post by cazzy on 2009-09-12
> **rob-ward said:**
>  
 
Basically you need to download 45meg and it will use 139 meg, you may be better trying to find somewhere that you can download the packages on someone elses web connection and then install them on your machine.
 
Hope that helps.
 
Hi,
 
Thank you to everybody who have taken the time to respond to my request.
 
A special thank you also goes to Rob for his valued input.
 
Many Thanks.
 
Regards,
Cazzy

---

### Post by rob-ward on 2009-09-12
It no problem, that's what we are all here for.

---

### Post by johnocon999 on 2009-09-13
[B]Re: I can't find Ubuntu Lamp under packages - Please Help?

[B]To Whom it concerns,

[/B]I know you havent mentioned wether or not your intention is to use Joomla with Lampp server, but if it is you should consider the following before doing an installation.  If you intend using Lamp with Joomla you will need the following version of xampp for linux.  Its xampp 1.7.1 and you can download it from here  [/B] [http://sourceforge.net/projects/xampp/files/XAMPP Linux/]("http://sourceforge.net/projects/xampp/files/XAMPP%20Linux/")
[B]
The reason for this is Joomla will not run using the newest release of lamp as it uses a newer version of php.

[B]best of luck
[/B][/B]

---

### Post by newsoft on 2009-09-13
thanks everyone for your efforts :) Keep it up...thumbs UP

---

