---
title: "How to use talk command?"
date: 2008-09-07
forum: General Help
---

### Post by pikabuntu on 2008-09-07
I have read the man page for the talk command, but I still don't understand how to use it.  Could someone explain it?

---

### Post by caljohnsmith on 2008-09-08
> **pikabuntu said:**
> I have read the man page for the talk command, but I still don't understand how to use it.  Could someone explain it?
The unix "talk" command has been around for at least 20 years, so it is a bit outdated compared to modern programs like IM, chat rooms, etc. :) The syntax is simple:
```
talk user@host
```
This divides your terminal screen into two sections, top and bottom, where each user can simultaneously type into their part of the terminal window (top or bottom), and each character stroke is relayed in real time, unlike in IRC where you have to hit return before it sends what you wrote.

The user you try to talk to on "host" must have his terminal permissions set enabling "write" privileges to group users. That can be done with the "mesg" command. If user's mesg is "y", then user will allow a talk session, if mesg is "n", then user will refuse your talk request:
```
john@TECH5321:~$ [COLOR="Blue"]mesg
is y[/COLOR]
john@TECH5321:~$ who
john     :0           2008-09-08 05:31
john     pts/1        2008-09-08 05:33 (:0.0)
john     pts/2        2008-09-08 05:33 (:0.0)
john@TECH5321:~$ ls -l /dev/pts*
total 0
crw--w---- 1 john tty 136, 0 2008-09-08 05:31 0
[COLOR="Blue"]crw--w---- 1 john tty 136, 1 2008-09-08 06:41 1[/COLOR]
crw--w---- 1 john tty 136, 2 2008-09-08 05:33 2
john@TECH5321:~$ [COLOR="Blue"]mesg n[/COLOR]
john@TECH5321:~$ ls -l /dev/pts*
total 0
crw--w---- 1 john tty 136, 0 2008-09-08 05:31 0
[COLOR="Blue"]crw------- 1 john tty 136, 1 2008-09-08 06:42 1[/COLOR]
crw--w---- 1 john tty 136, 2 2008-09-08 05:33 2
```
See how "mesg" just simply changes the permissions of the terminal? That's all that's happening.

---

### Post by Sycron on 2008-09-08
That's pretty awesome. :P can I talk over the internet with talk ?

---

### Post by caljohnsmith on 2008-09-08
> **Sycron said:**
> That's pretty awesome. :P can I talk over the internet with talk ?
You certainly can. :) I used to do that all the time with friends at other colleges when I was in college. Of course keep in mind that because that program is rather old and out-dated, I don't think most Linux/Unix systems may even have it installed by default any more.

---

### Post by Sycron on 2008-09-08
For example, how can we talk right now ?

---

### Post by caljohnsmith on 2008-09-08
> **Sycron said:**
> For example, how can we talk right now ?

Well.... First of all you would have to have both the "talk" and the "inetutils-talkd" packages installed. Next you have to get your talkd daemon going, which I'm not sure where in /etc/init.d it is, so you could reboot. Also, I think "talk" uses the TCP and UDP ports 518 for connections by default, so you would have to open up those ports in your router if you have one (port forwarding). You would have to ask your friend what his IP address is, assuming he's not at some easy-to-remember domain. Once you have it, and once he runs his own "talkd" daemon (and has talk installed too obviously), you would do:
```
talk joeshmoe@123.456.789.123
```
He will get your request (assuming he has mesg "y"), and he can accept it by using the same talk command aimed at you with your host to start the talk session.

---

### Post by Sycron on 2008-09-08
```
sycron@Book:~$ sudo apt-get install talkd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  inetutils-inetd
The following NEW packages will be installed:
  inetutils-inetd talkd
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 99.8kB of archives.
After this operation, 291kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com intrepid/universe inetutils-inetd 2:1.5.dfsg.1-8ubuntu1 [81.9kB]
Get:2 http://archive.ubuntu.com intrepid/universe talkd 0.17-13 [17.9kB]
Fetched 99.8kB in 0s (121kB/s)
Selecting previously deselected package inetutils-inetd.
(Reading database ... 103391 files and directories currently installed.)
Unpacking inetutils-inetd (from .../inetutils-inetd_2%3a1.5.dfsg.1-8ubuntu1_i386.deb) ...
Selecting previously deselected package talkd.
Unpacking talkd (from .../talkd_0.17-13_i386.deb) ...
Processing triggers for man-db ...
Setting up inetutils-inetd (2:1.5.dfsg.1-8ubuntu1) ...
 * Not starting internet superserver: no services enabled.

Setting up talkd (0.17-13) ...
invoke-rc.d: initscript inetutils-inetd, action "force-reload" failed.
invoke-rc.d: initscript inetutils-inetd, action "force-reload" failed.
invoke-rc.d: initscript inetutils-inetd, action "force-reload" failed.
invoke-rc.d: initscript inetutils-inetd, action "force-reload" failed.

```

pretty strange.

---

### Post by caljohnsmith on 2008-09-08
I just installed "talkd" on my machine with no problem. I did not get those errors you got at the end of your install, but I'm using Hardy and it looks like you are using Intrepid. That could be the difference.

---

### Post by Sycron on 2008-09-08
I're removed talkd ant installed inetutils-inetd. When I type ```
sudo talkd
``` that's what I get.```
sycron@Book:~$ sudo talkd
sycron@Book:~$ 

```

---

### Post by caljohnsmith on 2008-09-08
Looks like there may be more to it than just installing the "talk" and "talkd" packages:
[http://ubuntuforums.org/showthread.php?t=191896](http://ubuntuforums.org/showthread.php?t=191896)

---

### Post by pikabuntu on 2008-09-08
I encountered the talk command when I was looking for a way to message people on my network... Is there another way to do this?
I was looking for something that did popup windows, like when you leave a message on a locked screen...

---

### Post by Vivaldi Gloria on 2008-09-09
I've never used talk outside a lan so I cannot comment on how to do it. But let me point out that you can also chat with netcat or cryptcat. First install it:

```
sudo apt-get install cryptcat
```

In the first machine use

```
cryptcat -nvlp <port_number> -k <password>
```

and the in the second use

```
cryptcat -nv <ip_number> <port_number> -k <password>
```

Works similarly to netcat. I think cryptcat is better for net chatting as it sends everything encrypted. While chatting I prefer that one sides starts his lines with the plus sign so they are easier to see. 

Note that there is also socat which can use openssl:

[http://www.dest-unreach.org/socat/](http://www.dest-unreach.org/socat/)
[http://www.dest-unreach.org/socat/doc/socat-openssltunnel.html](http://www.dest-unreach.org/socat/doc/socat-openssltunnel.html)
[http://www.dest-unreach.org/socat/doc/socat.html](http://www.dest-unreach.org/socat/doc/socat.html)

---

