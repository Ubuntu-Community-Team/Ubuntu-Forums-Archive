---
title: "[SOLVED] iPod 6G woes."
date: 2008-09-30
forum: General Help
---

### Post by fINTiP on 2008-09-30
Guys, I'm bewildered.

I can't get my 6g ipod 160gig working, and I don't know why.

I'm trying to use Floola.

When I was plugging it in to the back of my Dell Latitude C640's only USB port (which I have reason to believe is usb 1.1, not usb 2), the ipod would connect for 1 second, and then begin ejecting.

I happen to have an HP PCMCIA laptop card that has 1 firewire and 1 usb (that I have suspect is usb 2) port, so I plugged that in, and plugged the ipod in to that.

When opening Floola, it acts like there is no iopd connected. I think I have an independent problem with floola, perhaps, because on the [floola faq]("http://www.floola.com/modules/wiwimod/index.php?page=docs_troubleshooting"), it mentions inputing the fwid (which I have obtained) for your ipod if it is 6g (which mine is), and I don't see any possible way to input that.

And yet, perhaps you only see that option if it detects the ipod in the first place.

So here's the thing, though. "dmesg" shows a bunch of "FAT: ..." errors, and when trying to view the ipod in Nautilus, I see no files. (I have set it to see hidden files, so that isn't the issue).

I also cannot unmount the ipod. I right click, and select "unmount", and nothing changes. The ipod still says it is connected, and right clicking still shows the "unmount" option, not the "mount" command it would show if it were unmounted.

What the heck is going on?

To add to the difficulty, this could end up being a card problem, also. When I used to try and use a certain usb webcam through the port on this card, it would work for a second, and within a moment get worse and worse, until the picture was so distored you couldn't see it (the camera was known to have problem with linux, however, so who knows). It appeared to be that the card would get hot, and make it worse as it got hotter- just a theory.

A usb keyboard works fine through it, however.

So yeah. Anyone have any ideas? Need some more info I can give?

Using Hardy, multimedia edition, latest upgrades. 1 gig ram, 2.2Ghz process, Dell C640.

K

---

### Post by fINTiP on 2008-10-10
I have discovered that my PCMCIA card was indeed a slightly fried USB port.

It also appears the USB port on my computer is erroneous.

Still wanting feedback, if someone thinks the evidence suggests otherwise.

L

---

### Post by fINTiP on 2008-11-04
I have discovered that my USB port on the computer itself seems to be fine. While I had thought it must be dropping data, and thus able to access something like a webcam but not something like an ext. harddrive, (unable to handle file systems), I was able to access a USB key and copy pictures to my computer from it. I noted that it tried to mount the USB key as "IPOD" at first, which made me realize some weird software problem must be happening...

Any ideas? My dmesg is interesting when I plug in the ipod, if that's worth anything, giving me I/O buffer errors and other things.

L

---

### Post by fINTiP on 2008-11-07
So, I figured out my problem. On this laptop, the cord's USB tip barely fits in my USB port. I had to really jam it in there, and it was fine. It was causing problems with mounting to be removed in the middle of the process and the like, and would 'sort of' detect it, but not make all the proper detections for sending data, it seems.

So, problem solved- if you're here looking for similar symptoms, I recommend checking connection abilities. In this case, data was being lost through the USB, but it wasn't a hardware defect, just a loose connection (Even though the cable was firmly lodged, it just wasn't fully inserted).

L

---

