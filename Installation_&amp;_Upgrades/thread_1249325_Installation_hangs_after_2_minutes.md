---
title: "Installation hangs after 2 minutes"
date: 2009-08-25
forum: Installation &amp; Upgrades
---

### Post by electrostaticman on 2009-08-25
Fresh Ubunbu 9.04 install, right from the CD.  I select language (English), select "Install Ubuntu", and after a minute or two it just hangs.  CD stops spinning and computer needs a powerdown.

Lots of room on the hard disk, the CD image check passes as does the memory test (i've tried these two options on the CD).

What gives?  This is my first attempt at Ubuntu and I was hoping for a more pleasant experience :)

---

### Post by giftedwon on 2009-08-25
what program did you use to make the CD?  

try to burn it at a slower speed.. The same thing happened to be before

---

### Post by presence1960 on 2009-08-25
Did you [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the downloaded iso?
Did you burn it as an image to CD at no more than 4x speed? if your burning software will not allow you to choose 4x for burn speed see [here]("https://help.ubuntu.com/9.04/switching/installing-burning.html").
If the same thing happens look at [boot options]("https://help.ubuntu.com/community/BootOptions") (F4 & F6)

If that fails try the [alternate text based installer]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")

---

### Post by electrostaticman on 2009-08-25
> **giftedwon said:**
> what program did you use to make the CD?  

try to burn it at a slower speed.. The same thing happened to be before

I'll give it a shot -- although the CD integrity check passed, so I'm not getting my hopes up :)

---

### Post by dE_logics on 2009-08-25
You should verify the downloaded content...CD integrity and downloaded content verification are different things.

Do that md5 check with of the downloaded image.

Once I downloaded a Sabayon Linux image; the DVD burnt perfectly, and it's integrity was good, but it turned out that the image file failed the md5checksum.

Also we would like to know your hardware...specially your graphs chip.

---

### Post by presence1960 on 2009-08-25
> **dE_logics said:**
> You should verify the downloaded content...CD integrity and downloaded content verification are different things.

Do that md5 check with of the downloaded image.

Once I downloaded a Sabayon Linux image; the DVD burnt perfectly, and it's integrity was good, but it turned out that the image file failed the md5checksum.

Also we would like to know your hardware...specially your graphs chip.

+1

I would refrain from using direct downloads and use a bit torrent to download the iso. Torrents check during the download and insure your iso is correct.

---

### Post by electrostaticman on 2009-08-25
> **presence1960 said:**
> +1

I would refrain from using direct downloads and use a bit torrent to download the iso. Torrents check during the download and insure your iso is correct.

thanks for the tips -- I'll try the ideas above.  No, I didn't do the checksum test.  I'll download again and try.  I've tried the 'safe graphics mode' (F4) option along with booting from the CD (without installing) with same results.  Maybe it is a bad iso!

I've got a 4-year old system.  AMD 2500, 512M mem,  ATI Radeon card. 7G free on primary drive, 100G free on second drive (where Ubuntu will be going).  Can't remember offhand the details.  It's not terribly slow by any means, I wasn't expecting any problems.

---

### Post by presence1960 on 2009-08-25
> **electrostaticman said:**
> thanks for the tips -- I'll try the ideas above.  No, I didn't do the checksum test.  I'll download again and try.  I've tried the 'safe graphics mode' (F4) option along with booting from the CD (without installing) with same results.  Maybe it is a bad iso!

I've got a 4-year old system.  AMD 2500, 512M mem,  ATI Radeon card. 7G free on primary drive, 100G free on second drive (where Ubuntu will be going).  Can't remember offhand the details.  It's not terribly slow by any means, I wasn't expecting any problems.

Do the iso thing, if that doesn't work I would try the alternate text based installer.

---

### Post by dE_logics on 2009-08-25
[QUOTE=electrostaticman]ATI Radeon card.[/QUOTE]

Now THIS is a real issue...if it does not work, it's cause of this.

---

### Post by electrostaticman on 2009-08-25
[FONT=Arial][SIZE=2]Thanks for[/SIZE][/FONT][FONT=Arial][SIZE=2] all the suggestions!
My video card is an [/SIZE][/FONT]  [FONT=&quot][FONT=Arial][SIZE=2]ASUS Radeon 9200SE.  Is this a problem?

I've run the md5 check on two images that I've downloaded (1 through torrents, 1 through ubuntu.com) and both checks are fine.  1 CD burned at 12x, the other at 4x.  Both give the same results (progress bar hangs a minute into the installation).

I've tried all the options in the F4 menu, and I've gone through all of the options in F6.  Nothing seems to work.

I'll try the text based installer...
[/SIZE][/FONT][/FONT]

---

### Post by electrostaticman on 2009-08-26
ok -- the good news is that the "alternate" installer works great :)  The text-based menus worked just fine.

HOWEVER once it was done installing, I booted up the computer and BAM it hung again.  The ubuntu logo shows up and the progress indicator moves about 15% across and then it hangs.  Same "progress" as the gui-based installer.

I rebooted it in the "recovery mode" and the last few lines before it hangs:

Linux video capture interface: v2.00
bttv: driver version 0.9.17 loaded
bttv: using 8 buffers with 2080k (520 pages) each for capture
bttv: Bt8xx card found (0)
bttv 0000:00:0e.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
bttv0: Bt878 (rev 17) at 0000:00:0e.0, irq: 17, latency: 32, mmio: 0xbf800000
bttv0: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]

Would this mean Ubuntu doesn't like my video card?

thanks for all the suggestions so far!

---

### Post by electrostaticman on 2009-08-26
ok -- not sure if this helps, but if I boot off the CD to repair an install, I can eventually get a prompt.

lspci |grep Radeon gives:
01:00.0 VGA compatable controller: ATI Technologies Inc RV350 AQ [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AQ [Radeon 9600] (Secondary)

Does this mean it can see my video card, and it's hung on something else?  Aside from my card being a 9200SE (not a 9600...is it just a generic driver?) I'm at a loss here.

---

### Post by tal007 on 2009-08-27
I ran into a similar problem. My initial guess was defective CD, but later I found out that my unused disk space was not large enough. After I cleaned my disk using a utility called zap.exe, everything back to normal. You have to make sure that you have enough unused space not used by other OS.

---

### Post by electrostaticman on 2009-08-27
Figured it out.  woo-hoo!

I had forgotten about a PCI card that was in my machine: a VisionPlus DVB satellite tuner card.  Apparently, Ubuntu doesn't like this card whatsoever, so it hangs when it detects it.

As soon as I removed it, everything boots wonderfully.

Thanks all for the suggestions -- now I just need to find a way to keep my PCI card in my machine without ubuntu hanging on startup.  It still works fine with Windows XP, so I'm sure there's a solution for ubuntu...

---

### Post by electrostaticman on 2009-08-27
I might as well add to this thread, maybe it will help someone....

the EEPROM in my VisionPlus card is pooched:
[http://www.linuxtv.org/wiki/index.php/Twinhan_VP-1020A](http://www.linuxtv.org/wiki/index.php/Twinhan_VP-1020A)

all fixable though!

---

