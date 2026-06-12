---
title: "PCMCIA Networkcard not working on 6.06LTS"
date: 2006-08-17
forum: Hardware &amp; Laptops
---

### Post by OZendel on 2006-08-17
Hi there,
I am trying to get my PCMCIA Networkcard 3M Megahertz 3CCFEM556BI working with Ubuntu 6.06 on my Thinkpad 600E. After installing Ubuntu with the alternate installation CD the network card was not active (it's status LEDs were inactiv). I found this hint:

# Add the following to your kernel options in /boot/grub/menu.lst:
acpi=force pci=noacpi

at [http://www.mueller.ch.vu/misc/tp600e_en.html](http://www.mueller.ch.vu/misc/tp600e_en.html) but this changed nothing.
After that I found [http://lkml.org/lkml/2006/8/4/166](http://lkml.org/lkml/2006/8/4/166) and copied
/etc/pcmcia/cis/3CCFEM556.dat to /lib/firmware/3CXEM556.cis
and added a script to init.d with a content like this:

pccardctl eject
pccardctl insert

Now the card's LED for 100Mbit networking is lit after startup. Even after manually removing and reinserting the card, it's LED becomes lit again. Nevertheless I can't get a connection to my network. Please help me getting it to work.

Sincerly Oliver Zendel

---

### Post by HerbAlpert on 2006-10-22
Hi

I have the same card on an older Dell Latitude and it wasn't working for me either. Ubuntu 6.06LTS.

I have been pulling my hair on this problem since yesterday and I think I've got something you can try:
Add the command cardmgr before your pccardctl-commands in your startupscript. That did the trick for me!

Try even shutting off ipv6:
[http://www.ubuntuforums.org/showthread.php?t=87798]("http://www.ubuntuforums.org/showthread.php?t=87798")
This is not only for speeding up - on some systems it can actually create problems with dhcp, according to some posts i have read.

---

### Post by yman on 2006-10-23
> **HerbAlpert said:**
> Hi

I have the same card on an older Dell Latitude and it wasn't working for me either. Ubuntu 6.06LTS.

I have been pulling my hair on this problem since yesterday and I think I've got something you can try:
Add the command cardmgr before your pccardctl-commands in your startupscript. That did the trick for me!

Try even shutting off ipv6:
[http://www.ubuntuforums.org/showthread.php?t=87798]("http://www.ubuntuforums.org/showthread.php?t=87798")
This is not only for speeding up - on some systems it can actually create problems with dhcp, according to some posts i have read.

can you please be more specific? where is this startupscript?

---

### Post by yman on 2006-10-23
I went [here]("http://lkml.org/lkml/2006/8/4/166") and did this:
```

$ cd /lib/firmware
$ pccardctl insert 1

```
then I took out my PC card.
```

$ sudo cardmgr

```
then I put the card back in.
I don't know if the problem was resolved then, because I only looked after writing this as root:
```

$ pccardctl insert 1

```
then I looked and saw the light was on, so I went to google, and it worked!
just so you know, I connected to the internet through a windows desktop.

for the first time I'm going to enjoy synaptic! It's been a real pain downloading on windows and then bringing it to ubuntu just to discover I'm missing a dependancy - dependency hell is what what they call it, right? suitable term in my opinion.

good luck to you. I really hope you find a way to do this for your machines. if I come up with something, I'll be sure to keep you posted.

you can get windows drivers at 3com and install them with wine, but it's a wast of time - it won't work.


[CENTER]:-D  :-D  :-D [/CENTER]

EDIT: after installing 187 updates, the fix I made was somehow cancelled but that was no problem since I only had to repeat the above steps to fix it again. I also learned that I don't need to write that last line after reinserting the PC card.

but maybe it was rebooting that ruined the fix, I'll have to check.


EDIT:
here are some before and after screenshots:

not working:
[IMG]http://www.orangejew.com/ubuntu/pccard/Screenshot-ConnectionPropertieslo.png[/IMG]

working:
[IMG]http://www.orangejew.com/ubuntu/pccard/Screenshot-ConnectionPropertieseth0.png[/IMG]

not working:
[IMG]http://www.orangejew.com/ubuntu/pccard/Screenshot-Networksettings-1.png[/IMG]

working:
[IMG]http://www.orangejew.com/ubuntu/pccard/Screenshot-Networksettings.png[/IMG]

I hope you can make use of this stuff.

---

### Post by OZendel on 2007-01-05
Hi,
thank you for your advices. 
1. I turned off IPv6 -> no effect
2. I added cardmgr before the pccardctl in the init-script -> scary effect, now the system beeps 3 times in different chimes on startup and shutdown, network is still not working
3. pccardctl insert 1, then cardmgr -> no effect

Something interesting I noticed:
My Network Settings are like yman's "working", but my Connection Properties are like yman's "not working".

Sincerly Oliver Zendel

---

### Post by yman on 2007-05-09
I recently updated to 7.04 and the problem seems to be worse. somehow I discovered that the following procedure works for me:
1. in the terminal: $sudo cardmgr
2. completely remove pcmciautils.
3. install pcmciautils.
4. hibernate.
5. turn on the computer.

In order to remain connected I must never shut down or restart, only hibernate (and probably suspend, but I didn't try it yet). also, weird bad things happen if I do this, disconnect the cable, and try to hibernate. so I must remember to always hibernate while I have an internet connection.

I don't think theres a reason it won't work in earlier versions of ubuntu.

NOTE: I really used pcmcia-cs (installed it, then completely removed it with pcmciautils, then installed it with pcmciautils), but I don't think that should make a difference.
NOTE: I am using the OEM installation, as OEM.

EDIT: I can only hibernate twice in a row, once to get the internet working and then once more, but after that hibernating gets stuck in the middle so I have to shut down. It's still worth it, though, and I've been playing lots of Super Tux.

---

