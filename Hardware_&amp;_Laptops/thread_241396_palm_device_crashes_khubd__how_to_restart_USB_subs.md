---
title: "palm device crashes khubd / how to restart USB subsystem?"
date: 2006-08-22
forum: Hardware &amp; Laptops
---

### Post by ChrisC on 2006-08-22
I've been putting it off for 6 months because I knew it would suck, and today I'm doing it: trying to get Palm sync working on my Ubuntu Dapper installation. Alas, my fears have proven correct.

Here's the latest problem, in sequence:
1. Freshly booted system.
2. lsusb shows a couple ports and one device (a flash reader)
3. I tail /var/log/messages to watch it while I do step 4
4. I plug my palm device into a USB port
5. Messages in /var/log/messages indicate that the device is recognized
6. lsusb shows the additional Palm device
7. I press the palm device's hotsync button, intending to see what pilot-xfer thinks of it.
8. tailed log immediately shows that khubd has crashed
9. lsusb now gives no results -- it hangs and I have to kill the terminal
10. I have to reboot the whole system to get USB functionality back, measured by whether lsusb works.

When I attempt the device HotSync, a whole lot of stuff gets dumped to the log, including this at the beginning:

Aug 19 18:00:12 localhost kernel: [17179931.608000] usb 1-3: USB disconnect, address 4
Aug 19 18:00:12 localhost kernel: [17179931.608000] ------------[ cut here ]------------
Aug 19 18:00:12 localhost kernel: [17179931.608000] PREEMPT SMP
Aug 19 18:00:12 localhost kernel: [17179931.608000] Modules linked in:

... some things in the middle about process, stack and call trace information (I can provide on request), and then this at the end.

Aug 19 18:00:12 localhost kernel: [17179931.608000] <6>note: khubd[1904] exited with preempt_count 1

Any ideas?

Any way to restart the USB subsystem without rebooting the whole computer?

[I have a standing offer to pay $20 to anyone who helps me solve my problem, even just materially moving me forward.]

---

### Post by ChrisC on 2006-08-24
Anyone?

---

### Post by ChrisC on 2006-08-25
heeeeeeeeeeeeeeelp.....

---

### Post by ciscosurfer on 2006-08-27
bump (sorry ChrisC, I don't have a clue...but I'm sure someone does ;))

---

### Post by ChrisC on 2006-08-27
Thanks ciscosurfer ... and another bump ...

Maybe I'll get a better response with a subject like "OMG Ubuntu sucks i am so tired of it" :)

---

### Post by ciscosurfer on 2006-08-27
bump.

Nice. =D>  I'll keep bumping.

Or maybe try, "Ubuntu rocks, what do you think?"....or, "Palm expert needed ASAP."

---

### Post by isandir on 2006-08-28
Try installing a new kernel revision.  Specifically, 2.6.17.1 or newer up to 2.6.17.11.  I don't really want to walk you through all of the ins and outs of a kernel upgrade.... I am sure there are some good walkthroughs here.  Remember you can upgrade your kernel and just give it a seperate entry on your bootloader.  This way if it all goes wrong you just get to reboot and choose the old kernel from the list grub or lilo gives you.  Well... I know you can do it with lilo.  I'm not sure about grub, but I would be very disappointed if it didn't have that functionality.  

If you want to stay in the 2.6.16 line of kernels, just try getting the newest one but it won't hurt to try going to 17 :).

kernel.org has all sorts of info related to what version is stable and other neat info.

I still see some usb related bugs reported in .17 too :(

Cheers

Isandir

---

### Post by Quirky on 2006-08-29
Does */etc/init.d/udev restart* get USB back again? It should do...

---

### Post by dsauxier on 2007-12-11
Restart USB : 
sudo rmmod ehci_hcd
sudo modprobe ehci_hcd

If that doesn't work, it may be one of the other hcd modules that needs to be reloaded.
Get a list of them : 

sudo modprobe -l  |grep hcd

Try them all.

---

