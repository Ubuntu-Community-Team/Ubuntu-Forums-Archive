---
title: "USB TouchPad"
date: 2007-07-20
forum: Hardware &amp; Laptops
---

### Post by gaelfx on 2007-07-20
I am living in China and I just bought a USB TouchPad in hopes that I could practice my Chinese writing on my computer. When I plug the device in, the OS seems to recognize it (it shows up as "PenPower Touchpad" in the device manager), however, I cannot find any program capable of using it. I thought I would be able to use GIMP to at least draw with it, but it doesn't show up in the available input devices for the program.

Can anyone tell me how to make it available? I would be especially thankful if anyone could tell me about some programs that would help me test my ability to write Chinese characters (I already looked through the education software available in Add/Remove Applications). Thanks!

---

### Post by gaelfx on 2007-07-21
is no one using an USB touchpad with Ubuntu? that's hard to believe....

---

### Post by overdrank on 2007-07-22
> **gaelfx said:**
> is no one using an USB touchpad with Ubuntu? that's hard to believe....

Hi and I did search but this is all I have found 
[http://ubuntuforums.org/search.php?searchid=24104060](http://ubuntuforums.org/search.php?searchid=24104060)
Sorry I could not be of more help. :(

---

### Post by teledyn on 2007-09-29
It is likely more a *Linux* issue than it is anything Ubuntu could fix on their own; I also have one of these little PenPower touchpads, they are super cheap and probably super simple, but yeah, there are no Linux drivers -- Linux can know what the device is called because the USB interface provides an 'info' command that just returns a string.

btw, the link in the comment above doesn't work.

I'll keep looking and if I find anything I'll post it here.  It would be a very useful addition to Ubuntu to support a low-cost pen interface like this; there are drivers for the Koala Pad, but I think only the hard-core graphic artists would be able to justify that sort of hardware cost.

Now here's maybe an option: [Windows drivers are available online](http://www.hkepc.com/bbs/viewthread.php?tid=769205) so wouldn't it be possible to load those drivers using the ndis support the way we support all those windows-driver wifi cards?

---

### Post by breaking on 2008-01-05
It seems that the PenPower touchpad support was added to the latest linux kernel since October 2007, 2.6.24, not released yet.

[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=14e4020630b364cc564172a476cd6a6ac4bc7393](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=14e4020630b364cc564172a476cd6a6ac4bc7393)

You can try it using git if you are eager. You also need xorg-xserver-input-evtouch. See instruction at:

[http://linux.chapter7.ch/touchkit/](http://linux.chapter7.ch/touchkit/)

You might need to add the id of your own device.  

less /proc/bus/usb/devices

---

### Post by teledyn on 2008-05-24
[http://www.linuxquestions.org/questions/linux-hardware-18/how-does-linux-handle-usb-mouse-634247/](http://www.linuxquestions.org/questions/linux-hardware-18/how-does-linux-handle-usb-mouse-634247/) contains some code to test this device using the hiddev0 device, but it also illustrates a problem: treating this as a tablet device is annoying for graphics because the square of the touchpad is mapped to the entire screen.  Very awkward to use as a drawing device.

What is needed is a mouse-device based on this hiddev code so the tablet behaves more like the synaptics pad.

---

### Post by gaelfx on 2008-07-04
I realize that this post is ridiculously out of date, but I thought I would throw it out there the reason I want the pad to work is that I would like to use it to practice writing my Chinese. Do any of you know of any good programs for that?

---

