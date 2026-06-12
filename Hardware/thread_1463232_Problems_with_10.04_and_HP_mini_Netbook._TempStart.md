---
title: "Problems with 10.04 and HP mini Netbook. Temp/Startup/Batt."
date: 2010-04-26
forum: Hardware
---

### Post by tjeremiah on 2010-04-26
I've decided just recently to upgrade my mother's netbook which right now turns out to have been a bad idea :( . In the past she had XP and about 2 months ago I decided to get rid of it for Karmic Netbook Edition. The results were great and everything ran smooth. 

What I liked about Karmic on her HP mini Netbook was how fast everything started up. No details in "text" (sorry, dont know the proper term) like "Battery full power" or "kill app." or whatever details that would usually show when starting up on the Desktop edition of Ubuntu. 

With this anyway, I decided to update to 10.04 and was curious to see how it performs on a Netbook :P. Here is one problem i've noticed right off the bat. [COLOR="Red"]**(UBUNTU NETBOOK EDITION) **[/COLOR]

**_Problems_**

When starting up, I would get a warning in text saying : "Critical temperature reached (85C), Shutting down." While receiving this warning, the Netbook never shutsdown but continues on with its business. How do I correct this warning and remove it from reappearing again? Its clearly not running hot but cool. 

The second problem is the "text" after booting. While it bypasses the selection of a Kernel unlike the Desktop Edition, the screen still displays messages of other items loading. How can I remove the "text" on startup? Also, I havent noticed any X-Splash or Plymouth ( I believe thats the proper wording for the loading screen).

Lastly is the battery problem. When removing the AC cord from the Netbook, the battery indicator on the panel turns red warning me that I have 5% of battery power left. That clearly isnt the case and is wrong. 

Overall, the performance is a bit sluggish from Karmic on this Hp Mini Netbook but yeah, 2 more days of updates to go :guitar:

---

### Post by tjeremiah on 2010-04-26
can anyone help :( ?

---

### Post by go7Ul1ai on 2010-04-26
I am having some of the issues discussed here on my girlfriends HP Mini also. I'm just going to stick with Karmic UNR until Lucid+1 RC is out.

---

### Post by tjeremiah on 2010-04-26
> **lee.jarratt said:**
> I am having some of the issues discussed here on my girlfriends HP Mini also. I'm just going to stick with Karmic UNR until Lucid+1 RC is out.
RC is out :( This is the version I installed on Mini just now. Also along with the 10.04 it was the UNE of course, not desktop.

---

### Post by ljrmorgan on 2010-04-26
I have am HP mini 210 and have not yet put Lucid on, running windows 7 for now - what HP mini is it? 110/210/311/...??

---

### Post by tjeremiah on 2010-04-26
> **ljrmorgan said:**
> I have am HP mini 210 and have not yet put Lucid on, running windows 7 for now - what HP mini is it? 110/210/311/...??

/i was looking for a model number but couldnt find it :(

EDIT  fount it. Its 1010NR

---

### Post by go7Ul1ai on 2010-04-26
> **tjeremiah said:**
> RC is out :( This is the version I installed on Mini just now. Also along with the 10.04 it was the UNE of course, not desktop.

I said I will stick it out with Karmic UNR until **Lucid+1 RC** is out. Meaning the RC of the next development version (in around 6 months time). ^_^

---

### Post by ljrmorgan on 2010-04-26
Part of the reason I asked is that many netbooks are basically the same but put together and branded my different companies - you might find others with similar problems on different netbooks.

I found a couple of bugs that might be similar to your battery problem, hopefully a fix will be released soon:
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/558627](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/558627)
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/516023](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/516023)

I wouldn't worry too much about plymouth not showing up - that might be because of your temperature error. I don't know how it works at all, but I wouldn't be surprised if, after getting a message about running too hot, the loading screen just stuck to printing out diagnostic text (purely conjecture, as I said, not sure how it works).

As for the temperature thing itself, I saw [this]("http://ubuntuforums.org/showthread.php?t=1459927") thread, might be relevant. I quickly searched all the forums (not just the Lucid forum) for "Critical temperature reached" and loads of results came up - something there might be useful. Hope that helps, good luck!

---

### Post by tjeremiah on 2010-04-26
> **ljrmorgan said:**
> Part of the reason I asked is that many netbooks are basically the same but put together and branded my different companies - you might find others with similar problems on different netbooks.

I found a couple of bugs that might be similar to your battery problem, hopefully a fix will be released soon:
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/558627](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/558627)
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/516023](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/516023)

I wouldn't worry too much about plymouth not showing up - that might be because of your temperature error. I don't know how it works at all, but I wouldn't be surprised if, after getting a message about running too hot, the loading screen just stuck to printing out diagnostic text (purely conjecture, as I said, not sure how it works).

As for the temperature thing itself, I saw [this]("http://ubuntuforums.org/showthread.php?t=1459927") thread, might be relevant. I quickly searched all the forums (not just the Lucid forum) for "Critical temperature reached" and loads of results came up - something there might be useful. Hope that helps, good luck!
thanks a lot :)

---

### Post by tjeremiah on 2010-04-27
Bump :(

---

### Post by tjeremiah on 2010-04-28
alright, the problem is obviously with the newer kernel. Going back to KERNEL 2.6.31-20 fix all of the problems. BUT with this kernel, going back to it, Lucid mentioned that I was not mounting a drive when booting and also wireless was not working, so i went back to 2.6.32-21 that installed when i upgraded to Lucid. I guess ill have to wait for a newer kernel to be installed via update manager that can help solve this problem.

---

### Post by cariboo on 2010-04-28
I'm posting this from my Compaq Mini 110, I just ran sensors-detect to set up lm-sensors properly, this is the output when I run **sensors**:

```
sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +48.0°C  (crit = +100.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +26.0°C  (crit = +90.0°C)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +26.0°C  (crit = +90.0°C)
```

This is the kernel I'm running:

```
uname -a
Linux redstone 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
```

Everything runs as it should otherwise, the state of the battery is shown correctly, I had to use a network cable to download the restricted Broadcom drivers for wifi. The built in web cam and microphone worked out of the box. Except for the sensors tweak I just did, the install is bone stock.

---

### Post by tjeremiah on 2010-04-28
When running sensors I get 

```
acpitz-virtual-0
Adapter: Virtual device
temp1:       +43.0°C  (crit = +39.0°C)        
```

And like I mentioned above, I went back to the orginal kernel that upgraded with Lucid after previously uninstalling it

```
Linux -laptop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linu
```

After I went back to this kernel I had to do what you did, install Broadcom and web and mic works without having to look for a solution. Still there is a problem with the batter app. when disconnecting AC plug and the warning message in the beginning of booting (I read your other reply in the other thread)

---

### Post by gtr@frii.com on 2010-04-28
I ran beta2 from flash without problems on an HP 210-1010NR, however, I was not able to get the rc to run.  It starts boot and then pops up a message to remove disks or other media and reboot.  This was built using unetbootin from windows 7, exactly the way I built the beta2 version which worked.  What am I missing here, and is there some kind of init script that I can tweak if I look at the flash from my desktop 9.10 machine/

---

### Post by tjeremiah on 2010-04-28
> **gtr@frii.com said:**
> I ran beta2 from flash without problems on an HP 210-1010NR, however, I was not able to get the rc to run.  It starts boot and then pops up a message to remove disks or other media and reboot.  This was built using unetbootin from windows 7, exactly the way I built the beta2 version which worked.  What am I missing here, and is there some kind of init script that I can tweak if I look at the flash from my desktop 9.10 machine/

Not sure if im understanding your question correctly but ill continue anyway. The way I did was from in 9.10, I pressed ALT+F2 and typed update-manager -d. This how I managed to get it to download.

---

### Post by gtr@frii.com on 2010-04-28
I can probably use update -d on any of my desktop ubuntu machines.  The problem was trying to test the netbook remix on a netbook which is running Windows 7. (This netbook has uefi instead of bios and the 160GB disc is guid partitioned, so I am hesitant to actually install to it until the final release comes out -- tomorrow). I'll go ahead and boot 10.04 from a cd on a desktop and then install the rc to flash there and see if that will work on my netbook.  What didn't work on my netbook was a copy of the 10.04netbookrc iso installed from windows 7 using unetbootin.exe (attempted boot from that flash yielded the 'remove disk...' error message and no way to proceed).

I booted 10.04rc from a cd iso on one of my desktops and created the flash from there using startup disk creator.  The netbook boots fine with it.  I'll try unetbootin to create  a flash from windows after the real release comes out.  For what it's worth, the usb-creator.exe file on the rc iso still doesn't work in Windows - you can't select source or destination.

---

### Post by bapoumba on 2010-04-29
Moved to Hardware & laptops.

---

### Post by Chris-Chicken on 2010-05-03
Hi all, I'm having the same issues with 10.04 NBR on my HP Mini 1030NR :(

The battery shows as discharging from around 5%.... which isn't accurate. The computer will suspend even though the battery is full.  I also get the Critical warning temperature messgae when booting up. 

I also had to download the Broadcom drivers from a cable connection, which I haven't needed to do before.


```
sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +48.0°C  (crit = +31.0°C)    

uname -a
Linux SylvanManko 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux


```


Do we know if the same issues affect the standard edition? I can't use my computer without a battery! 

:D

---

### Post by Chris-Chicken on 2010-05-04
-update- 

I've found that disconnecting the battery for a few seconds, and then turning the laptop back on causes the 'Critical Temp. Reached' message to not display.

Once on, the laptop just reports the battery as 'charged', and also displays the on AC symbol. The screen is at full display brightness, even though it's set to reduced when on battery power.

So, I suppose this suggests that it's an issue with connecting and disconnecting the charger......

With this work around, I can use the laptop for the full battery discharge, but it will drain the battery to 0%..... there's no monitoring going on.

I think that the problem reappears at some stage, not sure at the moment if it's when the charger is reconnected.

---

### Post by Chris-Chicken on 2010-05-27
Bumpedy bump.....

Does anyone know if it's worth installing Desktop Edition? The battery issue is very annoying.

---

### Post by axxter on 2010-05-31
I have the HP 110-1030NR with 10.04 Desktop running on it.
I don't have issues with the temperature, startup, or battery life/monitoring.
The only issue I have is the internal mic doesn't work with Skype (or anything else, for that matter). 
However, it works just fine with my Logitec USB headphones/mic.

Hope this helps.

---

### Post by Chris-Chicken on 2010-05-31
Thanks Axxter. :)

I had mic issues with older dists.

I solved them by either:

1. Switching the device (in the sounds properties menu) to 'Line'

or

2. Using the ALSA system, and recompiling the driver. There are instructions for doing this somewhere in [here]("http://ubuntuforums.org/showthread.php?t=1196019").

Though, I suspect that this isn't necessary, as it's in the current kernel already.

:D

---

