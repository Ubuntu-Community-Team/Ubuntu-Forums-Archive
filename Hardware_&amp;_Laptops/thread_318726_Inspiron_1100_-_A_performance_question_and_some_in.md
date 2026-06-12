---
title: "Inspiron 1100 - A performance question and some installation tips"
date: 2006-12-14
forum: Hardware &amp; Laptops
---

### Post by earth_walker on 2006-12-14
Hi all,

**First, my question:**

I installed Edgy on my wife's Inspiron 1100, which previously had Dapper on it. In general the performance is better and seems more stable. 

However, she has been finding that when she has two OO documents and a couple of Firefox tabs at the same time, performance grinds to a halt - task switching, tab switching, menus, etc. I have confirmed that it happens, but haven't had a chance to check memory use or dmesgs, etc. yet.  But before you say 'install more RAM', I have to add that although dapper was slower in general, it was consistently useable, and this particular grind-to-a-halt behaviour was not seen even with many OO documents and FF pages open. 

Has anyone else seen this? Is it a OO2.04 or FF2 memory leak or bug? Any comments or hints? I'm going to look at it tonight, but I can't think of what I may be able to do to fix it.

**Tips for installing Edgy on a dell inspiron 1100:**

1. Before doing anything, update your bios to at least version A29. The Dell site has instructions and files.

2. Use the 'Alternate Installation CD'. The liveCD does not work well with this laptop.

3. When you log in for the first time, your screen resolution will probably be stuck at 640x480 or something. Don't worry. As long as you updated the bios, all you need to do is change some lines in the video configuration file. 

First, make a backup of your existing xorg.conf file:

```
cp /etc/xorg.conf /etc/xorg.conf.bak
```

Now open the file for editing:

```
sudo gedit /etc/xorg.conf
```

Add horizontal and vertical refresh values in the 'monitor' section such as:

        HorizSync	31.5-48.5
	VertRefresh	59-75

and change the DefaultDepth value in the 'screen' section to 24. 

There's an example xorg.conf file at:

[http://www.geocities.com/randomnumbergenerator2001/xorg.conf.breezy.txt](http://www.geocities.com/randomnumbergenerator2001/xorg.conf.breezy.txt)

When you are done changing that, save and close, and reboot. 

**Tip for using DLink PCMCIA wireless card on Edgy:**

It took ALOT of sifting through garbage to find the answer to this one.

While my Dlink card worked out-of-the-box on dapper, some kind of political game has left the atheros wireless modules out of the normal edgy, but they are included in the repositories. YOU DO NOT NEED NDISWRAPPER!

1. Use synaptic to find and install an appropriate linux-restricted-modules package. If you're unsure, you're probably looking for the 'generic' one. If you cannot find these, look for help on enabling extra repositories.

2. Reboot when you are finished with the wireless card plugged in. 

3. Follow the Ubuntu help file on enabling networks. YOU DO NOT NEED NDISWRAPPER! I also recommend installing network-manager for laptops, which allows you to easily switch between wired and wireless networks (like windows xp does but buggy in different ways).

---

### Post by adaptr on 2006-12-14
Even trying to guess at what causes the slowdown is useless without investigating memory usage **first**.
I find FF2 to be much less leaky than 1.5, so I doubt that is the problem.

---

### Post by rbp1976 on 2006-12-20
Thanks earth_walker, worked like a champ on Dell 1100 with A32 BIOS.

---

