---
title: "Ubuntu is running in low graphics mode"
date: 2008-09-13
forum: General Help
---

### Post by Static42 on 2008-09-13
> Ubuntu is running in low graphics mode

That's the error message I get after ubuntu loads up and before the login screen. I was trying to install sound drivers for my sound card. When I restarted the computer, I began to receive those error messages, and each time I restart they keep on coming back. I assume the video card drivers somehow got corrupted when I installed the sound card drivers.

It gives me three options: Configure, Shut Down, and Continue. When I click on Continue, the screen goes blank. Nothing happens at all. I'm forced to shut down. When I try to configure the options and set my graphics card, I click OK, but I am still led to a blank screen.

I'm unsure of what to do. Help?

---

### Post by kokkus on 2008-09-13
This can be fixed by repairing the xserver from recovery mode
And now when you start your ubuntu again you'll have to enable the graphic driver again.

---

### Post by byzer on 2008-09-14
Hi,

I'm getting the same in Mythbuntu (which is essentially Ubuntu 8.04).

I installed a new Nvidia 9500GT, and had it all running. I then installed a few other drivers (including a NetGear WG111 USB wireless dongle), and now it constantly runs in Graphics Safe Mode. I've uninstalled / re-installed my Nvidia drivers a number of times, and even reverted back to an earlier Kernel version (which it was successfully running in). 

How do I enable normal graphics mode? I'm not sure how to repair X.

Any ideas?

---

### Post by Interpreter on 2008-09-20
I also seem to be stuck in lg mode and have no idea of how to use that recovery mode thing.

---

### Post by dylyn on 2008-10-01
You can try using 'envy' from recovery mode.  Boot your machine; if the grub boot menu is hidden, I think you  can hit any key to make it show up.  Arrow down to one of the selections that says "recovery mode" and hit enter.

That should get you to a text console.  You might need to run 'apt-get install envy' or 'apt-get install envyng' (7.10 uses envy, 8.04 uses envyng).

You can run "envy -t" to install or fix your ATI or Nvidia drivers from the console.

dylyn

---

### Post by komoras on 2008-10-23
or you can return xorg.conf to default by:


sudo dpkg-reconfigure xserver-xorg

---

### Post by Interpreter on 2008-10-23
thanks, worked.

---

