---
title: "Logitech Anywhere MX problem"
date: 2013-01-29
forum: Hardware
---

### Post by chenriques on 2013-01-29
Hi.

I have a wireless mouse from Logitech (Anywhere MX) that connects to the PC using the Logitech Unifying Receiver (USB dongle).

Every time I restart the laptop I need to remove the receiver and plug in it again to the mouse start working. 
After that it works great, but it would be better if it could work without having to plug off\plug in every time the laptop starts.

Anyone have the same problem?
Any ideas?

Thanks in advance :)

---

### Post by chenriques on 2013-02-01
Anyone?

---

### Post by Mark Phelps on 2013-02-01
Sorry, but I think you're stuck doing that.  

I have a multi-port USB hub that I have several things connected to because my laptop only has two USB ports -- and I have to unplug and replug the USB hub every time.

---

### Post by chenriques on 2013-02-02
Hi Mark.

I've found this bug report in the launchpad:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1006145](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1006145)

It seems to be a common problem.
It's odd it exists since Ubuntu 12.04 and still is active in the latest kernels of 13.04.

I'm with kernel 3.8.0-4.

---

### Post by massacgr on 2013-02-17
**My temporary suggestion would be to see if you know someone with an older receiver (who does not use linux) and see if that person is willing to swap, even just to test it out.**

--------------------------------------------

Using an OLD unifying receiver, my mice (yes, I tried 2) and keyboard work just fine in Ubuntu; however if using a new receiver they do not.  The reason I have both is that I lost my old MX Anywhere mouse (the old model), but still have the receiver from it.

Upon plugging the old or new unifying receivers into my laptop, I get the following:
Bus 003 Device 006: ID 046d:c52b Logitech, Inc. Unifying Receiver

If I plug both in, I get this:
Bus 003 Device 006: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 007: ID 046d:c52b Logitech, Inc. Unifying Receiver

That gives me the impression that both are being detected.

--------------------------------------------

Here is what I have tried on a Windows machine using the Unifying software:

[LIST=1]
[*]Remove all pairings from both devices
[*]Added any combination of 1, 2 or 3 devices to ONE receiver at a time.
[*]Tried that receiver in the Linux laptop.
[/LIST]
--------------------------------------------

[LIST]
[*]With the OLD receiver, depending on how many devices are paired, the command "ls /dev/hidraw*" displays at least hidraw0 and hidraw1
[*]With the NEW receiver, no matter how many devices are paired simultaneously, no /dev/hidraw entries appear.
[*]If I pair the devices with the new receiver, while the laptop is on and plug them in, they (sometimes) work until I reboot the machine again at which time the connection is lost.
[*]If I paired 1 or 2 devices on one receiver and the remaining on the other, only devices that were paired with the OLD receiver appear as entries in /dev/hidraw*
[*]"ls -l /dev | wc -l" shows 217 entries when the old receiver is plugged in.  If I plug in the NEW receiver that number does not change.  Unplugging the OLD receiver, reduces the number of items in /dev, but adding the NEW receiver does not even if the old receiver is not connected.
[/LIST]
--------------------------------------------

I suspect something might have changed in the receiver itself that is causing this, but that is my impression at this point.

---

### Post by greenwapiti on 2013-03-04
The discussion in the bug report noted above has a workaround solution effective for some users.

---

