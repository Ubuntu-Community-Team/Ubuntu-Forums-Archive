---
title: "Booting Acer Aspire One from a Ubuntu USB"
date: 2010-12-26
forum: Hardware
---

### Post by Mooooooo on 2010-12-26
Hi,

My Linpus system on Acer Aspire started working funny and I wanted to install Ubuntu. I made a bootable USB stick following those instructions [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download). The USB was made on another computer (Mac OS), and previously was formatted on that computer also.

However, when I try to boot the Acer from the USB it ignores it. But when I go to Bios settings it clearly sees the USB and asks me if I want to boot from it. I put it first in the boot order, choose to boot it (using f12) but all to no avail; the system just boots from the HD as if the USB wasn't there. 

Any ideas?

---

### Post by dandnsmith on 2010-12-26
I've recently noticed at least one other thread recently along these lines.

Personal experience says that you don't need to change boot order - you get the chance to boot without needing this, and it will work with a correctly formatted and written USBstick.

I've gone the route of using a Windows PC, and instructions from the [pendrivelinux](http://www.pendrivelinux.com/) site, and have seen others recommend this as well.

HTH

---

### Post by Mooooooo on 2010-12-26
I don't have a windows PC handy. Just a Mac...

I was also wondering whether I was using an incorrect format for the USB, or somehow unpacked the file wrong. According to the instructions in my link I downloaded it as an .iso, converted to an img.dmg and unpacked into the USB using sudo dd.

---

### Post by dandnsmith on 2010-12-26
Ok, that makes it outside my experience as I just have no dealing with Mac equipment, so have never tried that route.

With x86 based PCs, you don't convert the iso file, just use an appropriate installer to write it.

I suppose you can see the file structure on the stick?

---

### Post by Mooooooo on 2010-12-26
yes, I can see all of the Ubuntu files on there

to make the bootable USB I followed all of the instructions on that page I linked in the first post

---

### Post by dandnsmith on 2010-12-27
There's one bit of those instructions for the Mac which I don't (can't) know about - it relates to the format on the stick.

I see that the write seems to be using a dd command which, if anything like the linux dd results in a literal copy of the img file to the stick (in whatever format it might be).

I've always used FAT formatted sticks with an installer which writes to the stick, and the resulting stick is FAT formatted (and boots perfectly with my AA1).

I've seen postings relating to a problem caused when creating such a stick using a linux dd based on a .img file (which used to be available for the netbook version of ubuntu).

After this I'm stuck - but could this help you at all?

---

### Post by Mooooooo on 2010-12-28
> **dandnsmith said:**
> There's one bit of those instructions for the Mac which I don't (can't) know about - it relates to the format on the stick.

I tried formatting it using 'MS-DOS FAT' and I get the same result.

> **dandnsmith said:**
> I see that the write seems to be using a dd command which, if anything like the linux dd results in a literal copy of the img file to the stick (in whatever format it might be).

I've always used FAT formatted sticks with an installer which writes to the stick, and the resulting stick is FAT formatted (and boots perfectly with my AA1).

I've seen postings relating to a problem caused when creating such a stick using a linux dd based on a .img file (which used to be available for the netbook version of ubuntu).

After this I'm stuck - but could this help you at all?

that's exactly what dd seems to do - copy the files from the 'volume' (=directory) .img.dmg on the Mac HDD to the stick. So in theory it should work - all I do is download, convert, copy. But it doesn't...

---

### Post by trinitydan on 2010-12-28
On my GFs Acer Aspire One, sometimes you have to look for the USB in HDDs.  See if you have an extra HDD in your list of boot options that has a label that looks like it could be the USB drive.  Boot from the HDD designated one if its there.

---

### Post by Mooooooo on 2010-12-29
> **trinitydan said:**
> On my GFs Acer Aspire One, sometimes you have to look for the USB in HDDs.  See if you have an extra HDD in your list of boot options that has a label that looks like it could be the USB drive.  Boot from the HDD designated one if its there.

I just have a single list for all devices. It has IDE 0, IDE 1, USB HDD, USB FDD, USB CDROM, Network Boot. 

I put USB HDD top and the two IDE's bottom. Doesn't work.

---

### Post by Mooooooo on 2010-12-29
could the problem be that the Bios on my Acer is out of date?

it's version .3114

---

### Post by MoebusNet on 2010-12-29
Hmmm, I'm running my Acer Aspire D255 from Live-USB right now. I used usb-creator in Ubuntu 10.04.1 (System>Administration>Startup Disk Creator) to format & put Ubuntu on the USB thumb drive. If you can boot another computer from a Ubuntu Live-CD, you could set up your thumb drive this way. If you want to use your Live-USB to keep changes (documents saved, packages installed), enable that option when you get to it in the set-up menus.

I remember that my Live-USB showed up in the BIOS when I set it to boot from USB first, but I don't remember if I booted with the thumb drive plugged in or not. It wouldn't hurt to try that (plugged-in boot I mean).

EDIT: Just making sure, but you are using the PC version of Ubuntu for your Acer, not the Mac version, right?

---

### Post by Mooooooo on 2010-12-29
I don't know. I'm downloading it from here [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download). Could it be that the site detects I have a Mac and slips me the mac version?

The file names for the distributions I tried were

ubuntu-10.10-desktop-i386.iso
ubuntu-10.10-netbook-i386.iso
ubuntu-10.04.1-desktop-i386.iso

---

### Post by dandnsmith on 2010-12-31
Those distro names are all i386, and would not be Mac.

I don't know what BIOS version I have - but it hasn't been updated since purchase. When I have a bootable USB in a slot at bootup it offers the chance to boot from that, and it works when I take the opportunity - no messing about with the original installed boot order.

---

### Post by bouncingwilf on 2010-12-31
I'm writing this post now on an Acer Aspire and I've gone through the same processes as you but the bottom line is that I've never managed to get it to boot from a usb stick - always had to use the CD drive

Bouncingwilf

---

### Post by Jose Catre-Vandis on 2010-12-31
USB bootable sticks can be a bit finicky at times. I created a UNR 10.10 bottable stick using universalinstaller on Windows 7. It refused to boot on that same computer (a swanky Dell Precision M6500), however it boots fine on my AA1.

Try another stick, borrow an XP / 7 PC to create, you'll find the right combination in the end.

---

### Post by Jose Catre-Vandis on 2010-12-31
Forum had a crisis ;)

---

### Post by Jose Catre-Vandis on 2010-12-31
Forum had a crisis ;)

---

### Post by dandnsmith on 2011-01-01
Just been checking boot details for USBstick on AA1:

Have to hit key F12 at boot, then pick the USB stick from that menu and it all happens (if the stick is set up correctly).

HTH

---

### Post by Mooooooo on 2011-01-01
I seem to have managed to install Ubuntu from a CD in the end.

But I still didn't know why it wouldn't boot from a USB. The files on the USB and on the CD were exactly the same...

---

### Post by originalmaterial on 2011-01-29
Very simple explanation: It's because the instructions to make a bootable USB on mac os X don't work! 

I was in the same case as you and ended up just making the bootable USB from an ubuntu install in Virtualbox. There's a reason why the instructions for making a USB stick from a mac are prefaced by *"We would encourage Mac users to download Ubuntu Desktop Edition by burning a CD for the time being"* I guess...

---

