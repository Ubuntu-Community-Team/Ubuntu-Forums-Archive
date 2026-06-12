---
title: "SSD, wifi broken on new HP Omen; work in recovery mode -&gt; boot"
date: 2014-12-30
forum: Hardware
---

### Post by entropius42 on 2014-12-30
I recently replaced my dead laptop with an HP Omen and noticed two problems:

1) Wifi doesn't work (it's listed as "hard blocked" in rfkill, but there is no hardware switch)
2, and more serious) The SSD is incredibly, incredibly slow. It took two hours to install, and fifteen minutes just to "sudo apt-get install vim". hdparm reports a transfer rate of 2MB/s.

Looking at dmesg indicates an IRQ conflict between the Nvidia card and the SSD (which is an m.2 PCI express model).

Now, the second problem can be worked around, I suppose, with a USB dongle. But a painfully slow SSD can't.

However, when I boot the system into recovery mode and then choose the "finish booting" option, I get normal SSD performance (791 MB/sec). I do notice that not everything is loaded: in particular, glxgears seems to be running in software mode (GL_VENDOR is VMware) and my backlight control buttons don't work.

Can anyone suggest anything that might

1) cause this behavior
2) might be worth looking at to resolve the problem "honestly" without recovery mode, and thus enable all the hardware?

Also, what exactly does recovery mode do?

---

### Post by Ray_Ramos on 2015-02-01
> **entropius42 said:**
> 
1) Wifi doesn't work (it's listed as "hard blocked" in rfkill, but there is no hardware switch)


I happen to have an HP Omen available to me and did a quick test for you with the ubuntu-14.10-desktop-amd64 ISO.
Booting it into "Try" mode, I was able to get the Wifi working through the GUI tools (Enable Wi-Fi, Enable Networking, etc).

Looking at my rkill output, I noticed three interfaces:
0: hci0: Bluetooth
1: acer-wireless: Wireless LAN
2: phy0: Wireless LAN

After thinking about how you mentioned there was no physical switch to toggle "Soft blocked" and "Hard blocked" I tested toggling with the "fn" key + f12. On the Omen that is Function + Wireless. My rfkill output does change for hci0 and phy0 when I toggle this, and enabling the locks on phy0 does cause my wireless to stop working. More interesting though is toggling back doesn't work! 

Restated, my phy0: Wireless LAN interface had Hard blocked=no and Soft blocked =no until I toggle fn+f12 the first time. After the toggle they are both yes. After the second toggle only Soft blocked goes back to no and Hard blocked remains yes! :mad: 

I found this thread that might help. I don't have more time at the moment to continue but I think the guys on this thread have it figured out :
[http://askubuntu.com/questions/98702/how-to-unblock-something-listed-in-rfkill](http://askubuntu.com/questions/98702/how-to-unblock-something-listed-in-rfkill)

Basically the thread indicates that even it's listed as a hardware block it's often in BIOS or triggered by a kernel module. In both cases there are workarounds detailed in the thread.

> **entropius42 said:**
> 
2, and more serious) The SSD is incredibly, incredibly slow. It took two hours to install, and fifteen minutes just to "sudo apt-get install vim". hdparm reports a transfer rate of 2MB/s.

What did you use to measure performance? I wasn't able to reproduce this problem. See if you're using the same ISO I noted above, and do things in Try mode(choose Try in boot menu instead of install) if you want to be certain your hardware and software config match what I was testing with. I'm hoping maybe you just used a different ISO and this one solves that problem for you.

Good luck!
Ray

---

### Post by Ray_Ramos on 2015-02-01
Update: I messed around more and found that the magic seems to be : sudo modprobe -r acer_wmi
Apparently the acer_wmi kernel module just gets in the way. I was wondering why an HP laptop had a second Wifi adapter made by Acer in there...

Hope this helps.

Thanks,
Ray

---

### Post by baluchi on 2015-02-04
> **Ray_Ramos said:**
> Update: I messed around more and found that the magic seems to be : sudo modprobe -r acer_wmi

This little *magic* worked for me, thank you very much.
My next task is to get the NVIDIA graphics to work.

**Update:** Removing [FONT=courier new]acer_wmi[/FONT] module on startup makes my life easier. This can be done by *blacklisting* [FONT=courier new]acer_wmi[/FONT].

In terminal, use the following command to edit modules blacklist
[FONT=Courier New]sudo gedit /etc/modprobe.d/blacklist.conf[/FONT]

At the end of the file, add the following lines
[FONT=Courier New]# Fixing a bug that prevents wifi from working on HP OMEN
blacklist acer_wmi[/FONT]

---

