---
title: "Nvidia driver 331 upgraded to 340.93 doesn't work properly."
date: 2015-09-30
forum: Hardware
---

### Post by luca-dgh on 2015-09-30
Hi to all.
I'm using ubuntu 12.04 with gnome classic, kernel is 3.2.0-90. I have a GeForce 210 until yesterday with nvidia official driver 331 was working perfectly, then security update, new nvidia 340.93 and now the page refresh is a mess. When I use Mozilla, Libreoffice, Thunderbird, or every else program that need to scroll or refresh the page everything get messed and I need to scroll up and down several times, or press enter, or click the mouse, or other tricks to get a readable page.
There is something I can tune in the driver?
Is better to change to open driver Nouveau?
Thanks for your help.

---

### Post by luca-dgh on 2015-09-30
I would like to downgrade to 331 version, but has been removed from repos.
I tried with the higher 352 but my GeForce is not supported there.
I tried with 340 updates, the problem is less evident with that version, but has not been solved.
The driver selector in Gnome doesn't give me the choice to Nouveau, I tried to read some tutorials but all of them are 3-5 years old.
What I can do?

---

### Post by Bashing-om on 2015-09-30
luca-dgh; Well ...

The 340 driver is correct per:
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
However, a lot depends on the xserver version :
[http://nvidia.custhelp.com/app/answers/detail/a_id/3142/~/support-timeframes-for-unix-legacy-gpu-releaseshttp://nvidia.custhelp.com/app/answers/detail/a_id/3142/~/support-timeframes-for-unix-legacy-gpu-releases](http://nvidia.custhelp.com/app/answers/detail/a_id/3142/~/support-timeframes-for-unix-legacy-gpu-releaseshttp://nvidia.custhelp.com/app/answers/detail/a_id/3142/~/support-timeframes-for-unix-legacy-gpu-releases)

One can get the xserver version on the system from the result of terminal command:
```

X -version

```

Maybe with purging all Nvidia drivers, and (RE-)installing the 340 version all will be put aright ?

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by luca-dgh on 2015-10-04
> **Bashing-om said:**
> luca-dgh; Well ...

The 340 driver is correct per:
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html) 


My video card is in the list

> However, a lot depends on the xserver version :
[http://nvidia.custhelp.com/app/answers/detail/a_id/3142/~/support-timeframes-for-unix-legacy-gpu-releaseshttp://nvidia.custhelp.com/app/answers/detail/a_id/3142/~/support-timeframes-for-unix-legacy-gpu-releases](http://nvidia.custhelp.com/app/answers/detail/a_id/3142/~/support-timeframes-for-unix-legacy-gpu-releaseshttp://nvidia.custhelp.com/app/answers/detail/a_id/3142/~/support-timeframes-for-unix-legacy-gpu-releases)

One can get the xserver version on the system from the result of terminal command:
```

X -version

```

```

luca@pc-sala:~$ X -version
X.Org X Server 1.11.3
Release Date: 2011-12-16
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.42-61-generic x86_64 Ubuntu
Current Operating System: Linux pc-sala 3.2.0-91-generic #129-Ubuntu SMP Wed Sep 9 10:56:06 UTC 2015 x86_64
Kernel command line: BOOT_IMAGE=/vmlinuz-3.2.0-91-generic root=UUID=a2b476c2-a487-4562-88b1-1a139a1dde55 ro quiet splash
Build Date: 12 February 2015  02:49:01PM
xorg-server 2:1.11.4-0ubuntu10.17 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.30.2
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.

```

So, my X-server version is out of date?

> 
Maybe with purging all Nvidia drivers, and (RE-)installing the 340 version all will be put aright ?[INDENT][INDENT]maybe yes
[/INDENT]
[/INDENT]

I don't have any other nVidia driver installed.

---

### Post by Bashing-om on 2015-10-04
luca-dgh; Yeah ;

That too is the way I read it .. technology has passed you by.
Let's await a guru of graphics to advise further, but looks to me like the only option available now is open source.
I would like to be shown in error .

[INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT]

---

### Post by luca-dgh on 2015-10-04
Ok, I wish to have a try with Nouveau driver, but how I can try that?
I don't find any valid tutorial to achieve it.

---

### Post by Bashing-om on 2015-10-04
luca-dgh; Sure;

While we await wiser heads.
To remove Nvidia and install the open source driver:
```

sudo apt update
sudo apt upgrade
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo apt-get purge nvidia*
sudo apt-get install linux-headers-generic
sudo apt-get install xserver-xorg-video-nouveau

```

Reboot and you will be using nouveau .
A great chance it will work out just fine.

[INDENT][INDENT]it could happen
[/INDENT][/INDENT]

---

### Post by luca-dgh on 2015-10-18
Sorry for being late (sorry as well for my poor english :) ).
I tried to activate Nouveau driver, but I had no luck :( . The system can boot, the splash image doesn't appear and the video get confused, but after that Gnome starts (yes, I still use Gnome Classic ;) ), I can see the access screen where I can choose the user to login, for each user I can also see the desktop image, but when I try to login a user (any of them) it can't login and it bumps back to the screen where to choose the user to login.
Some messages appear on the top left corner in "terminal style" but are very quick and I can't read nothing.
After that I reinstalled the nvidia driver and rebooted, it looks like to have improved the screen performances, probably I had some trash in older nvidia installations that has been removed with the purge, for example now Firefox is well readable, but Gnome windows still have some problems.
I attach the Xorg logs, the failsafe log ends with a fatal error because the server can't find a valid configuration for the screen  (LG Electronic 19M35, with nvidia driver use a resolution of 1366x768). I don't know if that is actually the problem, it's just a try.
If you can help me to find out what is the real problem I'll be eternally grateful to you.

PD: I tried to deactivate Compiz, with Metacity 2D everything works perfectly with nVidia driver. Do you think that OpenGL environment can be the problem? Is it possible to tune up OpenGL parameters?

---

### Post by night_sky2 on 2015-10-18
This is a good exemple of why you should stick with a tested, proven graphic driver and never do updates unless you are a gamer and needs cutting-edge features.

In ''Additional drivers'' you are supposed to have the legacy 173 and 304 Nvidia drivers offered as options. That is the case for me on Ubuntu 14.04.

The 304.128 should be fine for the GeForce 210 card.

---

### Post by luca-dgh on 2015-10-18
May be you are right, I should have fixed the driver to avoid upgrades, but I trusted in nVidia and in the last 9 years I had no one problem with nVidia drivers on every version of Ubuntu I tried since Dapper Drake 6.06 .
Now I found a problem and I try to sort it.
So your advice is to use 304 driver. I'll try it.
Thank you.

---

### Post by night_sky2 on 2015-10-18
> **luca-dgh said:**
> May be you are right, I should have fixed the driver to avoid upgrades, but I trusted in nVidia and in the last 9 years I had no one problem with nVidia drivers on every version of Ubuntu I tried since Dapper Drake 6.06 .
Now I found a problem and I try to sort it.
So your advice is to use 304 driver. I'll try it.
Thank you.
My philosophy is if it ain't broke, dont fix it. Automatically updating drivers can cause some unexpected issues.

What's offered in the ''Additional Drivers'' tool as permanent options should be enough to cover your bases for the Geforce 210 without the need to do updates.


Cheers.

---

### Post by luca-dgh on 2015-10-18
I installed 304 driver and it seems that everything is ok, I also sticked it ;) . 
Thank you so much.

---

