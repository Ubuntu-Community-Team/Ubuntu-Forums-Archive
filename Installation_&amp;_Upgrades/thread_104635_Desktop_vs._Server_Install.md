---
title: "Desktop vs. Server Install"
date: 2005-12-16
forum: Installation &amp; Upgrades
---

### Post by Rajan Varadarajan on 2005-12-16
I understand in a general way the differences between a server and a desktop. But in ubuntu, the differences seem to be blurred. I read through the informal guide put together by A.Y. Siu where it says to use the default install for most users. I did a "standard" or default install on one machine and it installed GNOME etc, fine. But when I installed on another machine where I selected "server", when I ended up with the text prompt. There was no GNOME or other GUI.

My big question is - if I do a standard/default install, can I use the machine as a server for running it as a file/web/database server? It is a bit confusing to me. I want to be able to run the LAMP stack with ubuntu on my machine. Actually, I want to run ubuntu on two machines with one acting as a desktop and the other as a  web/database server. I am simply connecting the two machines with an ethernet switch.

Thanks much for suggestions.

---

### Post by harisund on 2005-12-16
The main difference, as far as I observed, (and apparently as you have observed too) is the number of applications that get installed. There are no other differences. Which means, you could pretty well do a standard install and continue to run a server. 

What determines whether a machine is a server or not is the software installed on it. You could use your desktop machine as a ssh "server" which means you can login to it from outside your network. 

At my home here, I have an old desktop to which I attached my 160GB hard disk, and am using it to run a server. As soon as my "server" installation finished, I ran "apt-get install openssh-server" and haven't physically logged into the machine ever since. "apt-get install apache2" has allowed me to host my web site on that. "apt-get install vsftpd" or "apt-get install proftpd" allows  me to use it as a file server. "apt-get install samba" and I can access my 160Gb from my Windows partition. 

The reason you wouldn't want to do a complete installation ("standard") on a machine you intend to use as a server is that you will be wasting hard disk space on stuff like GUI etc which you are unlikely to use. 

Anyway, I suggest you try downloading the server version of Ubuntu. 
[http://se.releases.ubuntu.com/ubuntu-server/5.10/](http://se.releases.ubuntu.com/ubuntu-server/5.10/)

This comes pre loaded with the packages that a typical server would have. 

[https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP)
might help when installing your  LAMP architecture. 

What you want to do appears similar to the setup I have at home. Install the complete version on your desktop and the minimal version in your other machine. You can then login to your server from your desktop and configure it. 

Note: in the above cases, you might need to do some configuring (read editing .conf files) and sudo all the commands.

---

### Post by WOteB on 2005-12-16
I agree! A few notes:

I use Debian 3.1 (Sarge) on my sever, but the Ubuntu sever install should not have a great difference I suppose.

With a minimal installation you also have a minimum of running deamons and only those deamons rinning when necessarry. With a desktop installation running on a sever, you have too muche deamons running.
Before my Debian installation I have used Trustix Secure Linux, with a very few deamons running, but that was on an old system.

I can advise you to install webmin on the server: apt-get install webmin. From your other system you can configure the server very simple and comfertable.

I also can advise you to install MC on the server: apt-get install mc. This is a swiss-knife for system administration like making directories etc.

On the desktop, install PuTTY: apt-get install putty. With PuTTY you can run ther server in a terminal on your desktop. Login with the normal account and, when running the server you can administer the server with sudo [commands] or switch with su to the root account (if you want). When using sudo, you must install that first on the server: apt-get sudo and put the following line in /etc/sudoers: [username] ALL=(ALL) ALL. [username] is, off course your own account name.

---

### Post by harisund on 2005-12-16
webmin? What is that? Do I install it using apt-get install webmin? Can I use webmin through Putty? 

yes indeed mc is awesome, but I actually vifm .. (File manager, with vi like key bindings) 

I use putty too !

---

### Post by WOteB on 2005-12-17
[QUOTE=harisund]webmin? What is that? Do I install it using apt-get install webmin? Can I use webmin through Putty? 

yes indeed mc is awesome, but I actually vifm .. (File manager, with vi like key bindings) 

I use putty too ![/QUOTE]

"Webmin? This is some information from [www.webmin.com:](www.webmin.com:)

What is Webmin?
Webmin is a web-based interface for system administration for Unix. Using any browser that supports tables and forms (and Java for the File Manager module), you can setup user accounts, Apache, DNS, file sharing and so on.

Webmin consists of a simple web server, and a number of CGI programs which directly update system files like /etc/inetd.conf and /etc/passwd. The web server and all CGI programs are written in Perl version 5, and use no non-standard Perl modules."

============================

You see, It's a webbased administration tool so you can administer your server from a workstation via your browser. Very, very nice tool with many possebilities. Take a look at [www.webmin.com](www.webmin.com) for more information.

Installation is easy. Via Putty you can install webmin like: apt-get install webmin on your server (root login via su), or sudo apt-get install webmin (sudo should be installed on the server).

Login via your browser is easy: [https://[server](https://[server) ip or name]:10000. An example: [https://192.168.0.1:10000](https://192.168.0.1:10000). Within a few moments you get the root login prompt and you can work on your server.

It's also possible to restrict the administration to a few workstations: In /etc/wemnin/miniserv.conf you have a line with allowed systems; Just put the ip address of your system in that line, and you have access from your desktop.

Success and have a lot of fun.

---

### Post by Rajan Varadarajan on 2005-12-17
First of all, thank you all for the valuable advice. I decided to do a regular install for the server machine as well because at times I would like to have the ease of the GUI for managing tasks. I am still not familiar with a lot of the terminal level commands. I am not scared of doing commands (I used to do a lot MSDOS batch files as well as TAPCIS, if any of you remember, it is an old utility to access CompuServer forums); it is just that I couldn't find a nice compilation of commands into a compact user manual or something like that. Eventually, I would like to alter the startup scripts to prevent loading GNOME/Nautilus and be able to load them on demand for my admin tasks. I think this way, I will have the best of both worlds - GUI on demand and less daemons running on the server at all other times.

I have read a little bit about webmin. How do I get it and install it? I looked in the package manager list but couldn't find it nor on the install CD.

Also would like some suggestions as to how to format my hard disk (60gb) and bring it on line. That is where I would like to store all my databases, script files for my projects, etc.

As always, thanks again for your help.

---

### Post by WOteB on 2005-12-17
In /etc/apt/sources.list you must have these lines:

deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) hoary universe 
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) hoary universe 
(read for hoary --> breezy)

 active. If not, remove the # before it. Then run apt-get update en look for the Webmin packages. (you should login as root!! to have priveliges for this sorces.list file)

I wrote I have Debian 3.1 Sarge (Stable version), so I had no problems with installing Wemin because Debian have more packages in store, I suppose. In this case Ubuntu is not equal I think. But with the universe lines active in the sources.list you have no problems with installing Webmin I think. Succes!!

---

### Post by Rajan Varadarajan on 2005-12-17
Thanks much to woteb and harisund.

<<Harisund - you mentioned:
What you want to do appears similar to the setup I have at home. Install the complete version on your desktop and the minimal version in your other machine. You can then login to your server from your desktop and configure it.>>

How do you reference/address the server from the desktop? Please note that I have connected the machines through an ethernet switch; so the IP addresses are going to be dynamic. Is there a way to reference the machine through their machine name? Like "server1" from a machine named "desktop1".

Thanks again.

---

### Post by harisund on 2005-12-18
The thing is I have a wireless router that acts as a router too. And it has an inbuilt DHCP server. So what I do is set it to give my Linux machine a static IP. I can then use the static (Class C) ip of the linux machine. For example, the IP that my ISP has currently given is 68.227.129.180 and my router does NAT and gives my laptop 192.168.0.135 and my server a static ip of 192.168.0.145. So, as long as I am in my home network I can just type ssh -X user@192.168.0.145 and I get connected (with X enabled! )

I am not very sure I know how a switch works. What kind of a IP address do your machines get from the switch? Is it class C, or some privately assigned ip? 

If your machines acqire an IP from the switch using a DHCP I suggest editing your /etc/network/interfaces to get a static ip. This way, you can make sure your server always has, say, xx.yy.zz.aa. Then you can access it from another machine on the same network using xx.yy.zz.aa

I may not be very clear, but sure could try if you could please explain what kind of IPs your machines acquire I guess we could get things done faster. 

By the way, I am Hari Sundararajan, and am from Bangalore. Where are you from? :D

---

