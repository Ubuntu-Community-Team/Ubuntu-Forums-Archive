---
title: "Netconfig command ?!?"
date: 2005-11-07
forum: General Help
---

### Post by victorche on 2005-11-07
Well again as a Slackware lover who wants to continue testing this lovely Kubuntu...
I was wondering how to setup my girfriend's PC internet connection...
And I tried for "**netconfig**" command... Ang I was so, so, so surprised!
There is not "netconfig" in Kubuntu :(
Adept also can't find a package with that name... /Maybe it is a part of another package/... Well Slackware/Fedora have it for sure ;)

And the graphical tool for network settings... I can see there my eth0 device... But I can't edit it... I need the "Administrator Mode"... And I am clicking... typing my pass, then nothing... clicking again, typing again... no result... eth0 as an interface is still not accessible by me :D So, I am still clicking on "Administrator Mode"... Still typing my password...
As far as I can see I won't be able to use this sweet and lovely graphical interface for configuring the network...
So, please tell me!!! How can I use NETCONFIG here on this Kubuntu 5.10?!?!?
:???:

---

### Post by mlomker on 2005-11-07
Ubuntu is Debian-based, so...

There are bugs in the KDE system control panel right now.  If you launch it using **kdesu kcontrol** or **kdesu systemsettings** from a terminal or the Run line it'll behave better.

I personally just edit /etc/network/interfaces manually.

---

### Post by victorche on 2005-11-07
[QUOTE=mlomker]Ubuntu is Debian-based, so...

There are bugs in the KDE system control panel right now.  If you launch it using **kdesu kcontrol** or **kdesu systemsettings** from a terminal or the Run line it'll behave better.

I personally just edit /etc/network/interfaces manually.[/QUOTE]
these bugs... are they for breezy or for dapper? And if they are in breezy, are they fixed in dapper?
And Ubuntu is Debian based... We know that ;)
But "Debian based" doesn't mean it shouldn't include such perfect tools like netconfig... Any ideas how can I use it in Kubuntu?
I am happy that there is at least joe in universe :???:

**Edit**: I want to ask something strange about joe also... See this file:
[ftp://archive.ubuntu.com/ubuntu/pool/universe/j/joe/joe_3.1-0.2.dsc](ftp://archive.ubuntu.com/ubuntu/pool/universe/j/joe/joe_3.1-0.2.dsc)
It is written in that file:
Build-Depends: libncurses-dev

Well when I found joe with Adept and marked it for install, it told me that one file only will be installed... joe itself. But the strange thing is - I don't have libncurses-dev installed... So Adept downloaded joe and installed it without problems. And it works :) Then what this depends means? Is it wrong or what?

---

### Post by mlomker on 2005-11-07
[QUOTE=victorche]these bugs... are they for breezy or for dapper? And if they are in breezy, are they fixed in dapper?[/quote]

I hope they will be, but Breezy was just released.  Only the truly brave are running Dapper at this point.

The good news is that Mark Shuttleworth made some comments about throwing more money behind Kubuntu.  Up until now Kubuntu was just an offshoot that wasn't that tightly affiliated with Ubuntu.

> netconfig... Any ideas how can I use it in Kubuntu?

I've never heard of it, so I assumed it was for the non-Debian distros that you mentioned.

> I am happy that there is at least joe in universe :???:

I like nano.

---

### Post by victorche on 2005-11-07
I hope you saw my last edit up there...
And netconfig... a console tool like wizard... it asks questions about your network, you give the answers and here you go - you network is up and running ;)
See a shot here:
[http://hem.bredband.net/emil1000/sle/slwhbkimg18.png](http://hem.bredband.net/emil1000/sle/slwhbkimg18.png)

---

### Post by mlomker on 2005-11-07
Build-depends is if you want to build it from source.  It's different than a regular dependency.

I'm reading a book called [The Debian System]("http://www.amazon.com/exec/obidos/tg/detail/-/1593270690/qid=1131409399/sr=8-1/ref=pd_bbs_1/104-3169223-3107119?v=glance&s=books&n=507846") right now and am just working through the chapter on DEB files.  It's a great reference book, but probably more than I need to know.

---

### Post by derek19 on 2005-11-07
[QUOTE=victorche]Well again as a Slackware lover who wants to continue testing this lovely Kubuntu...
I was wondering how to setup my girfriend's PC internet connection...
And I tried for "**netconfig**" command... Ang I was so, so, so surprised!
There is not "netconfig" in Kubuntu :(
Adept also can't find a package with that name... /Maybe it is a part of another package/... Well Slackware/Fedora have it for sure ;)

And the graphical tool for network settings... I can see there my eth0 device... But I can't edit it... I need the "Administrator Mode"... And I am clicking... typing my pass, then nothing... clicking again, typing again... no result... eth0 as an interface is still not accessible by me :D So, I am still clicking on "Administrator Mode"... Still typing my password...
As far as I can see I won't be able to use this sweet and lovely graphical interface for configuring the network...
So, please tell me!!! How can I use NETCONFIG here on this Kubuntu 5.10?!?!?
:???:[/QUOTE]

for your admin mode problem:

[http://bugzilla.ubuntu.com/show_bug.cgi?id=8681#c59](http://bugzilla.ubuntu.com/show_bug.cgi?id=8681#c59)

I have not tried this but it seems others have and it is working for them. I'm stuck in windows XP until i can get away from this Direcway crap....

---

### Post by WirelessMike on 2005-11-13
Is there a similar fix for this on kubuntu breezy amd64?

---

