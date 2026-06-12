---
title: "Serious USB2 issue..."
date: 2006-09-05
forum: Hardware &amp; Laptops
---

### Post by Konradman on 2006-09-05
Ok, so I have come across a serious issue which I can find only minimal information about. There seems to be a similar problem mentioned [here]("https://launchpad.net/distros/ubuntu/+source/initramfs-tools/+bug/47768").

Now, the problem is that when I boot Ubuntu, it hangs on "mounting file system" (the second thing it loads)... so I came across a few temporary solutions. 

1) I disconnected my external USB2 hub, with 2 hard drives, a DVD rom and a printer hooked up to it. Ubuntu booted.

2) I kept the hub in, and disabled USB2 support in my bios. Ubuntu booted.

Otherwise it will always hang on "mounting filesystem." Now this really sucks because I want Amarok to build my mp3 collection much faster than in 2 hours. Plus, I paid for USB2 hardware to be able to use it. I'm sure you can sympathize.](*,) 

So now my question is what do I do? How do I get my USB2 to work? Where can this problem be rooted? i scoured the internet for answers with very minimal results.

Also, a couple of newbie questions...

1) how do i eliminate the splash screen in the beginning so i can see exactly where the system is hanging?:-k 

2) is there a good resource describing how ubuntu (or linux in general) boots, what processes it goes through and what files it looks through? I want to learn how it all works so I can research how to fix some of these issues when they come up.

---

### Post by mkosmo on 2006-09-06
When you get to the grub loader, edit the commands it is booting to remove the word "splash" from the kernel arguments.  That will let you see whats going on.  If you want a little more detail you can remove "quiet" as well.

---

### Post by Marksman Ken on 2006-09-14
I have a similar problem, If I disable USB 2.0 on my motherboard (I can keep USB 1.1) it boots fine but with USB 2.0 it hangs.

I need USB 2.0 to use my Wifi and get onto the internet :(

EDIT: After more testing I found that changing the setting in my motherboard from High speed (480Mbps) to full speed (12Mbps) fixed the problem and allowed me to turn USB 2.0 back on.

---

### Post by Konradman on 2006-09-23
oh man, i am just having so much trouble with USB. my external usb2 hub spontaneously becomes nonexistant to ubuntu. 

is there anyway to refresh the usb ports? redetect the devices? because plugging and unpluggin doesnt work.

Anyone else having these issues?

I WANT FULL SPEED USB2!!!:mad: [-o< ](*,)

---

