---
title: "HP MIni 100 Wireless not working"
date: 2009-12-26
forum: Hardware
---

### Post by Mouser58907 on 2009-12-26
Hi, I tried following this:
[http://ubuntuforums.org/showthread.php?t=1363752](http://ubuntuforums.org/showthread.php?t=1363752)

but I can't get my hardware manager to find the downloaded drivers. I'm still a pretty big noob at ubuntu but any help would be very appreciated.

Thanks,

Craig Mouser

---

### Post by gordintoronto on 2009-12-27
Unfortunately, the original poster of that thread did not answer any questions.  As well, it is for a slightly different computer than yours.

I suggest you open a terminal session (Accessories/Terminal) and type in the command
lspci
which should display some detail for all the PCI devices, including your wireless adapter.  It should show you the brand and model of the wireless adapter.  Then you can Google it, and with a bit of luck it will bring you to a thread in the forums with a complete answer.

---

### Post by Mouser58907 on 2009-12-27
I'm sorry I mistyped my model number, I have the Mini 110, and the lspci said "Broadcom Corporation BCM4312.. which took me to that same drivers page.

---

### Post by gordintoronto on 2009-12-27
Would you believe that the part you put as ellipses could be important?  Apparently, there's a rev 01 and a rev 02, and they are significantly different.

However... If you come from a Windows background, you might not be aware that many wireless adapters "just work" in Linux, you don't have to download drivers and install them.  Basically, they are built in.

If you have a network icon near the volume-control icon, try right-clicking on it, select "edit connections," open the Wireless tab, click "add" and enter the router's ID, encryption type and password.  And watch it connect.  And if you already knew about that, but there's no network icon on your computer, my apologies.  [smile]

If none of that works, you might want to Google: BCM4312 Ubuntu

One of the places that took me is:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

It is old enough that it might be obsolete.

Another place I found from Google is:
[http://ubuntuforums.org/showthread.php?t=1056446](http://ubuntuforums.org/showthread.php?t=1056446)

---

### Post by Mouser58907 on 2009-12-27
Haha I did not realize it. I have a rev 01. I did know that most wireless drivers work with linux, I was so amazed when I first plugged a linksys usb adapter in and it immediately asked what network I wanted to join. 

It only offers me to join wired networks right now, and they work. My wireless card works in XP, I think it could work  if I could get it to show up in Hardware Drivers, but I don't think I'm doing something right. I extracted it in my Download folder, and I even tried to follow the readme from my initial link to install it and I'm just failing miserably.

Thanks for the help.

---

### Post by Mouser58907 on 2009-12-28
I did the readme again, and upon completion I clicked on the network manager in the corner and it listed both wireless and wired as options! It didn't find any networks however, so I tried restarting. It no longer shows wireless as an option, even if I repeat the readme.

---

### Post by gordintoronto on 2009-12-28
You might need to use ndiswrapper and a Windows driver.  Sorry, I can't help you with details, I've never had to do it.  Google might take you to a message thread with detailed instructions.

---

### Post by redwoodguy on 2009-12-28
I have an HP Mini 110-1134CL. It worked with my wireless network immediately after I installed Ubuntu 9.04. I didn't have to do anything at all. It works on my AIrport network here, and it automatically finds the Starbucks wifi network when I go there too. 

Is there anything I can check on mine (Ubuntu 9.10 now) that would help you with yours?

---

### Post by Ayuthia on 2009-12-28
You might try installing bcmwl-kernel-source from Synaptic or from the Terminal:
```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source
```
It will require internet access so you will need to have a wired connection to make it work.  It is the same application that is usually installed through Hardware Drivers.

---

### Post by Mouser58907 on 2009-12-30
Sorry, I've been ill and haven't been able to work on this. However I stuck my bootable usb in and booted up, accidentally went into the default "Try w/o installing" option. It offered me two drivers for my wireless. I restarted and pulled out my USB and it no longer worked. Is there an easy way to reinstall ubuntu and start over? I have it dual booting with XP now.

---

### Post by Mouser58907 on 2009-12-30
Good news, I reinstalled and I now have wireless working, erm, well sort of. It works, but when I restart I lose it. I just have to run these commands again to get it back though!

```

# rmmod b43
# rmmod ssb
# modprobe lib80211
# insmod wl.ko

```

Then it works again. Obviously this is annoying and I'm not sure what to do but it might have something to do that I get "Permission denied" when trying to run the blacklist commands from the README.TXT
```

# echo "blacklist ssb" >> /etc/modprobe.d/blacklist.conf
# echo "blacklist b43" >> /etc/modprobe.d/blacklist.conf

```
(Even if I put sudo in front of them)
Thoughts?

---

