---
title: "No Gnome after login"
date: 2007-04-18
forum: Hardware &amp; Laptops
---

### Post by stchman on 2007-04-18
Hello all.  I recently started using Envy on a few of my PCs.  I was using the driver that came with the below installation:

sudo apt-get install nvidia-glx nvidia-kernel-common

sudo nvidia-xconfig

Then I changed the "nv" to "nvidia"

This installed the 87.76 drivers.  I have a GeForce FX5700 Ultra and thought the latest drivers 97.55 would do better.  So I removed the drivers from above by doing this:

sudo apt-get remove nvidia-glx nvidia-kernel-common

I then use Envy to remove and booted up the PC in recovery mode.  I then did a "Clean the Installation of any Nvidia Driver" option (6) and let her go.  Lots of text flashed before my eyes as Envy did its thing,

Ok I booted back into Ubuntu and got an XServer error (expected) and logged into Ubuntu in a text fashion.  Typed envy -t and selected option (1).  This installed the Nvidia driver.

After all that I was able to log in to Gnome no problem.  Well then the problem started.  I had to restart the workspace and when I did I was greeted with the Ubuntu login screen.  I logged in and the music played but no Gnome.  I have to restart the machine to get back into Gnome.

So my question is do the 97.55 drivers for Linux not work well with the 5700 Ultra?  Has anyone else had this problem?  Should I go back to the original driver?

Envy worked great on my laptop (ATI Radeon XPress 200) and desktop (7600GT).

Thanks

---

### Post by stchman on 2007-04-18
Anyone?

---

### Post by stchman on 2007-04-19
Update:

I installed the older 87.76 drivers and all is well now.

---

