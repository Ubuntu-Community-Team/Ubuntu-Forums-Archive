---
title: "[SOLVED] Internet slowdown"
date: 2008-08-14
forum: General Help
---

### Post by Farajamo on 2008-08-14
I recently transferred from Windows XP to Ubuntu, and one of the first things I noticed is a major slowdown regarding the internet. My pages in firefox loaded much faster in windows, and using Transmission only gets me about 60 kb/s whereas when I used uTorrent I usually got around 200 kb/s.  Does anyone know why this is occurring? Thanks.

---

### Post by pytheas22 on 2008-08-14
It's probably a problem with your driver.  Please post the output of:
```

lshw -C Network
```

and maybe we can find a better driver for you to use.  Also, are you connected wirelessly or via ethernet?

---

### Post by Farajamo on 2008-08-14
I'm connected directly (ethernet).

That command gets me:

user@user-desktop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 00
       serial: 00:d0:c9:a6:ce:c0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=0.5-7 ip=192.168.1.136 latency=0 module=e1000 multicast=yes

---

### Post by pytheas22 on 2008-08-14
I think [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/42572") is the culprit.  It seems to have existed since 2006, but is still reported as an issue in Hardy as of May.

Someone in the bug report says that recompiling an older version of the e1000 ethernet driver from [http://sourceforge.net/project/showfiles.php?group_id=42302](http://sourceforge.net/project/showfiles.php?group_id=42302) solved it.  Another person says that "disabling ASPM in the network driver" fixes it...I don't know what that means (and the link to the suse forums provided in the bug report seems to be dead) but can try to research it more later.

I have to go now, but hopefully this will lead you somewhere.  If it doesn't help or you don't understand how to recompile the driver, et cetera, it's ok; I'll walk you through it when I'm back tomorrow.

---

### Post by Farajamo on 2008-08-14
Heh, I'll see you then... I'm very unfamiliar with Linux..

---

### Post by pytheas22 on 2008-08-15
Alright, try running these commands to compile version 7.6.15.4 of the e1000 driver, which according to that bug report solves the problem:
```

sudo apt-get install build-essential
wget http://downloads.sourceforge.net/e1000/e1000-7.6.15.4.tar.gz?modtime=1202774686&big_mirror=0
tar -xzvf e1000-7.6.15.4.tar.gz
cd e1000-7.6.15.4/src/
make
sudo make install
```

After that, reboot and see if you have better luck.  Please let me know how it goes.  I'm not sure whether this will fix the problem--I'm just going off of what some guy says helped him--but if this doesn't work, there are other things to try.

---

### Post by Farajamo on 2008-08-15
Heh, funny story.  I can't apt-get, synaptic, or add/remove because of another problem I have.

You can see it at [http://ubuntuforums.org/showthread.php?p=5591327#](http://ubuntuforums.org/showthread.php?p=5591327#)

---

### Post by Farajamo on 2008-08-15
At the end of installing it, I got:

cannot write to /var/cache/man/cat7/e1000.7.gz in catman mode
e1000.

Does that mean the installation failed?

---

### Post by pytheas22 on 2008-08-15
> At the end of installing it, I got:

cannot write to /var/cache/man/cat7/e1000.7.gz in catman mode
e1000.

Does that mean the installation failed? 

Yeah, it sounds like a problem with permissions.  Please try running this:
```

sudo -s
rm -rf e1000*
wget http://downloads.sourceforge.net/e1000/e1000-7.6.15.4.tar.gz?modtime=1202774686&big_mirror=0
tar -xzvf e1000-7.6.15.4.tar.gz
cd e1000-7.6.15.4/src/
make
make install
```

I think that should make it install correctly.

I'll take a look at your other thread too.

---

### Post by Farajamo on 2008-08-15
Don't worry about the other thread, someone helped me with it.

---

### Post by Farajamo on 2008-08-15
I got the same error again

---

### Post by jerome1232 on 2008-08-15
Just curious (becuase this solution is simple to try) but have you tried using openDNS. When using Ubuntu using my old providers DNS servers internet went Very, Very, slow (but windows was fine). Soon as I switched to OpenDNS it was remedied.

To try it edit /etc/resolv.conf comment out whats in there (so it's easy to restore) and put in openDNS servers, now try and surf around to a few pages, then try 'em again see if it starts clearing up.

I like vim as a text editor so I'll run through with that (you can use gedit if you want to.)
```
sudo vim /etc/resolv.conf
```

Now press "i" to get into --insert-- mode, hit down a few times stick a "#" sign infront of anything that isn't commented
start a new line and make it look like this
nameserver 208.67.222.222
nameserver 208.67.220.220
now press esc, then shift+ZZ it'll save.
Try surfing around see if it fixes the slowness.

---

### Post by pytheas22 on 2008-08-15
Actually I think that that error message may not matter, as I installed the driver on my system and it still seems to have replaced the original e1000 module without a problem.  To check whether yours did the same, type:
```

modinfo e1000 | grep version
```

If should return the version number; if it's "7.6.15.4-NAPI," then the driver installation worked and you can reboot, and hopefully your Internet will be faster.  If not, we can try some other things.

---

### Post by Farajamo on 2008-08-15
Okay, I successfully changed to open DNS, and I have the new version.  As far as navigating through a site (e.g. opening info in wikipedia, going through new threads in the Ubuntu forum) but as far as first entering a site, it's not too much of an improvement (but there is one).  I suppose I will get more definite results after more use of the interwebs.

---

### Post by jerome1232 on 2008-08-15
Well if you do want to keep OpenDNS you'll have to change that in your router, those changes I had you do will get clobbered when you reboot.

---

### Post by Farajamo on 2008-08-15
In Windows I was able to change to open DNS in my network properties... Ubuntu doesn't have something similar?

---

### Post by jerome1232 on 2008-08-15
Now that you mention it, it does.

click on network manager, hit unlock, click on the DNS tab, and manually enter the OpenDNS servers.

---

### Post by Farajamo on 2008-08-16
I just did that in Network and my internet sped up really fast.  Thanks, man.

---

