---
title: "Installing Ubuntu 8.1 on Asus A8V-VM freezes on login"
date: 2009-01-21
forum: Hardware
---

### Post by Magic30 on 2009-01-21
I'm using the Asus A8V-VM with 1,5 GB RAM. GFX, network card, and sound are onboard. The Ubuntu 8.1 install runs fine, but after booting, right when showing the (gnome) login textfield, the whole system freezes.

I installed Ubuntu server 8.04 earlier on that PC and textmode boots and works just fine.

I tried adding pci=nomsi noapic nolapic to the kernel's boot parameters but that didn't help.

Any ideas?

---

### Post by utnubuuser on 2009-01-21
Can you get in through rescue at the grub/boot screen?
If yes, try: sudo dpkg --configure -a

Might be a simple configuration issue.

---

### Post by dabl on 2009-01-21
Two more notions to toss on the pile:

1. Try a "xforcevesa" boot option

2. Shut down GDM (choose "command line" boot, or "Recovery Console") then issue

```
sudo /etc/init.d/gdm stop
```

and then issue

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and then 
```

startx
```

---

### Post by Magic30 on 2009-01-21
I tried all the above mentioned things, but that didn't solve the problem.

I deactivated the onboard sound, because I read, that it caused problems for other people, but no luck with that either.

Are there any interesting logfiles I should take a look at?

---

### Post by dabl on 2009-01-22
What is that onboard graphics chip?

I don't know how much of an log is being written to /var/log/Xorg.O.log before your boot process hangs, but that is where you would see a log of a video problem.  Maybe you could boot a Live CD and take a peek.

Speaking of which, does that PC boot and run a Live CD correctly?  If so, I'd study what the /etc/X11/xorg.conf file looks like on a booted system from Live CD.

---

### Post by Magic30 on 2009-01-22
The onboard graphics chipset is a VIA Chrome. The live CD (8.1 desktop, 32 bit) doesn't work with default settings either: it freezes while booting as soon as the round "loading mouse cursor" appears.

However with the "xforcevesa" boot option, the live CD actually boots!! I tried that boot parameter in my previous install (32 bit alternate install CD) too, but it didn't have this effect. Strange...

Now, I will try an installation out of the running live environment.

---

### Post by Magic30 on 2009-01-22
Hmm, that install worked fine. Ubuntu is running now. But why?
I did not change the hardware nor any bios settings.

The grub menu list shows that the kernel is not booted with special options...

Can someone try to explain this?

---

