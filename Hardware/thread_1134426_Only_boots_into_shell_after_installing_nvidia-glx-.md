---
title: "Only boots into shell after installing nvidia-glx-180.51"
date: 2009-04-23
forum: Hardware
---

### Post by darkzerox on 2009-04-23
I had this problem before, I just had to edit the /etc/X11/xorg.conf file, and add BusID "PCI:03:00:0" to the Driver section (I have one of those new fangled hybrid cards, and apparently it needs to know which one to use). But this time that isn't working. It only boots into the command-line. I can't uninstall nvidia-glx-180 either because it wants to connect to the internet (to uninstall? very frustrating!) and I can't get it to connect to the internet...at least not where I am. It requires authentication,and I don't know how to do that via the command-line. I tried xorg.conf.failsafe which uses the vesa driver, that didn't work either, and the "nv" driver didn't work either. fixx doesnt seem to exist on ubuntu 9.04... I'm really not sure what else to try. Suggestions?

thanks!

---

### Post by SketchyClown on 2009-04-23
> **darkzerox said:**
> I had this problem before, I just had to edit the /etc/X11/xorg.conf file, and add BusID "PCI:03:00:0" to the Driver section (I have one of those new fangled hybrid cards, and apparently it needs to know which one to use). But this time that isn't working. It only boots into the command-line. I can't uninstall nvidia-glx-180 either because it wants to connect to the internet (to uninstall? very frustrating!) and I can't get it to connect to the internet...at least not where I am. It requires authentication,and I don't know how to do that via the command-line. I tried xorg.conf.failsafe which uses the vesa driver, that didn't work either, and the "nv" driver didn't work either. fixx doesnt seem to exist on ubuntu 9.04... I'm really not sure what else to try. Suggestions?

thanks!

For net access, reboot and when it says **Starting GRUB**, hit the **ESC** key and boot to the **Recovery** kernel entry, and when it brings you to a blue screen with some options, select **NetRoot**. This will give you command line access with internet.

Also just a reminder, you are ROOT at this prompt so be careful what you do.

Now you can edit the xorg.conf if needed with pico or nano, and you can use APT t install anything you need.

HTH.

---

### Post by darkzerox on 2009-04-23
> **SketchyClown said:**
> For net access, reboot and when it says **Starting GRUB**, hit the **ESC** key and boot to the **Recovery** kernel entry, and when it brings you to a blue screen with some options, select **NetRoot**. This will give you command line access with internet.

Also just a reminder, you are ROOT at this prompt so be careful what you do.

Now you can edit the xorg.conf if needed with pico or nano, and you can use APT t install anything you need.

HTH.

Ah. Thank you. I tried that but I still couldn't connect wirelessly. I plugged a cable in though, and it works now.

Anyway...steps to fix:

sudo apt-get remove nvidia*
sudo apt-get install xserver-xorg (I think...... just try running 'X' and then it will tell you you're missing something, install that)
sudo cp /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf (you may want to back this up first)
sudo reboot

Now I have a perty GUI again, but the latest nvidia drivers still don't seem to like me...oh well.

---

### Post by sixcorners on 2009-06-05
Thanks for that last post, I was stuck with that same problem. :)

---

### Post by recluce on 2010-01-08
I had the same problem on my experimental installation of Ubuntu Lucid. After installing nvidia-185 drivers, the X-Server was broken and the system booted into the text-mode shell only.

Followed darkzerox instructions and was able to recover my system.

After that, added ppa:sevenenmachines/nvidia to the repositories and installed nvidia 195.22 drivers from there. The system is now working with all bells and whistles. :D

Thank you to darkzerox!

---

