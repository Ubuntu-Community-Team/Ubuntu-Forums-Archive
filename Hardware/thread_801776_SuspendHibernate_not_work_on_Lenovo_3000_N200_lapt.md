---
title: "Suspend/Hibernate not work on Lenovo 3000 N200 laptop using Ubuntu 8.0.4"
date: 2008-05-20
forum: Hardware
---

### Post by ngduonglam on 2008-05-20
Hello all,

Can any of you tell me how to fix the problem on my laptop?
The problem is that I can not suspend or hibernate my laptop. When I chose these 2 options, the computer seems to suspend/hibernate, but:
- for suspend: it went to sleep, the sleep light turn on, but can not resume when I press any key, event the power button.
- for hibernate: can not went to hibernate state.
And in both cases, it's ended by press and keep the power button until it turn off --> sometimes leak to problem that can not boot.

Can any one help me on this? Thanks.

---

### Post by cprofitt on 2008-05-21
What video card is in that particular Lenovo?

---

### Post by ngduonglam on 2008-05-22
> **PrivateVoid said:**
> What video card is in that particular Lenovo?
An nVidia GeForce Go 7300 card.

---

### Post by CazperII on 2008-05-24
The hardware is perfectly capable of hibernate/sleep. I have a Lenovo N200 with geforce 7300 and hibernate/sleep works fine.

---

### Post by cprofitt on 2008-05-25
> **ngduonglam said:**
> An nVidia GeForce Go 7300 card.

OK...

In most cases I have seen with Nvidia cards the wakeup problem has been that the computer does actually come out of suspend, but it has either a black or white screen. Typically users have been able to type in their password and then the screen appears.

> I found this solution for this bug... it has worked for me so far: 

Go to System --> Administration --> Software Sources and select the Third-Party Software tab. Click on Add and enter the following line:

    deb [http://ppa.launchpad.net/superm1/ubuntu](http://ppa.launchpad.net/superm1/ubuntu) hardy main

Then click on Add again and enter the following line:

    deb-src [http://ppa.launchpad.net/superm1/ubuntu](http://ppa.launchpad.net/superm1/ubuntu) hardy main

Click on Close, then on Reload. Shortly your software updater will indicate that there are updates available for compiz. Install them, restart your machine and you are done. 

credit here goes to mario limoncello which came up with this fix and published it on launchpad 

cheers
credit to cespinal in [this thread]("http://ubuntuforums.org/showthread.php?t=767620&page=2")

---

### Post by ngduonglam on 2008-05-27
But it does not work in my case :(

---

### Post by Maratonda on 2008-05-29
Is this it?
[https://bugs.launchpad.net/ubuntu/+bug/226279]("https://bugs.launchpad.net/ubuntu/+bug/226279")

---

