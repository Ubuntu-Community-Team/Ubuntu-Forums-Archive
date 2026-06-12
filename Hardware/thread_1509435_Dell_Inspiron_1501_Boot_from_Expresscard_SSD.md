---
title: "Dell Inspiron 1501 Boot from Expresscard SSD"
date: 2010-06-14
forum: Hardware
---

### Post by migs73 on 2010-06-14
Good or bad idea?
I have read lots of stuff with problems for doing this type of thing and do not know if it would be worth the investment if I can't get it to work.

My bios has a setting for boot from 'removable media' which is separate from the USB boot and boot from CD drive options. The only other media I have is an SD/MMC card slot (unlikely to be that) and an Expresscard slot. 

If this could work is there a simple (and I mean simple!) how to that anyone knows about?

---

### Post by migs73 on 2010-06-18
Bump

---

### Post by migs73 on 2010-06-27
The overwhelming lack of reponse has made up my mind that this is probably not a good idea:confused:
I'll now marked thread as solved, as it kinda is?

---

### Post by piedramania on 2011-01-21
Hi, 

Probably is too late for an useful answer, but any way.

I recently bought an express card SSD: Verbatim 16BG expresscard SSD.

My Dell studio 1555 can't book from the expresscard (I already knew that, so not a big deal).
Grub is installed on the SATA harddriver, and boot from there. 
Boot is slight faster than from my 7200 rpm SATA drive, but not much.
(note that this SSD has 120 MB/s read, but 30 MB/s write) I also made quiet a few SSD filesystem optimization, such as no swap, no journaling, /tmp, /var/lock, /var/tmp to ramdisk, mozilla profile also to ramdisk, etc (check the internet for details)

It all looks to work fine, but from time to time the SSD card disappears from filesystem, just like if I were extracted it, only that I didn't. 
fdisk -l just doesn't list it.
Obviously, the system becomes unstable and I have to hard poweroff. After rebooting, everything is ok, and the SSD is still there and fine. Often it require a fsck.

I still haven't figure out why it happens.
It might be a connector malfunction, or a kernel issue.
I'm using kernel 2.6.35-25-generic and Kubuntu 10.10, 64bits. The previous release, 2.6.35-24 didn't support the expresscard SSD because of a bug ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/669343](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/669343)) so this may be related

Any Idea

---

