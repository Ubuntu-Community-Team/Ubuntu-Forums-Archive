---
title: "Runing Remote Apps"
date: 2005-11-03
forum: General Help
---

### Post by El_Boti on 2005-11-03
Hi Greetings from Puerto Rico. (My first post, this is always so exciting!! LOL).

I am trying to run a remote application from a SUN computer at work that we use for network monitoring but for some reasons I cannot get the App to display.

Here is what I am doing: (BTW I AM RUNING A LIVE CD!!!)

ubuntu@ubuntu:~$ xhost +
access control disabled, clients can connect from any host
ubuntu@ubuntu:~$ telnet "Remote Host IP"
Trying "Remote Host IP"...
Connected to "Remoty Host IP".
Escape character is '^]'.


SunOS 5.8

login: 
Password:
Last login: Thu Nov  3 06:00:40 from "My IP"
Sun Microsystems Inc.   SunOS 5.8       Generic Patch   February 2004
$ DISPLAY="My IP":0
$ export DISPLAY
$ /mdm &
25654
$ xmsg: could not open display.
Error: Can't open display: "My IP":0
Error: Can't open display: "My IP":0
/opt/MagellanNMS/bin/msm: could not open display.


I hope that somebody can help me. Thanks in advance!!! 

(Sorry for any mistake, English is not my first language. Feel free to correct, that will help me improve my english). :)

---

### Post by RAOF on 2005-11-03
I don't suppose you can ssh into that machine?  It's more secure then telnet, and you can forward X over it with ssh -X user@ipaddress

---

### Post by El_Boti on 2005-11-03
[QUOTE=RAOF]I don't suppose you can ssh into that machine?  It's more secure then telnet, and you can forward X over it with ssh -X user@ipaddress[/QUOTE]


Yes, I can ssh to that machine, but i just want to know why I am recieving that error. I have done it trought telnet before without any problem , but not with Ubuntu. I just want to know what I am doing wrong or if I am missing something.

---

### Post by RAOF on 2005-11-03
Sorry, I've got no experience with doing it through telnet.  I can't help you fix the telnet.

---

### Post by El_Boti on 2005-11-03
[QUOTE=RAOF]Sorry, I've got no experience with doing it through telnet.  I can't help you fix the telnet.[/QUOTE]


Don't worry, thanks anyway I really apreciate your help. :)

I don't think the problem is the telnet, it should be something with the DISPLAY command.

I have done this before with KNOPPIX without any problem. I think it is a permission related problem.

---

### Post by El_Boti on 2005-11-03
Bump!        :p

---

### Post by ekravche on 2005-11-05
I don't think I've said anything new here, but 

ssh -X -l username hostname.domain.ca

works for me. 

P.S. I'm connecting to a sun solaris machine as well, and the above works great for me.

As an alternative of trying to get it to work with telnet you may want to try.
xhost

It didn't work for me, but you may have better luck.

---

### Post by nagilum on 2005-11-05
In Ubuntu the X server by default does not listen on a TCP socket, meaning that your Sun machine cannot reach it over the network. This is done for security reasons and since ssh -X is a better solution than the xhost stuff you should better leave it this way.
If you want to make X11 listen on a TCP socket nonetheless you have to edit the file /etc/X11/xinit/xserverrc and remove the '-nolisten tcp' option from it.

---

### Post by geoybest on 2005-11-08
[QUOTE=nagilum]In Ubuntu the X server by default does not listen on a TCP socket, meaning that your Sun machine cannot reach it over the network. This is done for security reasons and since ssh -X is a better solution than the xhost stuff you should better leave it this way.
If you want to make X11 listen on a TCP socket nonetheless you have to edit the file /etc/X11/xinit/xserverrc and remove the '-nolisten tcp' option from it.[/QUOTE]

After viewing some relevent posts, it seems that using
```
ssh -X -l myaccount hostdomain
```
is a good way to run remot XWindow applications. But it does not work for me. I have also tried to modify the ssh_config to "ForwardX11 yes", to remove the "-nolisten  tcp" in xserverrc, and even set "DisallowTCP=true" in gdm.conf but of no use. :confused:  What are other possible clues? One more thing to mention, I can use XWin32 on Windows to run XWindow applications remotely on the same host.

---

### Post by El_Boti on 2005-11-10
[QUOTE=nagilum]In Ubuntu the X server by default does not listen on a TCP socket, meaning that your Sun machine cannot reach it over the network. This is done for security reasons and since ssh -X is a better solution than the xhost stuff you should better leave it this way.
If you want to make X11 listen on a TCP socket nonetheless you have to edit the file /etc/X11/xinit/xserverrc and remove the '-nolisten tcp' option from it.[/QUOTE]


Ok, I remove "-nolisten tcp" from /etc/X11/xinit/xserverrc

but I still recieving the error.

Error: Can't open display: "My IP":0
Error: Can't open display: "My IP":0
/opt/MagellanNMS/bin/msm: could not open display

Btw, I tried: 

X -query "hostIP" and it says that X is already running. I will love to be able to run this command beacuse this one let me use the complete UNIX box and not only the App.

For some reason nothing is working out for me LOL.

Any suggestions??   :)

---

### Post by El_Boti on 2005-11-12
Bump!

---

### Post by El_Boti on 2005-11-13
[QUOTE=nagilum]In Ubuntu the X server by default does not listen on a TCP socket, meaning that your Sun machine cannot reach it over the network. This is done for security reasons and since ssh -X is a better solution than the xhost stuff you should better leave it this way.
If you want to make X11 listen on a TCP socket nonetheless you have to edit the file /etc/X11/xinit/xserverrc and remove the '-nolisten tcp' option from it.[/QUOTE]


Ok, I am sorry. It worked!!!! I forgot to restart GDM.

Thank you for your help.

---

### Post by wdg3rd on 2005-12-08
I have the same problem El_Boti was, and I have *already* edited /etc/X11/xinit/xserverrc and ssh'd in with the -X flag and not merely restarted gdm but rebooted the system (as to read my mail on the Xandros machine downstairs, a knoppix CD works fine, just xhost, ssh, export DISPLAY, kmail).  I've found I *like* ubuntu and I'd rather not go back to Mandrake and KDE, but if I always have to reboot to read my mail (it gets *cold* down in the basement about this time of year), my choices are limited.

Yes, I'm new to Ubuntu, but I've been running Linux since 1993 (SLS) and other flavors of Unix for a decade previous -- there's a working (when I can afford the electricity or simply need the heat) Tandy Xenix system in my basement).

---

### Post by Chickenmonger on 2005-12-08
I had somewhat similar problems with connecting remotely with ssh -X, and trying to run Matlab on my college's Linux servers. I had to replace the -X option with a -Y option. Not sure what the real difference was.

---

### Post by lucascr on 2006-03-02
Dear all,

I'm having the same problem with kubuntu 5.10. I can't display any window from a remote ssh connection. I have set xhost, the DISPLAY variable and removed -nolisten tcp from /etc/X11/xinit/xserverrc.
Did someone know how to fix this?

Luca

---

