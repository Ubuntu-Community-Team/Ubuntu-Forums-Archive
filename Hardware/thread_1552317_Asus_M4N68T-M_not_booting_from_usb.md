---
title: "Asus M4N68T-M not booting from usb"
date: 2010-08-13
forum: Hardware
---

### Post by Jason9 on 2010-08-13
I recently built a computer, and I used the Asus M4N68T-M:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131626](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131626)

I have tried multiple OS's with multiple tools to put them on usb drives, but none will boot. The board DOES support usb booting, and the board is recognizing the usb drive, because in the BIOS it says 1 USB device when it's plugged in. I've tried putting Ubuntu on two different usb drives, tried using Unetbootin and the Universal Linux usb installer thing.

I'm stumped.

EDIT:

Also, the usb drive DOES boot on my other computer, and all of the md5 sums match up

---

### Post by jmfal on 2010-08-13
Even though your mobo supports usb boot, still have to go into bios and select that as your 1st boot priority, save, exit, try to boot from usb.

If no success, restart, go to boot menu {not bios} see if there is option for usb, or maybe a card reader, make selection using keyboard arrows, same as in bios, hit enter should boot.

If you use card reader make sure you plug into usb on reader.

If it works rember to go back into bios and set your boot priorities as they were or how you want them , leaving usb boot first might slow down boot time.

good luck

---

### Post by Jason9 on 2010-08-13
Ok, will try the boot menu, if I can find the right key. I *have*tried setting usb as first in the boot order, though. At this point, I'm ready to just install the optical drive from an old computer. Will try, though.

---

### Post by Jason9 on 2010-08-14
Just connected an internal cd drive temporarily, works fine. Thanks, though.

---

### Post by bejinx on 2011-08-17
I just bought this mobo also with the intent of making a media center pc out of it.  

11.04 (ubunt, linux mint) would not install, 10.04 did with no problems.

***

-edit- My problem is my blue ray drive. (LITE-ON 4x Blu-ray Disc SATA Internal Optical Drive iHOS104).  Ive installed windows 7 fine with this drive, it recognizes it inside windows, plays blue ray no problem.  

When I stick a linux distro in it, it gets so far, and dumps me in a basic terminal.  Except ubuntu 10.04, it installed.  Ive tried Linux Mint 11.04, Ubuntu 11.04, XBMC Live 10.04, and all those hang up.  Stuck a spare DVD drive in it (also LITE-ON, but IDE) and they all booted up fine, and installed.  

Something with the iHOS104 is causing problems in linux, if anyone has any ideas please share, I'd appreciate it.

---

