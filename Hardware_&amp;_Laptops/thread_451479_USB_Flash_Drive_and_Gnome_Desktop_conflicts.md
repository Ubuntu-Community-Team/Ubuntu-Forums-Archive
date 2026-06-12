---
title: "USB Flash Drive and Gnome Desktop conflicts"
date: 2007-05-22
forum: Hardware &amp; Laptops
---

### Post by spillz on 2007-05-22
Hi Folks

I've recently installed Ubuntu Feisty (my first permanent linux install) on an HP Compaq NC6000. Largely trouble free except for running my USB flash drive. Here is a rough log of "my troubles"

1. I tried to simply plug my Imation USB flash drive into the USB port while ubuntu was running, but nothing happened

2. (after scouring the web) I ran "lsusb", which showed the device was present when it was plugged in and absent when it wasn't

3. (more web searching) I restarted the computer with the flash drive connected and the device showed up on the desktop and nautilus

4. I (carelessly) unplugged the flash drive without unmounting. plugging the flash drive back in (without restarting) did nothing.  then my real troubles began...

5. Launching gnome desktop apps such as the terminal, gedit, nautilus takes more than 10 seconds (previously less than a second). this is true even after a restart. other apps seem fine.

6. plugged the flash drive back in and restarted. The device was found upon restart, the delays disappeared and everything was working again.

7. after plugging in and removing a few more times (each time using unmount in nautilus if the option was available) the 10 second delays have returned and restarting with the USB key installed no longer resolves the delays.

8. Whenever I have the device plugged in ls /dev shows the device present as sdb1, but the drive is never mounted except at restart.

Can any one help me fix my gnome conflicts and get the usb flash drive working normally? I was under the impression the hotplugging flash drives should just work without messy configuration...

---

### Post by spillz on 2007-05-22
my (very big) mistake. turns out I have to distinctly separate problems that were related only by coincidence.

1. the 10 second delays were caused by specifying a domain with my computer name (e.g. COMPUTER.LOCAL). When the computer was not connected to the net (the same times I was using the USB flash drive) there was a 10 second network timeout during the launch of all gnome applications. After I deleted the domain name the network timeout disappeared. This is probably a bug, right? (I discovered this by running strace)

2. The USB flash drive is only mounted on power up. I can manually mount it at any time only by using pmount. Is there a fix for this? flash drives are supposed to mount automatically right?

---

