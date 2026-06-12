---
title: "Some (very basic) questions about Linux Servers in general"
date: 2008-08-02
forum: General Help
---

### Post by uraknai on 2008-08-02
Hi,

I currently work at a school as a web designer. There is talk that they want to host the website themselves from within school which makes sense for a number of reasons. Our IT technician is insistant upon haing a Windows IIS server setup to host the site but I feel a LAMP setup would be much more appropriate for the work I'm going to be doing.

Not knowing anything about servers I can't really argue my case and so need help on a few things to get me started.

I downloaded and installed Ubuntu Server and was alarmed to find it had no GUI:eek:. I proceeded to download a GUI merely to get a feel for Linux. I understand that for a server it's best not to have a GUI and so will reinstall without one when I've had a play around.

From installing Ubuntu I now have a few questions.

1. Once Apache, Mysql etc are setup and the server is running do I have to set up some kind of FTP on the server and login from another computer (i.e the windows XP pc I have been using to design the site) and upload the files as if it was any other webhost or would I transfer them via external HDD??

2. Is it possible to connect to the server from a windows pc to see the file structure and copy the files over?

3. I was unable to copy files to the /www directory (it said I had insuficient permissions). Are the permissions set by Apache or Linux and how would I set these permissions to allow me to copy files to the relevant directory?

4. What will I need to install to get it up and running (for example, Apache, Mysql etc)?

5. Are there any potential pitfalls I should be aware of while trying to set everything up?

Sorry for the stupid questions, I'm sure I'll think of more when I turn Ubuntu on Monday morning.

Cheers,


Nick

---

### Post by geirha on 2008-08-02
1. There is no ftp-software installed by default (actually no way in from the net after installing), and I would recommend using sftp/scp rather than ftp as it is more secure. You get sftp by installing openssh-server.

2. You can use samba to share folders.

3. The default web-root is /var/www if I remember correctly, and by default it is only writable to the root user. Create a group for the webdevelopers, change group-ownership to /var/www to that group, give the group write permission, and add all webdevelopers to that group.
```

sudo addgroup web-devel
sudo adduser user1 web-devel      # Adds user1 to the web-devel group
sudo adduser user2 web-devel
sudo chgrp -R web-devel /var/www  # All files and folders under /var/www get group-ownership of web-devel
sudo chmod -R g+w /var/www        # Adds write permission for the group

```
I recommend you read about permissions [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

4. ```
sudo tasksel             # Select Lamp
```

5. Hard to answer

---

### Post by uraknai on 2008-08-02
> **geirha said:**
> 1. There is no ftp-software installed by default (actually no way in from the net after installing), and I would recommend using sftp/scp rather than ftp as it is more secure. You get sftp by installing openssh-server.

2. You can use samba to share folders.

3. The default web-root is /var/www if I remember correctly, and by default it is only writable to the root user. Create a group for the webdevelopers, change group-ownership to /var/www to that group, give the group write permission, and add all webdevelopers to that group.
```

sudo addgroup web-devel
sudo adduser user1 web-devel      # Adds user1 to the web-devel group
sudo adduser user2 web-devel
sudo chgrp -R web-devel /var/www  # All files and folders under /var/www get group-ownership of web-devel
sudo chmod -R g+w /var/www        # Adds write permission for the group

```
I recommend you read about permissions [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

4. ```
sudo tasksel             # Select Lamp
```

5. Hard to answer

Thanks, I'll give it another go on Monday and let you know if I have any problems.

One more thing, am I right in thinking that once the Ubuntu Web Server is setup it wont really need to be touched as all files will just be uploaded to it from another PC?

---

### Post by geirha on 2008-08-02
> **uraknai said:**
> Thanks, I'll give it another go on Monday and let you know if I have any problems.

One more thing, am I right in thinking that once the Ubuntu Web Server is setup it wont really need to be touched as all files will just be uploaded to it from another PC?

As long as nothing unexpected happens it should be fine. If the web app has an unsanitized mysql-query for instance, someone may be tempted to drop a few tables. Then you'll need to restore from last backup and fix the bug in the web app naturally.

---

### Post by uraknai on 2008-08-04
I successfully got my Ubuntu Server up and running today and connected to it from my XP machine first my typing the IP (10.122.164.6) in the IE address bar which opened up the 'It Works!" html file showing APACHE is running ok and then by installing SSH and using Putty to connect from the XP machine.

As I understand it the next steps are:

1. Setup an FTP on the server allowing me to upload/download files from my windows XP PC (or possibly use some other method to easily transfer files from the pc to the /var/www directory on the server)

2. Allow the server to be seen by the outside world, maybe by ip address initially and then by a web address which I'll need to buy.

So, to begin with, could someone please explain the basic principles behind setting up FTP on the Ubuntu server and maybe point me in the direction of a good step-by-step guide which includes logging on and uploading files from a local machine.

Cheers,

Nick

---

### Post by geirha on 2008-08-04
First of all you got openSSH, which also brings along sftp. I don't know too many sftp clients, but WinSCP is an easy GUI-client. Alot of IDE's and editors also have the ability to upload files to an (s)ftp server as well. 

If you still want FTP, there is documentation on how to setup common server applications at [https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html) including FTP-servers.

---

### Post by uraknai on 2008-08-05
> **geirha said:**
> First of all you got openSSH, which also brings along sftp. I don't know too many sftp clients, but WinSCP is an easy GUI-client. Alot of IDE's and editors also have the ability to upload files to an (s)ftp server as well. 

If you still want FTP, there is documentation on how to setup common server applications at [https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html) including FTP-servers.

Thanks for all your help, the LAMP server is now up and running and I can copy my website from my XP PC. 

I guess the next stage is allowing the outside world access it via a web address :| Is this gonna be as difficult as I imagine??

---

### Post by H4rm0ny on 2008-08-05
You sound like you're making really good progress in short time. 

I don't know if you went with FTP or stuck with SFTP (which is better because its more secure). In either case, an excellent program for shifting the files about is [Filezilla]("http://filezilla-project.org") which provides a lovely interface and is available for both Windows and Linux (I don't use it for Linux, but whenever I find myself using a Windows system, I install it).

Regarding your earlier comment about not needing a GUI on a server... Well if you're an elitist snob (like me, I'm afraid), then don't have one on there because its theoretically just wasting resources, eating up disk space and the more code you have on there, the more risk there is of a security hole. But sooner or later, I expect you'll need to log in and do something more complicated such as changing lots of file permissions, creating new groups, setting up backup systems or something. And you can do all that from the command line but you might wish at that point you had a GUI. Don't feel obliged to remove the GUI if you don't want to. ;)

Now making your website available to the outside world could be very easy or could be a world of pain. Most of the pain will come from factors that are outside your control.

To serve the web-pages to clients in the school, you need:
To set up a name on the network that points at the IP address of your server.

To serve web-pages to clients outside the school you need:
A static IP address for your server.
A domain name registered.
To point this domain name at the IP address.

At this point, you should be pretty much done, assuming that you have configured Apache to return HTTP requests on Port 80 (which you seem to have done).

Is there anything that can complicated the above process? Oh yes! :D

Presumably your school already has a fixed IP? If not, you need to organise one with a registrar company. Likewise for the domain name. You need to check there is no existing firewall system that will block HTTP requests coming in from outside.  If your school handles all these sorts of things itself and there's nothing in place, then it'll be fairly straightforward (I hope). If your school is administered by outside companies that try to sew up this market for themselves, then you might end up having a few arguments.

In my limited UK experience with schools, everything gets micro-managed by the educational bureaucracy and becomes 100x more hassle than it ought to be. Also, school IT administrators in my experience, like to shuffle around doing not much, reading people's emails and talking in overly-technical terms to people without IT experience to make themselves sound like mystical gurus. They *hate* smart arses who know of better ways to do things. I sincerely hope you don't run into problems of this nature.

Apologies if any of my answers are too basic - it's hard to judge someone's level of technical expertise sometimes.

Let us know how it goes,

Harmony.

---

### Post by uraknai on 2008-08-05
> **H4rm0ny said:**
> You sound like you're making really good progress in short time. 

I don't know if you went with FTP or stuck with SFTP (which is better because its more secure). In either case, an excellent program for shifting the files about is [Filezilla]("http://filezilla-project.org") which provides a lovely interface and is available for both Windows and Linux (I don't use it for Linux, but whenever I find myself using a Windows system, I install it).

Regarding your earlier comment about not needing a GUI on a server... Well if you're an elitist snob (like me, I'm afraid), then don't have one on there because its theoretically just wasting resources, eating up disk space and the more code you have on there, the more risk there is of a security hole. But sooner or later, I expect you'll need to log in and do something more complicated such as changing lots of file permissions, creating new groups, setting up backup systems or something. And you can do all that from the command line but you might wish at that point you had a GUI. Don't feel obliged to remove the GUI if you don't want to. ;)

Now making your website available to the outside world could be very easy or could be a world of pain. Most of the pain will come from factors that are outside your control.

To serve the web-pages to clients in the school, you need:
To set up a name on the network that points at the IP address of your server.

To serve web-pages to clients outside the school you need:
A static IP address for your server.
A domain name registered.
To point this domain name at the IP address.

At this point, you should be pretty much done, assuming that you have configured Apache to return HTTP requests on Port 80 (which you seem to have done).

Is there anything that can complicated the above process? Oh yes! :D

Presumably your school already has a fixed IP? If not, you need to organise one with a registrar company. Likewise for the domain name. You need to check there is no existing firewall system that will block HTTP requests coming in from outside.  If your school handles all these sorts of things itself and there's nothing in place, then it'll be fairly straightforward (I hope). If your school is administered by outside companies that try to sew up this market for themselves, then you might end up having a few arguments.

In my limited UK experience with schools, everything gets micro-managed by the educational bureaucracy and becomes 100x more hassle than it ought to be. Also, school IT administrators in my experience, like to shuffle around doing not much, reading people's emails and talking in overly-technical terms to people without IT experience to make themselves sound like mystical gurus. They *hate* smart arses who know of better ways to do things. I sincerely hope you don't run into problems of this nature.

Apologies if any of my answers are too basic - it's hard to judge someone's level of technical expertise sometimes.

Let us know how it goes,

Harmony.

Yeah, so far everything's gone pretty smooth. It's been a really good learning experience as a web developer to discover how these things actually work. I guess we just take it for granted:)

I re-installed Ubuntu Server without the GUI (for the security reasons you mentioned). I then installed SSH and use Putty to type the commands from my windows XP machine for convenience. I created a group and gave it permissions to read/write to the /var/www folder and subfolders which I access using WinSCP from my XP PC using sftp(thanks again geirha)

So far, so good.

Before I register a domain name and have it point to the webserver from the outside world can I set it up so I can access the server by typing the ip address in the browser address bar. At the moment I can access the website locally by typing the server's ip address (10.122.164.6) but I'm not sure what I have to do to access it from outside the local network in the same way.

---

### Post by hyper_ch on 2008-08-05
hosting the domain will be a bit more challenging.

Do you have a dedicated ipaddress on that server?
The registrar where you registered the domain, do they let you use their nameservers to add entries for the domain?

---

### Post by mixmaster on 2008-08-05
Possibly this is a purely personal prejudice, but I have never got on with PuTTY.  I use MKS Toolkit, which is a commercial unix-like shell/utility set for windows but friends have reported success using Cygwin.  Either of these will provide you with a unix-like environment under windows which you may find useful for a variety of other tasks.

---

### Post by H4rm0ny on 2008-08-05
> **uraknai said:**
> Yeah, so far everything's gone pretty smooth. It's been a really good learning experience as a web developer to discover how these things actually work. I guess we just take it for granted:)

I re-installed Ubuntu Server without the GUI (for the security reasons you mentioned). I then installed SSH and use Putty to type the commands from my windows XP machine for convenience. I created a group and gave it permissions to read/write to the /var/www folder and subfolders which I access using WinSCP from my XP PC using sftp(thanks again geirha)

So far, so good.

Before I register a domain name and have it point to the webserver from the outside world can I set it up so I can access the server by typing the ip address in the browser address bar. At the moment I can access the website locally by typing the server's ip address (10.122.164.6) but I'm not sure what I have to do to access it from outside the local network in the same way.

It might be difficult to drive in to your server from outside. There are numerous things that might stop you. The obvious is that if your school does have a fixed IP address (ISPs sometimes reassign IPs from a "pool" as needed unless you've agreed a fixed one with them), then the IP address will certainly not be pointing at the server that you just set up, but at some other machine the school has configured (that's if it isn't just pointing at a router somewhere). This machine or the router would need to be configured to forward requests on to your server. And then there might well be a firewall that prevents incoming connections anyway and this would need to be re-configured. I'm not trying to dissuade you, it's plenty possible. But there are too many things to cover for anyone to give you specific instructions on how to do this at this point. It's something you need to investigate and try, I'm afraid. It's a very detail dependent thing you're asking.

However, you might find it easier to drive out from your server to your home computer somehow. Again you run into problems with a fixed IP, (though often, even with a dynamic IP, in practice it stays the same for days or even weeks), but you don't have to worry about DNS, NAT and other deceptively innocent looking acronyms. ;) Look into setting up a VPN between your home computer and your school one and bear in mind that you need to be requesting the connection from the school side (so that it can find your home connection) rather than from home (because it wont find the school connection). And there are ways to have it re-establish a VPN automatically if it drops, you turn your computer off, etc.

This is a large area though. You may wish to take a copy of the files home with you, or put a Linux install on a USB drive so you can have an install on your home computer without messing anything up. Have a look into VPNs and judge how much hassle it is or isn't for yourself. We'll be happy to help, I'm sure, but try finding some good How To's on it first.

Of course, there's a lot of assumptions made in all of my reply. It might turn out to be very simple for you to expose your server to the outside world. I'm just listing probable issues and context around them so you can make more informed judgements. I hope this helps,

Harmony.

---

### Post by uraknai on 2008-09-07
Just an update and some more questions.

I've set up the Ubuntu Server which is running on the local network and the website is accessible from networked computer by typing its IP (10.122.164.6) into browser address bar.

I've contacted our ISP who have sent me some forms to complete to get this server available as a webserver accessible from the outside. The information they need is just the schools IP address, the IP address of the server and the port number.

I have a few questions before I send back the form.

1. My web files are located in /var/www folder and at the moment can be accessed using the servers IP address. If I wanted to save them in a different folder, say /var/www/website, how would I make apache automatically look in this folder rather than having to type 10.122.164.6/website for apache to look for the index file.

2. When the forms have been sent off and our ISP point the schools ip address to this webserver ip address how will I then get a domain name to redirect to the schools IP address and therefore to the webserver?

3. What changes will I need to make to the Apache configuration files once the schools IP address is directed to the webserver and we have a domain name setup?

Thanks,

Nick

---

