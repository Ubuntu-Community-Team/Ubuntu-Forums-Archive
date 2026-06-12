---
title: "Question: How to create liveusb from iso using a mac?"
date: 2009-07-01
forum: Installation &amp; Upgrades
---

### Post by ethidda on 2009-07-01
**Short Version**

I have a 4gig USB stick that I know is bootable with my laptop from previous experience. I want to put the latest version of ubuntu livecd on it to make it a liveusb. And I have to do this using a mac (10.5) on a different computer.



**What I've tried**

I've tried the following:

1.) unetbootin for linux - apple won't seem to even read the binary

2.) macports wine with netbootin for windows - seems to work, but laptop won't boot from usb after everything's finished. I get a black screen with a blinking underscore-cursor after "booting" from usb.

3.) macports wine with liveusb - neither the regular version nor the w9x version would run, so I just gave up.

4.) "dd if=path/to/image.iso of=/dev/disk2" - after it copied everything (which took much longer than method 2), the laptop does not recognize the usb stick as bootable at all and skips over it completely.



**Long version**

I have a Thinkpad X61. It's 12", ultra portable, and has no optical drive (and I'm not in the position to acquire one, or even a router right now, as I'm on the go). I've been using (X)ubuntu on it for about the past half year perfectly fine. The reason I wanted a fresh install at all is because I wanted get rid of the windows restore part on on the harddrive.

I was able to "reinstall" it several times with the liveusb I created from the 8.04 version. However, for some reason, the bios thought the harddrive was corrupt and would want to load the windows restore partition, which has already been wiped. It did not even load the bootloader.

I had thought this might be a problem solvable with a new version of linux. So naively, I did (1) and (2) above to make my usb stick a liveusb with the 9.04 ubuntu. (I even reformatted the drive into FAT beforehand.) However, after this, it seemed that the usb is no longer live at all.

So now I have a 1-year-old ultra-portable thinkpad which does not have any bootable operating system, and cannot boot from the usb. I'd like to make a liveusb using a mac (the only working computer to which I have access). If anybody has any other suggestions, I'm open to them. But I cannot buy an external optical drive or boot from network (it's just not possible).




I'm much obliged to anybody who can help. Otherwise, I just have a piece of brick. Thank you in advance.

---

### Post by ethidda on 2009-07-01
Okay, I think I got it to work. I reformatted the usb in mac with a MBR partition table. Then I ran ubuntu in a virtualbox (from the livecd) and used it to create the usb stick.

Now it's booting (but into "(initramfs)", but that's another issue).

If anybody needs more detailed instructions, I can give them.

---

