---
title: "Setting up a simple file server"
date: 2005-12-09
forum: Installation &amp; Upgrades
---

### Post by dirkvl on 2005-12-09
I'm a Windows sysadmin and I've been following the linux scene from behind the lines. At this point I've decided to start experimenting with linux as a file server.
I chose UBUNTU, noticing it's huge support forum.
After I downloaded the install CD and following the installation "wizard" I soon set up UBUNTU and made connection to the internet.
Now this is what I want to do : I want to set up a file server with samba and configure it as a member server in a windows 2003 domain.
Then I want to share a folder and use a domaingroup (from AD) to grant write access.
This job takes about 2 minutes (or less) on a windows server, after setting up windows.
Imagine my supprise : no wizards, no manual for beginners to do this, no nothing !
I can't even determine if SAMBA server is present/running on the machine.
I can only imagine how hard this must be for a novice...
is there a comprehensive, SIMPLE procedure to do what I described - preferably using a grafical interface. Installing add-ons or extra soft is not an issue.
If there isn't, I'm afraid my freshly written install CD will end up in the trash can.
I really want to do this, but note the following : hard work for small results is not an option for sysadmins. We want things done fast and fluent.
Can anyone point me in the right (=painless) direction ?

---

### Post by gborbolla on 2005-12-09
Read this two posts from the "Customization Tips & Tricks" forum.

[http://www.ubuntuforums.org/showthread.php?t=76647&highlight=samba]("http://www.ubuntuforums.org/showthread.php?t=76647&highlight=samba")

and

[http://www.ubuntuforums.org/showthread.php?t=91510&highlight=samba]("http://www.ubuntuforums.org/showthread.php?t=91510&highlight=samba")

Hope this helps

---

### Post by dirkvl on 2005-12-12
I took a glance at the two links, which led me to how to's for samba, winbind and pam.
Bottomline : it's still hard.
- You have to edit 7 text files and be very carefull you place your server and domain name in the right place (which isn't explained very clearly at all in the how to)
- You have to type 9 commandlines and hope they each start the selected service/join.

However, this commandline crap isn't going to get me down.
Sometime (hopefully in the near future) someone is going to create a good gui for automating all these actions.
Face it guys : all you need to join a server in a domain is the servername, domainname and an admin for the windows domain.
Where's the wizard/gui ?
I haven't even got a clue how to use a domain group to put security on a share. Is there no "how to" for this ?
I'm afraid this simply does not do. This is not user friendly.

---

### Post by ShiftyPowers on 2005-12-12
I completely agree with this statement.  I just started playing around with ubuntu and linux and love hte fact that things are free and customizable and stable.  However, installation of software and configuring of things such as samba is just an unneccessary hassle.

---

### Post by jwd45244 on 2005-12-12
While Ubuntu has lots of good information around Samba, the best documentation is at [www.samba.org](www.samba.org).  As to having to edit configuration, you can use SWAT (which comes with Samba) wich provides a "Web Interface" to Samba Admin.

---

### Post by dirkvl on 2005-12-16
I managed to install "SWAT", but after installing I get "connection refused" on [http://SERVER00:901](http://SERVER00:901) (SERVER00 is my netbois name for the server).
Does anyone know how to resolve this ?

---

### Post by nocturn on 2005-12-16
[QUOTE=dirkvl]
Face it guys : all you need to join a server in a domain is the servername, domainname and an admin for the windows domain.
Where's the wizard/gui ?
I haven't even got a clue how to use a domain group to put security on a share. Is there no "how to" for this ?
I'm afraid this simply does not do. This is not user friendly.[/QUOTE]

It is a huge deal that Linux can handle this at all.  AD implements a broken version of LDAP and Kerberos, it took al lot of reverse-engineering from the Samba guys to make any of it work, and they are still working very hard on keeping it working and extending it to have full fucntionality (ADS primary server).

Yes, winbind is hard, but all this hacking should not have been needed if the implementation was clean, then attention could have turned to making a nice GUI for pam_krb5 and nss_ldap instead of the winbind mess.

---

### Post by nocturn on 2005-12-16
> 
I can only imagine how hard this must be for a novice..


I'm really sorry to say this, but a novice should not be put in a administrator role...  A sysadmin should have a solid understanding of the technology he/she is using (for ADS this includes LDAP and Kerberos).

A lack of knowledge on the part of admins leads to insecure installs.

---

### Post by nocturn on 2005-12-16
[QUOTE=dirkvl]I managed to install "SWAT", but after installing I get "connection refused" on [http://SERVER00:901](http://SERVER00:901) (SERVER00 is my netbois name for the server).
Does anyone know how to resolve this ?[/QUOTE]

You need to use the DNS name (or IP) for the server.

---

### Post by dirkvl on 2005-12-16
I believe that forums are not for picking on people, but for serious aid, and I will state at once that throwing bullshit at me will have no effect at all.
To correct a misunderstanding : with novice users I meant novice LINUX users.
When you're a windows sysadmin and you have to dig yourself into linux, the job should be made easy, not harder. If you can't see the simple facts of business life ("time is money"), that's too bad.

I still haven't got a solution for my problem. The browser window I opened was actually on the server itself, so DNS is no issue. I've tried localhost and the IP of the server too instead of "SERVER00". Still "connection refused".

---

### Post by nocturn on 2005-12-16
[QUOTE=dirkvl]I believe that forums are not for picking on people, but for serious aid, and I will state at once that throwing bullshit at me will have no effect at all.
[/quote]

That is not the intent, but I really appreciate the effort made by the Samba people in supporting an ever-changing and undocumented specification.  
Most people, including myself are quite willing to help you deal with specific issues, including setting up winbind but complaining about the lack of a GUI to interface with a closed specification is not the way to go about this.

> 
To correct a misunderstanding : with novice users I meant novice LINUX users.
When you're a windows sysadmin and you have to dig yourself into linux, the job should be made easy, not harder. If you can't see the simple facts of business life ("time is money"), that's too bad.


First of, time = money is a fallacy, if this equation where correct it would be able to say money = time.  Which means that if you had a billion $/€ you could extend your life, which you cannot.

Secondly, getting to know the technology behind the functions you use is not a waste of time (or money), it will make you a better system admin and a better skilled IT person.

> 
I still haven't got a solution for my problem. The browser window I opened was actually on the server itself, so DNS is no issue. I've tried localhost and the IP of the server too instead of "SERVER00". Still "connection refused".

Ok, then let's see if the port is actually open.

What is the output of:

```

netstat -an |grep LISTEN

```

---

### Post by MetalMusicAddict on 2005-12-16
[QUOTE=dirkvl]
is there a comprehensive, SIMPLE procedure to do what I described - preferably using a grafical interface. Installing add-ons or extra soft is not an issue.
If there isn't, I'm afraid my freshly written install CD will end up in the trash can.
I really want to do this, but note the following : hard work for small results is not an option for sysadmins. **We want things done fast and fluent**.
Can anyone point me in the right (=painless) direction ?[/QUOTE]
If your learning a new OS why do you expect it to be "fast and fluent"? It took you time to learn windows didnt it? In the end Linux and windows are going to be 2 different animals. You will *have* to learn the different way of things to make it all work together. Consider this a experiment for you and not a mission critical part of your network or you will get discouraged quickly. Which already seems to be happening.

Samba is alot to learn. I have a 2" thick book on it in front of me. Unlike alot of linux stuff it is very well documented.

If you "really want to do this" hang in there and read/look around. Youll get it. ;) Youll be suprised at all the things this **FREE** OS can do.

---

### Post by nocturn on 2005-12-16
> note the following : hard work for small results is not an option for sysadmins. We want things done fast and fluent.

That depends on what type of admin you are.  I'm a sysadmin too.
I prefer doing things slowly with a good understanding of what happens because  in my experience it leads to better long term results and time saving (because in the event of breakage, you have the ability to trace the problem).

The big difference is that I got my sysadmin experience on Unix (Solaris) and Linux systems, which are very different from the way thing are done in the windows world.   Actually, I had to admin a couple of windows boxes along the way and over the course of a year, they were a lot harder and more time consuming then their *nix counterparts.

---

### Post by Frymaster on 2005-12-16
much kudos must go to the samba folks for its existence, but that doesn't change the fact that for novices, configuring it is an unbelievable headache.

I couldn't find a decent front-end app, webmin's samba plugin is a nightmare (and webmin is broken for ubuntu anyway)

text-based-natural-language configs instead of obscure binary files YES, but that shouldn't mean you have to be forced into using a text editor for anything but the most obscure of setups (or for getting your GUI back when you broke it ;) )

---

### Post by dirkvl on 2005-12-20
admin@SERVER00:~$ netstat -an | grep LISTEN
tcp        0      0 127.0.0.1:32769         0.0.0.0:* 
             LISTEN
tcp        0      0 127.0.0.1:32770         0.0.0.0:* 
             LISTEN
tcp        0      0 0.0.0.0:139             0.0.0.0:* 
             LISTEN
tcp        0      0 127.0.0.1:631           0.0.0.0:* 
             LISTEN
tcp        0      0 0.0.0.0:445             0.0.0.0:* 
             LISTEN
unix  2      [ ACC ]     STREAM     LISTENING     8416
    /tmp/.gdm_socket
unix  2      [ ACC ]     STREAM     LISTENING     9371
    @/tmp/dbus-WBglF9GjV7
unix  2      [ ACC ]     STREAM     LISTENING     8605
    /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     9366
    /tmp/ssh-wiPhAb6380/a gent.6380
unix  2      [ ACC ]     STREAM     LISTENING     9391
    /tmp/orbit-admin/linc -1918-0-30cc9a82586be
unix  2      [ ACC ]     STREAM     LISTENING     7951
    @/tmp/hald-local/dbus -bBBJOSCqb7
unix  2      [ ACC ]     STREAM     LISTENING     9401
    /tmp/orbit-admin/linc -18ec-0-2a6600337b6ad
unix  2      [ ACC ]     STREAM     LISTENING     9602
    /tmp/.ICE-unix/6380
unix  2      [ ACC ]     STREAM     LISTENING     9611
    /tmp/keyring-eZtyEl/s ocket
unix  2      [ ACC ]     STREAM     LISTENING    
13579    /tmp/orbit-admin/linc -191f-0-1de6ba898320a
unix  2      [ ACC ]     STREAM     LISTENING    
13600    /tmp/orbit-admin/linc -1921-0-1e908c41d9395
unix  2      [ ACC ]     STREAM     LISTENING    
16055    /tmp/orbit-admin/linc -194a-0-3271e4567c238
unix  2      [ ACC ]     STREAM     LISTENING    
16082    /tmp/orbit-admin/linc -194f-0-79adc4294f7c5
unix  2      [ ACC ]     STREAM     LISTENING    
16101    /tmp/orbit-admin/linc -1953-0-79adc42974484
unix  2      [ ACC ]     STREAM     LISTENING    
16135    /tmp/orbit-admin/linc -1957-0-64050cd0dcf0c
unix  2      [ ACC ]     STREAM     LISTENING    
16149    /tmp/orbit-admin/linc -1951-0-64050cd0ea1a0
unix  2      [ ACC ]     STREAM     LISTENING    
16178    /tmp/orbit-admin/linc -195b-0-5626d5f141ef4
unix  2      [ ACC ]     STREAM     LISTENING    
16229    /tmp/orbit-admin/linc -1961-0-5626d5f1f4056
unix  2      [ ACC ]     STREAM     LISTENING    
16251    /tmp/orbit-admin/linc -1964-0-473b47c41ebe4
unix  2      [ ACC ]     STREAM     LISTENING    
16315    /tmp/orbit-admin/linc -195d-0-7250f309780ab
unix  2      [ ACC ]     STREAM     LISTENING    
16339    /tmp/mapping-admin
unix  2      [ ACC ]     STREAM     LISTENING    
20086    /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING    
16381    /tmp/orbit-admin/linc -1975-0-793b013045570
unix  2      [ ACC ]     STREAM     LISTENING    
16398    /tmp/orbit-admin/linc -1977-0-793b0130cb2a7
unix  2      [ ACC ]     STREAM     LISTENING    
16415    /tmp/orbit-admin/linc -1979-0-2ad3c5d75a4c3
unix  2      [ ACC ]     STREAM     LISTENING    
16797    /tmp/orbit-admin/linc -1994-0-34ba56bf9908
unix  2      [ ACC ]     STREAM     LISTENING    
16899    /tmp/orbit-admin/linc -19c3-0-1ef471c147b75
unix  2      [ ACC ]     STREAM     LISTENING    
26077    /tmp/orbit-admin/linc -2e95-0-474b2f83b8681
unix  2      [ ACC ]     STREAM     LISTENING     7935
    /var/run/dbus/system_ bus_socket
unix  2      [ ACC ]     STREAM     LISTENING    
13609    @/tmp/fam-admin-
unix  2      [ ACC ]     STREAM     LISTENING     9091
    /var/run/sdp


Sorry for the late reply. Had some major hardware issues at work.

---

### Post by nocturn on 2005-12-23
[QUOTE=dirkvl]admin@SERVER00:~$ netstat -an | grep LISTEN
tcp        0      0 127.0.0.1:32769         0.0.0.0:* 
             LISTEN
tcp        0      0 127.0.0.1:32770         0.0.0.0:* 
             LISTEN
tcp        0      0 0.0.0.0:139             0.0.0.0:* 
             LISTEN
tcp        0      0 127.0.0.1:631           0.0.0.0:* 
             LISTEN
tcp        0      0 0.0.0.0:445             0.0.0.0:* 
             LISTEN
[/quote]

Swat (901) is not listening in there.  How did you install and set it up?
If I remember correct, it runs from inetd or xinetd, so that should be running too.

> 
Sorry for the late reply. Had some major hardware issues at work.


It has taken me a while to respond too, I have been at home, sick for 3 days.

---

### Post by guitard00d on 2005-12-25
[QUOTE=nocturn]Actually, I had to admin a couple of windows boxes along the way and over the course of a year, they were a lot harder and more time consuming then their *nix counterparts.[/QUOTE]

Amen to that, in my opinion, obscuring things with a GUI and limiting an admin's capabilities is a bad design plan all together. If people think a GUI makes the task of marrying a Windows and a *nix system any easier, get a Mac and test that theory again.

---

### Post by ottothecow on 2005-12-31
I would be forced to say that for pure server usage (and first time running linux at that), ubuntu probobly isnt the best choice.  Mandriva offers server products and most everything under that brand is geared towards easy of use/configuration.  Other companies supply other linux server packages that come with many services pre-installed that you are forced to add to a base ubuntu distro to get a server setup.

Ubuntu is great on the desktop but if you are trying to run a server and it is your first linux server and you are not fully comfortable with the CLI, there are probobly better choices.

---

### Post by sham69 on 2006-03-02
Might be easier to set up the regular install of Ubuntu, instead of the base server system if all you want to do is share a folder with Samba and like to use a gui. You can use VNC to control it from your Windows machine.
Or you could get Xandros OCE (free version) linux. Absolutely no sweat to setup a windows share and browse the network, but not officially for commercial use....they have a commercial product that interfaces with Windows AD domains.

---

### Post by Dragineez on 2006-03-06
> I believe that forums are not for picking on people, but for serious aid, and I will state at once that throwing bullshit at me will have no effect at all.
To correct a misunderstanding : with novice users I meant novice LINUX users.
When you're a windows sysadmin and you have to dig yourself into linux, the job should be made easy, not harder. If you can't see the simple facts of business life ("time is money"), that's too bad.This is actually a difficult concept for an experienced computer professional to wrap their minds around. I know I had trouble with it in the beginning. Believe it or not - you ***are*** a novice.

[Linux Is Not Windows]("http://linux.oneandoneis2.org/LNW.htm")

---

### Post by LivnLarge on 2006-03-15
I just wanted to say that I am a complete beginner with Linux and I'm using Ubuntu and only Ubuntu due to fact of installation errors on other distros.  The very first thing I loved about Ubuntu is how it has Gnome for easiness or good ol' terminal for basics and simplicity to some users.  Being a Windblows user my whole life made it quite difficult for the transition but it was one that I enjoyed.  The reason I'm using Linux is I wanted to learn how to use this powerful device i am now typing on and spending so many hours of my life in front of. Instead i was using a device created by one person/persons who yes made it easier for people to use a computer but yet in reality those people have no idea what is actually going on to allow them to do what they are doing which kinda symbolizes a zombie if you ask me.. a dont know dont care it just works idea.  Which to me is a bad habit we humans tend to have.  Linux offers the chance for newbies like me and novices as well to learn something powerful. That's why I'm here. I have had problems with my ATI video chip, my wifi driver, and even mounting an external harddrive but i will have to say it was some trip to find out how to resolve these problems. I learn more than I thought I could in three weeks which i felt would have taken me a year. 

 As of right now I am also trying to get Samba set up for my home network which is a wireless network connected thru a wireless router where the host computer is a windows laptop.  I read some how tos on samba and got discouraged easily since they didnt exactly say the same things in the steps.  Right now Im not worry about Samba now that I have learned of VNC(virtual network computing) now that to me is alot cooler than normal networking.  If you are worried about secureness then check out how to with vnc tunneling with ssh.  Right now I cant wait to get everything all ready to go soi can sit back enjoy the power and learn more about these extra consoles we have (ctrl-alt- F1,F2,F3 etc)  

I dont need to learn Samba, since i have a windows network that works fine for both computers to share files... but you have to start somewhere to learn not to rely on such a terrible OS like windows.  Sadly I rely on Windows ONLY for my P2P file sharing.  Im a crazy file downloader.. i got a 200GB HD come on now!

---

### Post by jalonsom on 2006-04-28
[QUOTE=dirkvl]I took a glance at the two links, which led me to how to's for samba, winbind and pam.
Bottomline : it's still hard.
- You have to edit 7 text files and be very carefull you place your server and domain name in the right place (which isn't explained very clearly at all in the how to)
- You have to type 9 commandlines and hope they each start the selected service/join.

However, this commandline crap isn't going to get me down.
Sometime (hopefully in the near future) someone is going to create a good gui for automating all these actions.
Face it guys : all you need to join a server in a domain is the servername, domainname and an admin for the windows domain.
Where's the wizard/gui ?
I haven't even got a clue how to use a domain group to put security on a share. Is there no "how to" for this ?
I'm afraid this simply does not do. This is not user friendly.[/QUOTE]


I think you missed this in one of the links to topics:

[QUOTE=intangible]I have already set up my Linux boxes manually to join the domain, but I was wondering if anyone has had any luck with this tool: [http://sadms.sf.net](http://sadms.sf.net) ?  It looks like the perfect tool to do all this with a gui instead of manually, and they have a Ubuntu package :D[/QUOTE]

Seems like a GUI to do what you want.

---

