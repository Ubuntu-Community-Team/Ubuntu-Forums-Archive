---
title: "ATI Radeon 4350"
date: 2013-04-15
forum: Hardware
---

### Post by King Dude on 2013-04-15
I attempted to boot Ubuntu 12.10 x64 from a second hard drive on my Desktop (can't remember exact model, some HP Pavilion). So far it worked perfectly- at least until I tried getting the ATI Catalyst driver to work. At first the driver didn't want to install, giving me errors about root headers, but once the root headers were fixed and the driver was installed I rebooted to find that my display was strange. When I say strange, I mean that I was missing the task bar and screen displayed magnified & blurry as though it would if you were to run Windows without a GPU driver.

My video card is an ATI Radeon 4350 512MB, and my driver is Catalyst 13.1 legacy (I believe...).

Keep in mind I'm an immigrant from the Windows community, and despite having a decent computer background this is a whole new world to me.

---

### Post by Yellow Pasque on 2013-04-15
AMD dropped support for RadeonHD 4xxx series in the proprietary fglrx/Catalyst driver. Your options:
1) Go back to Ubuntu 12.04, where you can still use fglrx/Catalyst legacy release
2) Remove fglrx/Catalyst and use open-source driver
3) Use the following PPA to downgrade the X server and allow you to use fglrx/Catalyst legacy with Ubuntu >= 12.10: [https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx)

#1 is probably best if you absolutely need Catalyst to game or get video decode acceleration

#2 should work best if you're not a heavy gamer. It's what I personally use on my RadeonHD 4550.

#3 is a hackish approach and may cause package management issues in the future, but a lot of folks are using it. Make sure you remove the current fglrx package if you go that route (you need the fglrx-legacy package that the PPA provides).

---

### Post by Mark Phelps on 2013-04-15
Would strongly recommend against option 3) in Temujin's post, and in favor of option 2).  

Being new to Ubuntu, the last thing you want do deal with is a kludged system that is going to yield really major problems maintaining it down the road.

You probably don't even need the restricted AMD drivers.

---

### Post by King Dude on 2013-04-15
Hmm... any recommendations for a decent open source driver that supports my video card?

---

### Post by QIII on 2013-04-15
Hello!

The open source Radeon driver you weere using when you first install Ubuntu is the open source driver.  You don't need to install anything further.  If you have uninstalled fglrx, you are using it now.

Best wishes!

---

### Post by King Dude on 2013-04-16
Cool. Also, I might need help getting my system back to normal. The task bar is gone, and I'm not sure what to do with the terminal.

---

### Post by QIII on 2013-04-16
Since that is a different problem from the graphics issue, you should probably begin a new thread with a new subject line and ask for help with these issues.

Feel free to refer to this thread if it it will help others understand.

Thanks and good luck.

---

### Post by zrdc28 on 2013-04-16
removing xorg.conf should put you back to the open source driver. ** mv /usr/share/X11/xorg.conf  /usr/share/X11/xorg.conf.old ** will rename it. then reboot.

---

### Post by Yellow Pasque on 2013-04-16
> **King Dude said:**
> Cool. Also, I might need help getting my system back to normal. The task bar is gone, and I'm not sure what to do with the terminal.

[http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Removing_Catalyst.2Ffglrx)

---

