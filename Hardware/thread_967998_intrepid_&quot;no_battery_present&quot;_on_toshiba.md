---
title: "intrepid &quot;no battery present&quot; on toshiba m305d"
date: 2008-11-02
forum: Hardware
---

### Post by zyconae on 2008-11-02
I've been using Ubuntu since 7.04 on many different forms of hardware, laptops, desktops, servers. I've also installed it for and helped many friends use it. I have a toshiba m305d and it took a bit of work but I got it running with 8.04 almost perfectly. However now (on 8.10 release 32bit) I can't get my battery's status to show up, it just says "no battery present". It will tell me when I have AC input though. It's kind of frustrating because it worked right away on the older 8.04LTS :confused: If you have any help I would really appreciate it :), also I can't get the wireless (atheros ar5007eg) running well like it used to.

---

### Post by couillard45682 on 2008-11-25
First of all, hi to everyone!
I was wondering if your problem has been resolved. I'm having the same issue : Ubuntu 8.10 doesn't seem to detect my battery, but in older version ( 7.04,7.10 and 8.04) everything was working fine. I have a Compaq Presario v2610ca. It's very frustrating never to don't know when my battery will die.
Thank you for your futur help.

p.s. sorry for my bad english, i'm french.

---

### Post by vagabond on 2008-11-25
I have the same problem with the same notebook model.  Power management is all FUBAR in 8.10.  On a unrelated note, I can't shut my computer down.  Choose shutdown and it reboots.  Shutdown from terminal, and it locks up half way through the shutdown.

---

### Post by rhenium3 on 2008-11-27
I have the same problem with 8.10.  I have a notebook MSI, and when the battery is plugged in I get a notice on how long it has until full charge.  But when it is not plugged in I get no notice what so ever. Any ideas?

---

### Post by larytet on 2008-12-20
Same here
Sony Vaio VGN-S460
No battery. I tried to plug out/in the battery - nothing. Even worse - the battery is completely discharged and not being charged. The battery is old but worked just fine under 8.04. The battery issue is rather critical.

---

### Post by shane2peru on 2008-12-20
> **zyconae said:**
> I've been using Ubuntu since 7.04 on many different forms of hardware, laptops, desktops, servers. I've also installed it for and helped many friends use it. I have a toshiba m305d and it took a bit of work but I got it running with 8.04 almost perfectly. However now (on 8.10 release 32bit) I can't get my battery's status to show up, it just says "no battery present". It will tell me when I have AC input though. It's kind of frustrating because it worked right away on the older 8.04LTS :confused: If you have any help I would really appreciate it :), also I can't get the wireless (atheros ar5007eg) running well like it used to.

Here is a link for your atheros wireless:  
[http://ubuntuforums.org/showthread.php?t=816780](http://ubuntuforums.org/showthread.php?t=816780)

As for your battery, same issue here.  If you suspend and bring it back up, battery should be recognized.  This is not really a fix, just a little info for ya.  Don't ask me why it works, it just does.  Mine also doesn't shutdown correctly.  When I hit shutdown, it reboots!  Everytime.  Annoying.

Shane

---

### Post by my_former_self on 2008-12-22
Same here. I have a Toshiba U405 (AMD64) & the battery status is always "On AC Power". Odd thing is, if I boot on battery power, it recognizes during initializing (text on screen) that it is on battery power; states it's on battery power & skips disk check. Once logged in, it still gives an AC Power plug symbol, but says it's on battery. Both instances still give no status (i.e. Percent Remaining) & terminal tells me I have no battery.

Another rather odd issue is this: 8.04 recognizes the battery but not the wireless Atheros card, but 8.10 does the opposite. Unfortunately, 8.04's kernel version doesn't support the ath9k driver for the Atheros card. I happened to find a script to compile the driver for any kernel, but it needs a connection to do so :) I'm going to try a VirtualBox install, compile with its connection, output to .deb and install to actual 8.04 installation. We'll see if it works!

---

### Post by larytet on 2009-01-05
> **larytet said:**
> Same here
Sony Vaio VGN-S460
No battery. I tried to plug out/in the battery - nothing. Even worse - the battery is completely discharged and not being charged. The battery is old but worked just fine under 8.04. The battery issue is rather critical.

In my case probably the battery is dead. Laptop does not charge even when the OS is down.

---

### Post by shane2peru on 2009-01-10
In my case the battery is not dead, it is new!  However I downloaded the Jaunty Alpha2 and it seemed as though it recognized the battery!  So when they get to a beta stage I may start running it.  We will have to see.  Intrepid has been nice, but not without it's fair share of difficulties for newer hardware.

Shane

---

### Post by micokoko on 2009-01-10
I have the Same Problem Here. I got is Toshiba Satellite® M305D-S4830.

My problem is that the battery indecator does not show up. Also evry time I shutdown my computer, it restarts by it self.

I have tried different Gome distributions (openSUSE 11.1, Sabayon 4) and i got the sane problem execpt that i can shutdoown safely. 

if any body got any ideas, please share us. 

THANKS

---

### Post by zyconae on 2009-01-28
Thanks to everyone for their replies and shane2peru for the wireless suggestion, I'm sorry I haven't checked back in a while, fresh install and all updates -> still no luck with battery but I'm going to keep looking and try shane's link for the wireless.

---

### Post by zyconae on 2009-01-30
New kernel and still no battery, also that wireless solution kind of sucks. I can't adjust my screen brightness either. The data rate keeps dropping down, I remember now that this card AR5007EG tends to drop data rates down all the way to 1Mb/s, it just crawls. I think I'm going back to 8.04.2 LTS.

---

### Post by adalf90 on 2011-06-01
could you solve it?
My Toshiba L600 57B has "no battery" option.....

---

