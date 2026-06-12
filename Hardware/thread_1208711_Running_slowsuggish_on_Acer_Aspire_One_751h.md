---
title: "Running slow/suggish on Acer Aspire One 751h"
date: 2009-07-09
forum: Hardware
---

### Post by dtmoody on 2009-07-09
Well, please help me out here... Im a linux nube so bare with me.
I've used Ubuntu for a few years, but I have never had to dive into any issues with getting something to work, so I guess I have been lucky.

Installed the lastest Ubuntu NBR alongside Vista via USB drive as listed
in the instructions on the Ubuntu site.  The install went as it should.
I am currently typing this on the "functioning" system.

However, the main reason I wanted Ubuntu on this netbook was because the
Vista crap it came with is just a resource hog, and I use Ubuntu on my desktop and prefer it...

I'm having a few issues:

The overall interface/GUI is very slow and sluggish.

You cannot set the native screen size to 1366×768, it only lets you have
1024x768 (4:3)

A few LED's are not working.  One I notice is the wireless LED.

Anyone care to point me in the direction I need to fix these issues if it is even possible?

I would like to know if I just need to go back to Vista or XP with this netbook before I pull my remaining gray hair out...lol

THANKS FOR YOUR HELP!

---

### Post by bandyta on 2009-07-13
I just purchased an Aspire One 751h, and am having the same issues.  Everything seems to be working but it is just sooooooo slow I can barely navigate through it.

---

### Post by ubudex on 2009-07-17
First Gnome is to heavy for a netbook, you should try something like Xubuntu or [Crunchbang]("http://crunchbanglinux.org/").

For the display you need to follow [this directions]("http://ubuntuforums.org/showthread.php?t=1190639").

For the LEDs install linux-backports-modules-jaunty from Package Manager. ;)

---

### Post by azile19 on 2009-07-21
I'm having the same problem with my aspire one.  Altho I have gotten the resolution working, the GUI is unbearably slow.  If I want to switch from gnome to xubuntu or crunchbag, does this involve reinstalling the OS? Or is there an easier way to change it?

---

### Post by bacil on 2009-07-21
I got one ZG5 running fully blown 9.04 with kde (kubuntu) and didnt have any of these problems. only struble i had was mmc card reader.

---

### Post by ubudex on 2009-07-21
> **azile19 said:**
> I'm having the same problem with my aspire one.  Altho I have gotten the resolution working, the GUI is unbearably slow.  If I want to switch from gnome to xubuntu or crunchbag, does this involve reinstalling the OS? Or is there an easier way to change it?

If you have an existing Ubuntu installation, it is possible to install Xubuntu and retain your current installation. To do so, just go into Synaptic and install the xubuntu-desktop package. Next time you login, you can choose Xfce4 from the Session menu on the login screen. If you want to have a default Xubuntu install but have installed Ubuntu, you can remove all Gnome packages by following instructions on [this page]("http://www.psychocats.net/ubuntu/purexfce").

For crunchbang you could reinstall the os or install lxde from the repositories and modify to your liking.

---

### Post by azile19 on 2009-07-22
I now have xubuntu running like you said, however as I had started with Ubuntu Remix, I still get their weird home page thing and am wondering if this is some of the cause of the sluggishness.   Even with xubuntu, my CPU is still running at 95%ish all the time.  Do you have any more ideas of things to try to calm down the CPU, or at least how to get rid of the home page to have just a normal looking desktop?

---

### Post by azile19 on 2009-07-22
The fix to get a normal desktop is to run desktop-switcher in the terminal.

---

### Post by Dovydas on 2009-10-29
I am having the same problem on Acer AO751h. It is sooooo slow.

---

### Post by Dovydas on 2009-10-29
BUMP for help.

---

### Post by elgandoz on 2009-10-31
The Problem of this netbook is the missing driver for the Intel video Card GMA500 (Driver Poulsbo isn't supported yet). 
For a quick fix of the issue, check for the Lucazade workaround,
he gives a easy to install script, and even if it doesn't fix completely the problem, it works (native resolution and smoother performances)

Here some specs:
[http://gma500re.altervista.org/php5/index.php?title=Main_Page](http://gma500re.altervista.org/php5/index.php?title=Main_Page)

Here the installation script (choose PPA version)
[http://gma500re.altervista.org/php5/index.php?title=Ubuntu_9.10](http://gma500re.altervista.org/php5/index.php?title=Ubuntu_9.10)

---

### Post by Steveaustin1971 on 2010-05-23
I have the Aspire one 751h, and the issue is the GMA500 video, I had issues with Ubuntu as well and the only way I got this netbook running smoothly was switching to Mandriva. It runs the proper resolution right away, and the wifi works smoothly, light and all with the XP drivers through ndiswrapper. I run Mandriva One 2010 with XFCE, and its faster than it was on Vista or Windows 7 (which ran well) and it is stable. The Ubuntu netbook remix has a lot of issues and actually runs slower than regular ubuntu distro's. If you decide to run Mandriva you can use Mandriva seed to put the live cd on a usb drive.  Hope this helps a bit.

---

