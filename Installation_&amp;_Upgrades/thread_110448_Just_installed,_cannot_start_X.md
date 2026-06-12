---
title: "Just installed, cannot start X"
date: 2005-12-30
forum: Installation &amp; Upgrades
---

### Post by OrangeGoblin on 2005-12-30
First of all, I'm completly new to Linux, so apologies if I am making stupid mistakes

Second of all, I found a number of threads with people having a similar problem as me, but I'm not quite sure if it is exactly the same.

Thirdly, this is the only machine I currently have access to, so I am duel booting Windows and Ubuntu. This means that any error messages I get, I'm having to relay from memory, so I could be wrong.

Having got that out of the way...

I installed, booted up, and got an error saying X couldn't start. The problem was  "/etc/X11/X not executable", which I managed to fix thanks to this forum (or at least I think I did, the error doesn't come up anymore).

However, now when I try startx I get two errors - errno 111 and errno 3, both basically saying that I am unable to connect to the server. Does that mean the server has started, and I can't access it, or that it just isn't there?

I tried sudo dpkg-reconfigure xserver-xorg (again on the advice of these forums) and that didn't seem to do anything. I'm now pretty much at a loss, so any help would be great! Failing that, I guess I have to reinstall? Oh well...

---

### Post by OrangeGoblin on 2005-12-31
Can no one help with this?

---

### Post by wanger123 on 2005-12-31
Hi, what type of machine is it? Desktop, laptop? You could try typing: linux vga=771 at the boot prompt and/or pci=no acpi

If you have already installed the OS you may have to hit del or esc or F?? to get the boot prompt when starting your machine

hope it helps
wanger

---

### Post by OrangeGoblin on 2005-12-31
Hi, thanks for the reply. Its a desktop machine with an integrated graphics card (which I'm not using) and a pci geforce 2 (which I am using). What will those two commands do? Does pci=no acpi switch off pci stuff? Because thats where the graphics card is. Thanks.

---

### Post by surfer63 on 2005-12-31
I've seen a couple of times with my Kubuntu, after changing boot files, that it sticked to terminal 1 and that the server was locked when trying to start it manually with startx

After boot when you are at the terminal login, try to do ALT+F7 to switch to the default "X-terminal" . If your X has started you should find your graphical login there. If that's the point, Kubuntu will remember the next time you reboot.

good luck.

---

