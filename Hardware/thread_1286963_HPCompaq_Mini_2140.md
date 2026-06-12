---
title: "HP/Compaq Mini 2140"
date: 2009-10-09
forum: Hardware
---

### Post by mivo on 2009-10-09
Has anyone successfully installed Ubuntu (any flavour) on a Compaq/HP Mini 2140 netbook? I just picked up one of those. It runs reasonably fast with XP after I spent a few hours removing and disabling stuff (why they always bog down these machines with crap is beyond me), but the temptation to slap Linux on it is great. :) I'm mostly concerned with wireless support, the touchpad and the slightly weird screen resolution (1024x576 instead of 1024x600).

It also doesn't have a DVD/CD drive, so I may have to look into getting an external USB DVD drive or consider an online installation, which is a little tricky with my limited 384k DSL here (about 45k/second, so downloading gigs of stuff is not an option).

Ideally, I'd just want to install Ubuntu and be done with it. Don't currently have the time to really fuzz around with it much, as I had to with both my other laptop and my desktop.

---

### Post by gunjin1 on 2009-10-13
Sort of - I have Ubuntu Netbook Remix running off a 16GB SD card in my HP Mini 2140. Wireless & touchpad worked out of the box for me. I have the model with the HD screen so I didn't noticed any weird display issues. Don't recall any sound or other major issues as well. There is some lag when opening programs, but I attribute that to running off an SD card.

HOWEVER, since I am not a 100% convert (yet) I only log in to UNR occasionally. Last month I did some updates, a reboot, and then tried switching to the normal desktop view as opposed to the default view in UNR. I never rebooted at the time after switching to desktop view until last night when I booted into UNR. I now have the blank desktop issue! 

This has been resolved in [[SIZE="3"]this post[/SIZE]]("http://ubuntuforums.org/showthread.php?t=1225098") I just haven't gotten around to implementing the fix yet. 

Would be interested to know what flavor you end up installing on your Mini and how it goes. That may push me over the fence for a full install on my own :D

---

### Post by RaveJunkie on 2009-10-13
you might not care but I have a dell netbook and it SHIPPED with ubuntu remix on it and it runs great.  I has a 160gig HDD on it atom cpu and 1.5 gig of ram.... 

im debating on putting full ubuntu on it and using ext4 just to see if if can boot faster.....

---

### Post by mivo on 2009-10-14
> **gunjin1 said:**
> Would be interested to know what flavor you end up installing on your Mini and how it goes. That may push me over the fence for a full install on my own :D

I was hoping not to have to be the test subject! :p I love the netbook, especially the keyboard, but I am somewhat afraid of having to spend days on fixing stuff. It works fine with XP now. Not overly fast, but it is a convenient "turn on and it is there" kind of thing.

I think my best option here is to buy a USB DVD drive and fiddle around some. Might end up with Arch Linux (prefer the rolling distro system over the "update every six months and end up reinstalling" approach), but that is something for the Christmas holidays when I am less dependent on a working machine.

Unless you give the full install a whirl!

---

### Post by RaveJunkie on 2009-10-15
I had remix on it and liked it alot just to get online and stuff.  Right now im runing full version but i might go back.  If i had a SS HDD id stay with remix it was good enough and ran fast......

---

### Post by Arjunanda on 2009-10-21
Is you **wired** network working well? Mine does not work at all! I have HP Mini 2140. Also internal microphone does not work, neither does close lid sensor. Also the screensaver will not get locked, and after resume anyone can use the laptop. Everything else is working great.

Yes, I have found the bugsreports and have been looking for workarounds, with no results so far.

---

### Post by RaveJunkie on 2009-10-23
my sensor and network work out of the box.  My netbook will not hibernate or suspend well at all, and if they do its like 2-10 time it will come back...... It boots up so quick i dont really mind just turning on and off.  For network i tried a third party network manager and it didnt work to well so i went back.  I tried   >  Wicd    and it overwrites your default one that i found out was better off.

---

### Post by Arjunanda on 2009-10-24
- Screensaver lock was just disabled in screensaver settings. Enabling it solved the problem
- Network led comes nicely on when cable is plugged, but no network connection is established. dhclient does not help either. Here is my ifconfig with cable plugged:

```

$ ifconfig -a
eth1      Link encap:Ethernet  HWaddr 00:21:00:bf:18:14  
          inet6 addr: fe80::221:ff:febf:1814/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:913036 errors:7 dropped:0 overruns:0 frame:2541731
          TX packets:670372 errors:224 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1131300770 (1.1 GB)  TX bytes:85517686 (85.5 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:70 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6367 (6.3 KB)  TX bytes:6367 (6.3 KB)

pan0      Link encap:Ethernet  HWaddr aa:0d:85:c8:c1:69  
          inet6 addr: fe80::a80d:85ff:fec8:c169/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:2178 (2.1 KB)

```

---

### Post by Arjunanda on 2013-01-14
This is an old thread, but thought to answer anyway - The wired network problem was due to LAN powersave feature being enabled in BIOS - the LAN card gets disabled if the laptop is started on battery power. Disabling the feature in bios solved the problem.

---

