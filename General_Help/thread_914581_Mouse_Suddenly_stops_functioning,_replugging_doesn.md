---
title: "Mouse Suddenly stops functioning, replugging doesn't work"
date: 2008-09-08
forum: General Help
---

### Post by Codename46 on 2008-09-08
Hey guys,

I'm running Ubuntu 8.04, and have a Logitech MX518 USB optical mouse. Occasionally, my mouse just stops working. The red light at the bottom of the mouse still shines, but the cursor doesn't move. This has happened 2 or 3 times before, and appears to happen at random times. I'm pretty certain my mouse isn't broken because it works all the time in Windows XP. Unplugging it and plugging it in again doesn't work, and when I do it, the red light under the mouse doesn't shine. Restarting my computer solves the problem, but I was wondering if there's something in the command line I can type in to resolve this quickly

Right now I have to keep pressing tab to navigate the forums and post this thread :P

My system specs:

AMD Athlon 64 5600+ Socket AM2
EVGA Nforce SLI 590 motherboard
PNY Geforce 8800GT 512MB PCI-e
Creative Labs Soundblaster Audigy SE PCI
OCZ 2GB DDR2-800 RAM

Thanks

---

### Post by Codename46 on 2008-09-09
Ok, I think I might have isolated the cause, but still haven't found a solution. This has happened 3 times in the last 10 minutes, and I had to reboot every time. I think it might be caused by Rhythmbox, because the mouse would freeze while playing a particular song.

Still befuddled though

---

### Post by fragos on 2008-09-09
You may have some hair or dust in the optical opening. My last mouse had this problem on a regular basis. I'd just blow the junks out and it would work again. Seeing the red light doesn't mean there's nothing in there. What you are using for a mouse pad could be part of the problem. I now have a different mouse and a "wowpad" which is designed for optical mice. I haven't had this problem occur in a long time.

---

### Post by duffy_ryan on 2008-09-13
I've been having the same problem. I'm almost positive its nothing to do with the mouse itself. I don't know what to do. I can get nothing done having to reboot every 2 or 3 minutes. Can someone please help?

---

### Post by kanem on 2008-09-15
This is a problem that has been around for a while. And there are threads about it, which I'm trying to find now, which is how I came across this one.

I have exactly the same symptoms. Mouse stops working, but light is still on. If I unplug it and plug it back in, it still doesn't work and light stays off. This isn't actually a mouse problem, its a USB problem. At the same time my mouse stops working, so do all my other USB devices.

I'm not sure about the cause, but if we are experiencing the same thing, then a partial fix is to add a couple of options to the kernel in /boot/grub/menu.lst:
Change the line that reads:
```
/boot/vmlinuz-2.6.24-19-generic root=UUID=2c0b4d74-a4be-4007-8e97-9ea7b047eda2 ro quiet splash
```
to:
```
/boot/vmlinuz-2.6.24-19-generic root=UUID=2c0b4d74-a4be-4007-8e97-9ea7b047eda2 irqpoll pci=routeirq ro quiet splash
```
The only difference is the addition of the two options "irqpoll pci=routeirq". 

I say this is a partial solution because, at least for me, it causes another problem. My mouse becomes a bit jittery whenever there is a high CPU load. 

So, I'm searching for a better solution that someone may have come up with since the last time I looked into it a couple of years ago.

Here's a sample of what you'll find if you google "usb stops working linux irqpoll":
[http://www.linuxquestions.org/questions/slackware-14/usb-device-stops-working-after-a-time-fix-stops-cdrom-device-mountreadability-538595/](http://www.linuxquestions.org/questions/slackware-14/usb-device-stops-working-after-a-time-fix-stops-cdrom-device-mountreadability-538595/)

Edit: some folks in this thread:
[http://ubuntuforums.org/showthread.php?t=189572&page=4](http://ubuntuforums.org/showthread.php?t=189572&page=4)
seem to have had more luck with "acpi=force irqpoll"

---

