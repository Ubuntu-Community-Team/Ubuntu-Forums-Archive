---
title: "Authorization help..."
date: 2008-09-20
forum: General Help
---

### Post by Shiv4m on 2008-09-20
I'm the only user on my laptop and I can't put any files in specific folders, how do I give myself permission so that I can put files in locked folders like opt directory.

---

### Post by mb_webguy on 2008-09-20
Well, those folders are locked for a reason, so unless you're absolutely sure you know what you're doing, it's generally best to leave them alone.

Having said that, your user account doesn't have appropriate privileges to write to those folders.  You have to temporarily gain root privileges to do that sort of thing.  You do this using the sudo or gksu commands in the terminal.  Use sudo to run command line apps as root, and gksu to run GUI apps as root.  Therefore, to copy a file to the /opt directory from the command line, you would use the command "sudo cp /path/to/file /opt".  To run Nautilus with root privileges -- which is *highly* unadvised -- you would use the command "gksu nautilus".  Be warned:  improper or careless use of running Nautilus as root can seriously hose your system!

---

### Post by Shiv4m on 2008-09-20
I want to install XAMPP and it's telling me to put the extracted folder in the opt directory, I don't know any other way to install it but that way.

---

### Post by Bakon Jarser on 2008-09-20
You should use gksudo instead of gksu.

---

### Post by mb_webguy on 2008-09-20
If you follow [these instructions]("http://ubuntuforums.org/showthread.php?t=223410"), it will tell you exactly which commands you need to use.

---

### Post by Shiv4m on 2008-09-20
Mainly I want to do this is because I want to install XAMPP is there any easier way to install it?
XAMPP extracted folder is on desktop what should I do now?

---

### Post by mb_webguy on 2008-09-20
> **Bakon Jarser said:**
> You should use gksudo instead of gksu.

In Ubuntu, gksudo is just a link to gksu, so it doesn't matter which you use.

```
matt@the-tardis:~$ ls -lsh /usr/bin/gksudo
0 lrwxrwxrwx 1 root root 4 2008-08-21 17:06 /usr/bin/gksudo -> gksu

```

---

### Post by mb_webguy on 2008-09-20
> **Shiv4m said:**
> Mainly I want to do this is because I want to install XAMPP is there any easier way to install it?
XAMPP extracted folder is on desktop what should I do now?

Is there some particular reason why you want to install XAMPP?  Isn't XAMPP just an all-in-one installer for a LAMP server?

Open Synaptic and go to Edit->Mark Packages By Task, and check LAMP Server, then apply the changes to install the software.

---

### Post by Shiv4m on 2008-09-20
> **mb_webguy said:**
> Is there some particular reason why you want to install XAMPP?  Isn't XAMPP just an all-in-one installer for a LAMP server?

Open Synaptic and go to Edit->Mark Packages By Task, and check LAMP Server, then apply the changes to install the software.

Thanks, didn't even know there was a program called LAMP :KS

---

### Post by mc4100 on 2008-09-20
> **Shiv4m said:**
> Thanks, didn't even know there was a program called LAMP :KS
It [isn't]("http://en.wikipedia.org/wiki/LAMP_(software_bundle)"); just a software bundle consisting of:
**L**inux
**A**pache
**M**ySQL
**P**HP
Hence, **LAMP**

---

### Post by mb_webguy on 2008-09-20
LAMP stands for Linux, Apache, MySQL, and PHP -- which isn't a program, but a common setup for webservers.  XAMPP is simply an installer for a webserver consisting of Apache, MySQL, and PHP.  So if you install those applications on a Linux system, you have a LAMP server.  The option in Synaptic is simply a quick way of installing the packages for all three applications at once.

---

### Post by Shiv4m on 2008-09-20
> **mb_webguy said:**
> LAMP stands for Linux, Apache, MySQL, and PHP -- which isn't a program, but a common setup for webservers.  XAMPP is simply an installer for a webserver consisting of Apache, MySQL, and PHP.  So if you install those applications on a Linux system, you have a LAMP server.  The option in Synaptic is simply a quick way of installing the packages for all three applications at once.
Ye thanks I got all that, where is it located? I can't find any launcher.

---

### Post by mb_webguy on 2008-09-20
Hehe...  First time at web development, I guess?

There isn't a launcher.  Apache runs as a service.  You can test to make sure it's running by typing "localhost" in the address bar of your browser.

You put html or php files in the /var/www directory.  You might want to check out the [W3Schools]("http://www.w3schools.com/") website for information about html and css, and the [PHP]("http://www.php.net/") website for tutorials and reference material for PHP.

Html, php, and css files are just text files, so you can use any text editor such as Gedit (the default text editor for Ubuntu) to create them.  You can also use a WYSIWYG editor such as Kompozer, which you can install with Synaptic.

---

### Post by Shiv4m on 2008-09-20
How should I know which ports to open then?

---

### Post by Shiv4m on 2008-09-21
How should I know which ports to open then?

---

### Post by mb_webguy on 2008-09-21
You don't need to open any ports.  Installing Apache opens the ports for you.

That's actually the only difference between and open and a closed port -- whether there's a server application listening at that port.  By default, all ports on Ubuntu are closed, which simply means that there are no installed applications that listen at any ports.  A firewall will "stealth" a port, which is a bit different.  

I like using the analogy of a dance club.  Let's assume that the only way of getting into a club is for someone to open the door and let you in -- you can't open the door on your own, and breaking in isn't allowed.  If the club is closed, there isn't anyone inside to open the door when you knock, so you can't get in.  That's the same as a closed port.  If the club is open, then someone inside will probably open the door for you if you knock.  That's the same as an open port.  If the club has a bouncer standing at the door, then if you're not on the list, then you can't get in, even if there's someone inside who would open the door for you.  That's the same as if a firewall has stealthed a port.

---

