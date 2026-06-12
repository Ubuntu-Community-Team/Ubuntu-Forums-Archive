---
title: "Power off problem with Dell m1330"
date: 2008-07-10
forum: Hardware
---

### Post by jeffeb3 on 2008-07-10
Hardware:
Dell m1330 
Dell N wireless 
Nvidia 8400 graphics. 

I installed 8.04.  Rebooted several times without any problems, finished setting up vista.  

Then I got back into ubuntu, enabled the nvidia drivers, and configured ndiswrapper to control the wireless card.  Both of those things worked great.  

But, sometime after that, I've been unable to shut down or restart the computer from ubuntu.

It get's all the way down (I think) to the point where it should just turn off or restart, and then the screen starts slowly changing colors.  It's almost like the monitor isn't getting any instructions, and the noise or something is creating an image for it to write.  It's really slow, and it looks like colorful vertical bars.  For the shutdown, waiting will not help anything, I have to hld the power off for a few seconds.  In reboot, it waits maybe 15 seconds and then reboots.

I've seen this before, but never cared much.  Someone must know what to do.  I can't figure out what to search to get useful results.  My guess is that it has something to do with ACPI, but I have no idea how or where to configure it.  

I've been using Linux for a while, but if you have a suggestion, make it clear, so I know I'm doing it right (and others can get help even if they don't know how to change their /etc/default/acpi-support).

---

### Post by phidia on 2008-07-10
I think it would help to know the specific model of the wireless card.
In a terminal lspci -v
You could also try disabling ndiswrapper (sudo modprobe -r ndiswrapper) and the windows driver ndiswrapper installed. Shutdown after that and see if there's a difference.

---

### Post by jeffeb3 on 2008-07-10
I don't have my computer with me.  (bad forum form right?).

Dell calls it "Dell Wireless 1505 Wireless-N Mini-card" on the reciept.  But I will find out when I get home what it is and post it before tomorrow.

---

### Post by jeffeb3 on 2008-07-10
apparently, it's Broadcom BCM 4328 a/b/g/n.

```

0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
	Subsystem: Dell Wireless 1500 Draft 802.11n WLAN Mini-card
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f9ffc000 (64-bit, non-prefetchable) [size=16K]
	Memory at f0000000 (64-bit, prefetchable) [size=1M]
	Capabilities: [40] Power Management version 2
	Capabilities: [58] Vendor Specific Information
	Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [d0] Express Endpoint IRQ 0

```

As for the "sudo modprobe -r ndiswrapper".  I tried that, and then did an lsmod, and it is still there...
```

jeff@ltlredbook:~$ sudo modprobe -r -v ndiswrapper
rmmod /lib/modules/2.6.24-19-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
jeff@ltlredbook:~$ lsmod | grep ndiswrapper
ndiswrapper           192920  0 
usbcore               146028  5 ndiswrapper,uvcvideo,ehci_hcd,uhci_hcd

```

I'm getting pretty convinced this is the problem... I will try to research this approaching it as an ndiswrapper problem.  I wonder where the ndiswrapper is being loaded.

---

### Post by jeffeb3 on 2008-07-10
AH HA!!!

It's not ndiswrapper or nvidia.  That was just a coincidence.

I couldn't modrpobe -r the ndiswrapper, so I uninstalled it.  

It was still happening.  So I disabled nvidia proprietary drivers.

I've been using my wired ethernet so I check google for help etc.

When I shut down with neither installed, the computer still hung (hanged?) at the same point, for about the same time (maybe 60 seconds).  But this time, it showed an error message.  Something about CIFS can't find something.

If you haven't figured it out by now, I should say that I set up a smb automount to connect to my home file server in the same boot that I set up nvidia and ndiswrapper.  The network module was taken down before the OS tried to umount the drives in fstab.  I'm guessing CIFS wants to say one last thing to the samba share before it umounts, so it just sits there for 60 seconds, waiting.  Meanwhile, when I was using the nvidia drivers, that module was also taken down, so all I was was the random things that the video card could give me since it had no instructions.

I confirmed this by booting without any network.  The CIFS never mounted, and the shutdown/reboot happens normally.  

So this problem went from an ACPI, to an nvidia or ndiswrapper, and now it's a CIFS problem.  

Does anyone know if it's safe to put a umount /media/server somewhere sooner in the shutdown process?  Maybe I should find another way to connect to my server...

---

### Post by jeffeb3 on 2008-07-11
This is a common problem, with CIFS.  Here's a link to a solution:

[http://blog.avirtualhome.com/2008/03/10/ubuntu-shutdown-problem-cifs-related/](http://blog.avirtualhome.com/2008/03/10/ubuntu-shutdown-problem-cifs-related/)

---

### Post by phylae on 2008-07-15
> **jeffeb3 said:**
> then the screen starts slowly changing colors.  It's almost like the monitor isn't getting any instructions, and the noise or something is creating an image for it to write.  It's really slow, and it looks like colorful vertical bars.

I get something very similar. There isn't much color though. It usually fades to or from black or white. The vertical lines appear/disappear. However, If I wait 15-30 seconds the computer will shutdown.

I first noticed this when I upgraded to Hardy from Gutsy. I have a Dell XPS M1330.

---

### Post by avpap on 2008-07-15
My XPS1330 with same configuration as yours works perfectly with Ndiswrapper and Wicd instead of network manager and of course it's closing normally. I also have dual boot with Windows Vista Business.

---

