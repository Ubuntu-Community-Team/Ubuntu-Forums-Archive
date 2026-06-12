---
title: "Custom sleep.sh"
date: 2012-10-06
forum: Hardware
---

### Post by badem4o on 2012-10-06
Hey guys I built myself a nice workstation and it is running great on Ubuntu 12.04 Kernel Linux 3.6.0-030600-generic the only thing is that I can't suspend it. Is there a wiki or any kind of documentation that will guide me in the right direction so I can make this work. Any help will be well appreciated.
Thanks in advance.

---

### Post by funicorn on 2012-10-06
run 

dbus-send --system --print-reply --dest="org.freedesktop.UPower" /org/freedesktop/UPower org.freedesktop.UPower.Suspend

and see what it says

---

### Post by badem4o on 2012-10-06
It does partially suspend. It suspends but the fans and all are still running. Also I have a dual monitor setup and only one of them gets shut off. The second monitor stays on with a black screen. Then it resumes with no problem.
Thanks.

---

### Post by JKyleOKC on 2012-10-06
> **badem4o said:**
> It does partially suspend. It suspends but the fans and all are still running.This makes me wonder if you're aware of the difference between "suspend" and "hibernate." When you suspend, the CPU goes into an almost-asleep mode of operation at reduced power but RAM remains active. Since the machine does not fully power down, the cooling fans are still needed to keep temperatures under control.

If you want complete power-off action, "hibernate" is the mode to use. It dumps all RAM content into the swap partition, then powers the system down. When you turn power back on, early in the boot sequence the CPU looks at the swap partition for the flag that indicates it has been put into hibernation, and when it finds it, simply reloads RAM from the swap partition and brings the system back to life.

Each has its own particular application although both states are so,ewhat similar... Recovering from hibernation takes a bit longer since all the hardware has to be re-initialized just as in a normal "cold boot" but uses no power when down. Recovering from suspension is more like bringing the desktop out of screen-saver mode but isn't so much of a power saver.

---

### Post by ahallubuntu on 2012-10-06
> **JKyleOKC said:**
> This makes me wonder if you're aware of the difference between "suspend" and "hibernate." When you suspend, the CPU goes into an almost-asleep mode of operation at reduced power but RAM remains active. Since the machine does not fully power down, the cooling fans are still needed to keep temperatures under control.

This isn't true with modern hardware.  I have built several Ubuntu desktop systems that I regularly use with suspend, and they do not keep any fans running.  In fact, power consumption is reduced to almost the same level as "OFF" (even when plugged in, a motherboard draws SOME power unless the power supply is turned OFF too or you unplug it).  So almost no heat is generated and no need for extra cooling.

Of course, laptops don't have their cooling fans on during suspend, either.  That would drain the battery pretty quickly.  On some older desktop systems I've used (P4-based), suspend would not shut down the fans, making suspend kind of pointless (the idea was to have the systems be quiet and generate no extra heat, etc.)

And yes, I do know the difference between suspend and hibernation.  Sometimes I use hibernation on my laptop when I know it's going to be off for a while, and I don't want to drain the battery.  But I prefer the nearly "instant on" resume from suspend provides, especially on a desktop when there is almost zero power draw anyway.

---

### Post by badem4o on 2012-10-06
Yes I am aware of the difference between suspend and hibernate. How would you then explain one of the monitors not powering down?
Nevertheless any suggestions on how to make a custom sleep.sh that will properly put my machine to sleep?
Thanks

---

### Post by ahallubuntu on 2012-10-06
Suspend is one of those things that sometimes doesn't work in Linux out of the box.  It depends how well the hardware is supported by the kernel.  Please post more information about your hardware (try "sudo lshw") - more information about your motherboard's chipset might help track down a work-around.

---

### Post by badem4o on 2012-10-06
Hey ahallubuntu. Here is a link to the output.

[http://dl.dropbox.com/u/50454683/badem4o_system_info.html](http://dl.dropbox.com/u/50454683/badem4o_system_info.html)

Thanks for the help!

---

### Post by ahallubuntu on 2012-10-06
Sorry, that dropbox link 403's - can you try again?

I probably can't offer you any direct solution - but you can look for one yourself.  Find the name/model of the chipset and do some creative googling and see if people have suggestions for tweaks to allow suspend/resume to work correctly. You probably aren't the first one to have encountered such problems with it.

---

### Post by badem4o on 2012-10-06
Ooops sorry. I fixed it. If anyone can help that would be great. I have been googling all day with no luck so any help would be appreciated.

---

### Post by ahallubuntu on 2012-10-07
Did you see this one?  I think it may be relevant to your chipset, not sure:

[http://crunchbanglinux.org/forums/topic/19427/hibernatesuspend-solved/](http://crunchbanglinux.org/forums/topic/19427/hibernatesuspend-solved/)

Start with post #20 in the thread - that may give you enough to make it work in Ubuntu...

---

### Post by badem4o on 2012-10-07
I still don't have a fix for this. I found a ton of scripts written by people all over the place on google but none of them work for me. Can anyone point me to a resource that will explain how to write my own script.
Thanks.

---

### Post by funicorn on 2012-10-19
When it comes to linux kernel power management, there is little you can do. If you are to stick on this, try the 'dbus' suspend command line again, then wake it up and look into the log files /var/log/{pm-suspend.log,syslog,kern.log, dmesg,udev}. There is no anticipated  pattern of error report, you can focus on the lines started by (EE) though.

---

### Post by Mars73 on 2013-01-13
> **funicorn said:**
> run 

dbus-send --system --print-reply --dest="org.freedesktop.UPower" /org/freedesktop/UPower org.freedesktop.UPower.Suspend

and see what it says

Ah great, it's working fine for me.
Gnome 3/shell suspend wasn't working for me.
I made a launcher with this command in it and it goes to sleep perfectly.

---

