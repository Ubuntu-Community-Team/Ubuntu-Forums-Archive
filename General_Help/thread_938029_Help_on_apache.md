---
title: "Help on apache"
date: 2008-10-04
forum: General Help
---

### Post by dr_cerebro on 2008-10-04
I have read a lot of webpages to make apache to work, but I've not been succesful.

This is the problem: My wife need a program to manage patient files.  She has a program for Windows to do that, but I only have one extra computer, with Linux installed, and her old Sony Vaio laptop with Windows XP is a piece of junk, so she wants a new computer. I want her to use Linux, and she agreed, but I can't even install the program.

I need to install this:

[http://www.care2x.org/manuals/en_install_auto_2_1.htm](http://www.care2x.org/manuals/en_install_auto_2_1.htm)

into the apache main server page.

I read a lot of tutorials and howto's, but i cannot even access my own test pages... it says Forbidden...I think I'm in a lot of trouble... I can't access mysql, I don't even know the password

I need a lot of help

I will uninstall apache2, php5 and mysql

Could somebody please check it out and tell me (step by step...with examples), how to do it?

Thank you

---

### Post by homemadejam on 2008-10-04
Have yoy had a look at XAMPP?
[http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html)

Its so much easier to use and install I think

Jam

---

### Post by cariboo on 2008-10-04
I wouldn't install XAMPP as it is not an official package and won't get updated when new versions come out.

I had a look at the installation procedure and the current version of php installed in Hardy is to new you need php4 in order to run the program.

The only way you are going to get php4 is to downgrade to dapper. the iso is available here:

[http://mirror.mcs.anl.gov/pub/ubuntu-iso/CDs/6.06/](http://mirror.mcs.anl.gov/pub/ubuntu-iso/CDs/6.06/)

Be aware that support for 6.06.2 LTS is no longer available as it has been superceded by 8.0.4.1 LTS

If you decide to continue the installation procedure it is pretty simple. Download the complete package and extract it to your home directory. Copy the files in the dirctory that was created when you extracted the package to /var/www. You will have to do this as root. In a terminal type:

```
cd ~/care2x
```

then

```
sudo cp * /var/www/
```

once you have copied the files, you will have to change the permissions of the files as the installer needs write permission to a lot of files: First in a terminal type:

```
cd /var/www
```

Next to change permissions type in the same termihnal:

```
sudo chmod -R 777 *
```

You should now be ready to install the application, open firefox and type:

```
http://localhost/installer/install.php
```

From there it is just a matter of filling in the information and following the prompts.

I didn't do a full installation as I was not willing to downgrade to php4

Jim

---

### Post by dr_cerebro on 2008-10-04
Hi, thanks for your reply.

After:

```
sudo cp * /var/www/
```

it displays a message:

```
cp:se omite el directorio `htdocs'
```

it does not work that way.

Any ideas?

> **cariboo907 said:**
> I wouldn't install XAMPP as it is not an official package and won't get updated when new versions come out.

I had a look at the installation procedure and the current version of php installed in Hardy is to new you need php4 in order to run the program.

The only way you are going to get php4 is to downgrade to dapper. the iso is available here:

[http://mirror.mcs.anl.gov/pub/ubuntu-iso/CDs/6.06/](http://mirror.mcs.anl.gov/pub/ubuntu-iso/CDs/6.06/)

Be aware that support for 6.06.2 LTS is no longer available as it has been superceded by 8.0.4.1 LTS

If you decide to continue the installation procedure it is pretty simple. Download the complete package and extract it to your home directory. Copy the files in the dirctory that was created when you extracted the package to /var/www. You will have to do this as root. In a terminal type:

```
cd ~/care2x
```

then

```
sudo cp * /var/www/
```

once you have copied the files, you will have to change the permissions of the files as the installer needs write permission to a lot of files: First in a terminal type:

```
cd /var/www
```

Next to change permissions type in the same termihnal:

```
sudo chmod -R 777 *
```

You should now be ready to install the application, open firefox and type:

```
http://localhost/installer/install.php
```

From there it is just a matter of filling in the information and following the prompts.

I didn't do a full installation as I was not willing to downgrade to php4

Jim

---

### Post by bodhi.zazen on 2008-10-04
you forgot the "-R"

cp **[color=red]-R**[/color] * /var/www/

---

### Post by Calmatory on 2008-10-04
If apache causes trouble, you could try [lighttpd](http://www.lighttpd.net/), which is lightier and simplier. Doesn't have as much functionality though.

---

### Post by dr_cerebro on 2008-10-04
> **bodhi.zazen said:**
> you forgot the "-R"

cp **[color=red]-R**[/color] * /var/www/

It works !

Thank you very much.

Now I have another problem.  When I open my browser and type:

[HTML]http://localhost/htdocs/installer/install.php[/HTML]

it just opens the default download box to download "install.php" and asks me to open it with gedit, or save to disk.

Do you know how can I fix this?

---

### Post by bodhi.zazen on 2008-10-04
See this link :

[http://www.ubuntugeek.com/apache2-web-server-installation-with-php4-and-php5-support-in-ubuntu.html](http://www.ubuntugeek.com/apache2-web-server-installation-with-php4-and-php5-support-in-ubuntu.html)

you need to add :

> DirectoryIndex index.html index.cgi index.pl index.php index.xhtml

---

