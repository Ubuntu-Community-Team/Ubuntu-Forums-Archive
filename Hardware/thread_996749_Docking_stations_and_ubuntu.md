---
title: "Docking stations and ubuntu"
date: 2008-11-29
forum: Hardware
---

### Post by rapattack1 on 2008-11-29
Hi I am thinking of bidding on a docking station on ebay and just wanting to know how Ubuntu handles them. I have a Dell Inspiron 7500 notebook and this is the listing [http://cgi.ebay.com.au/ws/eBayISAPI.dll?ViewItem&rd=1&item=230310573347&ssPageName=STRK:MEWA:VRI](http://cgi.ebay.com.au/ws/eBayISAPI.dll?ViewItem&rd=1&item=230310573347&ssPageName=STRK:MEWA:VRI)
if you have to be logged into ebay to get to this url and you are not a member the item number is  230310573347. I would like the dvd drive in the listing too as I have often burn my data on the desktop on a dvd otherwise I take whatever it is to the notebook via a usb drive. I have had my machines networked but I killed my router. Wrong power supply. Ah well.
Would appreciate peoples opinion or links that show info on how Linux or Ubuntu handles docking stations.

---

### Post by frogotronic on 2008-12-04
Hi,

  Looks as though Ubuntu & Fedora handle docking stations well - but you have to use the restricted drivers.

[http://forums.fedoraforum.org/showthread.php?t=201555](http://forums.fedoraforum.org/showthread.php?t=201555)

[http://www.linlap.com/wiki/HP+EliteBook+8530W](http://www.linlap.com/wiki/HP+EliteBook+8530W)

- CH

):P

---

### Post by rapattack1 on 2008-12-05
Ah ok yes I have seen a restricted drivers thing pop up a couple of times in two different desktops I have had ubuntu installed on when I put a different graphics card in. So I had to install it after thing notification popped up to do so.
What were those links about? To say that it is possible to use linux and docking stations together?
I have never used a docking station so it is all new to me. I ended up buying the docking station yesterday anyway before I got your reply. Thanks!!!

---

### Post by frogotronic on 2008-12-05
> **rapattack1 said:**
> Ah ok yes I have seen a restricted drivers thing pop up a couple of times in two different desktops I have had ubuntu installed on when I put a different graphics card in. So I had to install it after thing notification popped up to do so.
What were those links about? To say that it is possible to use linux and docking stations together?
I have never used a docking station so it is all new to me. I ended up buying the docking station yesterday anyway before I got your reply. Thanks!!!

Hello,

Yes, it looks as though most docking stations and Ubuntu are compatible.

The RESTRICTED DRIVERS notification tells you that if you want to get the most out of your video card (ATI or nVIDIA), you should install the driver.  (BTW: It's not free, nor open source, so you can't file a bug report with Ubuntu).

It appears that docking stations are pretty much fully supported in the newer kernels, thus making the issue non distro-specific.  You may have to fiddle with your xorg.conf file - if you have trouble, post back here and we'll get you sorted.

I just bought a docking station myself for an HP6910p.  Will post back here when I have the results after it arrives.

- CH

---

### Post by rapattack1 on 2008-12-05
Yes i got that notification after putting in nvidia video cards. On one machine it made things worse and I had to uninstall it but on the other it works.
I haven't quite got the hang of bug reports so will have to ask more about that next time the issue comes up.
Ah ok I didn't know that the thing was dependant on the kernel. Still learning so much about linux. Yes I will ask more when I get my docking station as I think I have only edited that file once on a machine a while back and I stuffed things up.

Ah so your getting a docking station too. Ok would love to hear what happens! Thanks!!!

---

### Post by frogotronic on 2009-01-06
Okay,  Got the HP Docking station.  VGA, sound out, ethernet work, I suspect the other stuff does.

One thing that does not work are the USB hubs.

Will investigate.

- CH  :popcorn:

---

### Post by rapattack1 on 2009-01-06
Yeah I am going through some tests right now as I am reinstalling windows and Dream Linux to see what happens with the docking station. I think Ubuntu is just too heavy for it now. It slowed down too much and DL is much lighter. Ah well I guess i can't post the results here now as I am not using Ubuntu. I have installed DL on my main box too and will post stuff on the DL forum now. :popcorn:

---

### Post by frogotronic on 2009-01-08
Okay, got the docking station USB ports working.

```
$sudo gedit /etc/initramfs-tools/modules
```

Add the following to the modules file

dock
uhci_hcd
ohci_hcd
ehci_hcd

Save & close the file.

```
$sudo update-initramfs -u
```

Reboot.  When rebooting I have to have a mouse connected to one of the docking station USB ports.  Then all is well.

- CH   :D

---

### Post by rapattack1 on 2009-01-08
Gee i wish I had of known this earlier but I have to hand the laptop over to it's new owner tomorrow so I have run out of time. Plus I have to go to bed now. Ah well it is all experience! I hope that next time this happens I can refer to this forum. There are so many pc's coming through my hands as I am the ameteur techie nerd in my area. Plus a friend is sending a whole lot of old pc's to Africa(Senegal) so I get to test out some different distro's on them before they go.
Thanks heaps cement_head!:D

---

### Post by frogotronic on 2009-01-09
**WORKAROUND CAN BE FOUND HERE:** [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/314734](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/314734)

---

