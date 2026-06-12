---
title: "Need help,problem after instalation"
date: 2009-05-24
forum: Installation &amp; Upgrades
---

### Post by sevic33 on 2009-05-24
I do triple boot,XP+backtrack+ubuntu on my laptop.I install Ubuntu last so i cant acces backtrack before i edit GRUB.
But her is the problem,when i try to run Ubuntu i got this massage:

```
Ubuntu is running in low-graphics mode

Your screen,graphic card,and input device settings could not be detected correctly.You will need to configure these yourself
```

I press ok and got this massage:

```
What would you like to do?

*Run Ubuntu in low-graphics mode for just this session

*Reconfigure graphics

*Troubleshoot the error
```

If i press *Run Ubuntu in low-graphics mode for just this session i got this massage:

```
Stand by one minute while the display restarts...
```

and i wait and nothing hapen.
Same if i try if i try Reconfigure graphic

But when i try to Troubleshoot the errot i got options:

```
What information would you like to review?

*Review the xserver log file

*Review the startup errors

*Edit configuration file

*Archive configuration and logs
```

So can anyone can help me with this problems?

---

### Post by sevic33 on 2009-05-24
I forget to tell its Ubuntu 8.10
And sorry for posting in wrong section,now i see there is a laptop problem board

---

### Post by tommcd on 2009-05-24
Try booting to recovery mode and choose the option "xfix fix video". Then reboot.
If that does not work, then what graphics chip does the laptop have? If you don't know,then boot the Ubuntu live CD, open a terminal, and run:
```
lspci | grep -i vga
```
This will tell us what graphics chip the laptop has. You can then hopefully install the appropriate driver for it.

---

### Post by sevic33 on 2009-05-25
> **tommcd said:**
> Try booting to recovery mode and choose the option "xfix fix video". Then reboot.
If that does not work, then what graphics chip does the laptop have? If you don't know,then boot the Ubuntu live CD, open a terminal, and run:
```
lspci | grep -i vga
```
This will tell us what graphics chip the laptop has. You can then hopefully install the appropriate driver for it.

I try xfix fix video,doesnt work.
If i try boot Live CD i got error,same like trying boot from Grub.
I check drivers in Windows,her is the name:
```
VIA Chrome9 HC IGP Family
```
Is there any way to acces just terminal from Live CD?

---

### Post by tommcd on 2009-05-25
> **sevic33 said:**
> 
If i try boot Live CD i got error,same like trying boot from Grub.
Did the live CD bootup ok when you first installed Ubuntu? How did you install Ubuntu then if the live CD doesn't work? Did you use the alternate CD?
> **sevic33 said:**
> 
Is there any way to acces just terminal from Live CD?
You can boot Ubuntu to recovery mode and you will be presented with a root terminal. Boot the installed Ubuntu on the hard drive, not the live CD. You can then run **lspci | grep -i vga** to report what graphics chip you have.
> **sevic33 said:**
> 
I check drivers in Windows,her is the name:
VIA Chrome9 HC IGP Family

Since you have a VIA Chrome, i would guess that you probably need the **xserver-xorg-video-openchrome** driver.
According to this page, the openchrome driver is not present in Ubuntu 8.10:
[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)
I can't confirm this, since I am using Ubuntu 9.04.
Do this:
Boot to recovery mode and run:
```
lspci | grep -i vga
```
Report back the exact name of the graphics chip. While in recovery mode, also run:
```
aptitude search openchrome
```
On Ubuntu 9.04 it reports:
```

i A xserver-xorg-video-openchrome

```
The "i" means installed, and the "A" means automatically installed. If it reports a "p" before the package, it means that it is not installed. You could then install it with:
```
sudo apt-get install xserver-xorg-video-openchrome
```
If it reports back nothing, then the driver is not present in the 8.10 repos. Your option then would be to either compile the driver manually as per the instructions on the above link, or install Ubuntu 9.04, which has the openchrome driver and (hopefully) will work for you. 
You may possibly need the **unichrome** driver. This driver is not in the 9.04 repos. It is available from VIA though:
[https://help.ubuntu.com/community/UniChrome](https://help.ubuntu.com/community/UniChrome)
[http://www.viaarena.com/default.aspx?PageID=2&OSID=45&CatID=3220](http://www.viaarena.com/default.aspx?PageID=2&OSID=45&CatID=3220)

First report back the exact output from **lspci | grep -i vga** and I will try to determine what driver you need. I am not familiar with VIA graphics drivers though. Perhaps someone else can provide better guidance once you report back what lspci reports.

---

### Post by albinootje on 2009-05-25
> **tommcd said:**
> 
Since you have a VIA Chrome, i would guess that you probably need the **xserver-xorg-video-openchrome** driver.

For the VIA Unichrome there's the via driver (From Xorg I think), the openchrome driver and the unichrome driver projects.

Perhaps this is helpful : [https://answers.launchpad.net/ubuntu/+question/11807](https://answers.launchpad.net/ubuntu/+question/11807)
See the newest comments.

---

### Post by tommcd on 2009-05-26
> **albinootje said:**
> For the VIA Unichrome there's the via driver (From Xorg I think), the openchrome driver and the unichrome driver projects.

In Ubuntu 9.04 when I run "aptitude show xserver-xorg-video-via" it reports:
> 
Description: X.Org X server -- VIA display driver (dummy transitional package)
 This transitional package helps users transition to the OpenChrome driver. Once
 this package and its dependencies are installed you can safely remove it.
Homepage: [http://www.openchrome.org](http://www.openchrome.org)

So it seems that, at least on 9.04, the driver is now openchrome.
It seems that the opnchrome driver is available in Intrepid:
[http://packages.ubuntu.com/search?keywords=openchrome&searchon=names&suite=intrepid&section=all](http://packages.ubuntu.com/search?keywords=openchrome&searchon=names&suite=intrepid&section=all)
I suppose the OP could use the xorg.conf that is posted in one of the more recent comments in the link you gave as a starting point.

---

### Post by acruzcosta on 2011-08-08
Hi, did you solve this problem?
I have a HP mini with this via chrome 9 hc igp family.
I´ve tried to run ubuntu 11.04 but that freeze twice and i gave up.
Then I installed ubuntu 10.10, but youtube doesn´t run as windows xp. So I gave ubuntu and tried jolicloud. But jolicloud didn´t even started.

What I´m supposed to do with I would like to run linux in my net book?

Regards.

---

