---
title: "USB mouse dies, killing all USB ports"
date: 2006-06-19
forum: Hardware &amp; Laptops
---

### Post by Frem on 2006-06-19
I've got a generic USB mouse. It works fine in Debian.
Unfortunetly, in Ubuntu, it seems to break after a thirty minutes or so of use.
It seems to be triggered by using the scroll wheel on certain web sites, moving the mouse while a full screen admin password prompt is up, and certain other seemingly random things.
What's really annoying is that when the mouse dies, it kills all the other USB ports on the machine. I have to reboot to reset them.

Any ideas why this is happening and how I can fix it?

I'm using this on a Toshiba Satellite M55-S139 laptop with the 686 kernel (happens with the 386 kernel also, though).

---

### Post by Frem on 2006-06-23
...Anyone?
I've looked though dmesg and some other stuff I found in /var/logs, but I can't find anything that looks useful. Maybe I've just missed it. What logfile would something like this be reported in?

---

### Post by jjborcha on 2007-03-09
i was having big problems with my USB mouse hanging in Ubuntu (actually i tried more than one distro and more than one kernel to see if that was the problem).

the rest of the system would be fine after the mouse died, i.e., i could still use my PS/2 keyboard and interact with the command prompt.

reinserting the usbhid kernel module would fix it, also plugging the mouse in again would fix it.  i was getting some strange messages in /var/log/kernel involving "IRQ lossage" if memory serves me correctly.  

random things seemed to trigger the hangup, but it would happen every 10 to 30 minutes.  very annoying!

i fixed the problem by turning off "legacy USB device support" in my BIOS configuration.  (it is a ASUS P5N-SLI motherboard with NVIDIA chipset.) i've read that my BIOS has some sort of PS/2 mouse emulation for USB mice, and that the linux kernel basically does not like this.  windows never had a problem with this feature turned on.

---

### Post by mvaranda on 2007-04-14
My Toshiba was working fine with 6.06 but USB started freezing after upgrading to 6.10.

The fix that worked for my machine was the following:

sudo gedit /boot/grub/menu.lst

change boot option (red):

kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda3 ro quiet splash [COLOR="Red"]noapic irqpoll pci=routeirq[/COLOR]

I hope it helps.
Take care

---

