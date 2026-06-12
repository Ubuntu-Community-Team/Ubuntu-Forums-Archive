---
title: "NEWBIE DITCHED windows love UBUNTU but need help desperately"
date: 2008-10-31
forum: General Help
---

### Post by lollylegs on 2008-10-31
What I have done:
installed Ubuntu successfully:)
installed web server successfully\\:D/

What I dont know what do is set up my local server for testing:cry:

In windows apache\htdocs was the document root which had no permissions so I could use that for my web documents and programs that needed to be placed there eg phpmyadmin.

However when i try to use ubuntu the same way i dont have permissions to do what i want in /var/www the apache documentroot folder.

So could someone please help me setting up my directory and file structure as i want to use codeigniter which usually goes in my windows apache/htdocs folder.

Can a virtual host be set up if you dont have a domain name or do i have to use an alias.

Unfortunately Im fairly new to apache configuration as well.

If any kind person will take the time to help i would greatly appreciate the help.

regards
marea (lollylegs)
australia](*,)

---

### Post by ashmew2 on 2008-10-31
I would recommend you try out [this]("http://ubuntuforums.org/showthread.php?t=456422") thread and read unless someone else shows up to save the day ;)

---

### Post by ju2wheels on 2008-10-31
Hi, I will explain two methods, the first being the preferred and the second will be a little easier since you are new to Ubuntu and probably not too familiar with the command line.

1. Open Applications -> Accessories -> Terminal and type the following:
```

sudo cp /path/to_file /var/www/webpath/

```

If your path has a space in it you must use a backslah:

```

sudo cp /path/to_file_with\ space /var/www/

```

The command "sudo" elevates your permission to administrator so you can copy files into and do administrative tasks in areas of the file system where you can potentially damage your install. Unlike Windws, this is what keeps Linux so secure.

2. Again, open terminal, this time we will give administrator permissions to Nautilus (the file explorer application) so this way you have a GUI with permission to copy files into /var/www. Please be careful with method as moving, deleting the wrong things could damage your install.

```

gksudo nautilus

```

gksudo is used to give administrative permission to graphical applications, where as sudo is used for command line applications.

Apache's configuration files are pretty much the same as in Windows, except they are extremely segmented into separate files which allow Linux to automate the configuration of Apache through other applications. The configuration files are found at /etc/apache2 if you are familiar with modifying them on Windows. It will take a few minutes to figure out how they split it but once you understand it should be straight forward if you are used to configuring it by hand, and I believe named virtual hosts is enabled by default. 

Either way you should be able to access the website using either "localhost" on the same machine or the machine's ip as the domain name on a different machine.

---

### Post by lH)4~mK0e on 2008-10-31
Here is what I dug up on phpmyadmin:

[[COLOR="Blue"]phpmyadmin Help[/COLOR]]("https://help.ubuntu.com/community/phpMyAdmin")

I like webmin, myself.  I can configure all of my server modules without having to put a monitor and keyboard on my server.

[[COLOR="Blue"]Webmin[/COLOR]]("http://www.webmin.com/")

As far as a apache's functionality, if you could do it in the "other" O/S it should be functional no matter what O/S you are using.

Looking at the permissions for my /var/www, I see it's owned by the root user and root group.  Copy ups using scp or ftp will require you to use the "sudo" command.  If you are a developer than you already know the dangers of uploading invalidated code so I wouldn't think you were implying of editing it directly from /var/www ;)

scp is the easiest way to do it so make sure you do

sudo apt-get install openssh-server

I also think you can upload your documents straight from the webmin interface, or at least you could at one point.

---

### Post by lollylegs on 2008-10-31
Thank you everyone for the help.
I will take all advice on board and hopefully can get windows out of my brain and concentrate on linux directory and filesystem.

Love you all for your help

Marea (lollylegs):lolflag:

---

### Post by lollylegs on 2008-10-31
Thanks to all the replies

---

