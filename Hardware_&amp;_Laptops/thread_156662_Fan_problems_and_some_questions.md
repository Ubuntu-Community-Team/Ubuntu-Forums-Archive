---
title: "Fan problems and some questions"
date: 2006-04-07
forum: Hardware &amp; Laptops
---

### Post by starfire1983 on 2006-04-07
I'm using a Gateway 7322GZ laptop. I have everything working and configured properly, but one thing still bothers me.

While in Ubuntu (using Breezy) the fan never turns off and runs continuously at the same rate. I've disabled apmd, I've even tried turning off SpeedStep to see if that would help and it didn't. I'm dual booting w/ XP Pro and my fan is never on very long.

The laptop's specs:

Mobile Pentium 4 @ 2.8GHz
768MB of memory (32 shared for video)
Intel 852/855 chipset
Broadcom Wireless 54g (working fine through ndiswrapper and Network Manager/GTKWifi)

So, my questions are 1) how would I get the power management or whatever to scale down the cpu so the fan isn't on all the time (literally)? 2) How do I disable the synaptics touchpad (I hate it and don't ever use it)? 3) And how do I make it so during boot up that it doesn't automatically try to configure eth0 since I'm on wireless? This is causing my bootup to take in excess of 2min.

---

### Post by whoa_551 on 2006-04-07
I am a major newbie, so take my advice (for what it's worth) very carefully.

#1) A very common problem in Linux.  There are alot of threads on this subject, and if you take the time to go through them (it will take awhile), you might find what you are looking for.  I know there is something called powernowd that Ubuntu uses to help regulate cpu clock speed.  I don't know if your fan problem is related to your cpu running too high-too often, but you may want to see if you have powernowd installed, and if it's working properly.  The command ```
cat /proc/cpuinfo
``` in a terminal window might (?) help give you some info in this regard.  As far as reconfiguring at which cpu-intensity level the fan kicks on at, as far as I know, some people have figured out a way to do it, but my impression is that it is complicated and risky.
#2) My personal guess is that the synaptics touchpad is probably turn-offable ;) in the /etc/xorg.conf file.  I can link you to a Slackware thread that talks about this a little, if you are willing to tool with your xorg.conf.  [http://www.linuxquestions.org/questions/showthread.php?t=368082]("http://www.linuxquestions.org/questions/showthread.php?t=368082")
#3) I have no idea.  Sorry.

---

### Post by starfire1983 on 2006-04-07
1) I have powernowd installed and running fine, afaik.
2) I've already tried to turn off the touchpad in the xorg.conf, no go.

---

### Post by teeb on 2006-04-08
#3 [http://www.ubuntuforums.org/showthread.php?t=143095](http://www.ubuntuforums.org/showthread.php?t=143095)
may help.

---

### Post by starfire1983 on 2006-04-08
The touchpad link did work, I thought it didn't but I had something commented out  that I needed.

Also, my laptop is constantly running between 64-66C and the fan is always on. I'm running the SMP kernel since the CPU supports HyerThreading. The power preferences say cpu scaling hasn't been implemented or something and it seemingly doesn't work. I don't think this is an immediate threat to my computer's life but with the recent crap out of my XP install (decided to BSOD while I was sleeping and won't run for long anymore), I need to find a solution to this problem. CPU usage is usually up at around 15-30% on average, as well.

---

