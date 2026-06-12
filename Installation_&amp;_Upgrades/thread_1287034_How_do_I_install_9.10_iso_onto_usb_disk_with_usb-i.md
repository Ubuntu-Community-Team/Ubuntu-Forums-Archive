---
title: "How do I install 9.10 iso onto usb disk with usb-imagecreator?"
date: 2009-10-09
forum: Installation &amp; Upgrades
---

### Post by frecon on 2009-10-09
I want to install ubuntu netbook remix 9.10 beta but it's only delivered in iso format and the official [guide to install onto usb memory]("https://help.ubuntu.com/community/Installation/FromImgFiles") does only work for img-files. What to do? I googled for answers and tried using AcetoneISO2 and UltraIso to convert it to img. I tried system->administration->create usb-startup disk. I also tried just renaming the file to img. Nothing worked. This is so dissapointing that canonical(?) released a system intended to be installed with an usb memory but it can't be created. It's clearly no one think this through. :confused: ehh?

---

### Post by mgol on 2009-10-09
Wouldn't USB Startup Disk Creator work? Of course, if You have access to any computer with an Ubuntu (at least 8.10) installed.

---

### Post by frecon on 2009-10-09
> **mgol said:**
> Wouldn't USB Startup Disk Creator work? Of course, if You have access to any computer with an Ubuntu (at least 8.10) installed.

No, I've already tried that.

---

### Post by mgol on 2009-10-09
So, what error messages You experienced in both cases?

---

### Post by frecon on 2009-10-10
> **mgol said:**
> So, what error messages You experienced in both cases?

No error messages. It simply doesn't boot from the usb memory. It can'&#7831; be something wrong with my usb memory or the process because I can I install unr 9.04 (img) with no prob.

---

### Post by ram2008 on 2009-10-11
[SIZE="3"]If you have access to 9.04, you can use the Create USB utility to put 9.10 on your USB drive using the ISO file.  However, you may be disappointed with how well it works.  I ran 9.10 from my USB drive a couple of days ago and was very frustrated with the very slow boot time.  It took 5.25 minutes to get to the desk top, so I've abandoned the idea.  That's way too long.  Maybe you'll have better luck than I did.[/SIZE]

---

### Post by frecon on 2009-10-11
> **ram2008 said:**
> [SIZE="3"]If you have access to 9.04, you can use the Create USB utility to put 9.10 on your USB drive using the ISO file.  However, you may be disappointed with how well it works.  I ran 9.10 from my USB drive a couple of days ago and was very frustrated with the very slow boot time.  It took 5.25 minutes to get to the desk top, so I've abandoned the idea.  That's way too long.  Maybe you'll have better luck than I did.[/SIZE]

Didn't you read my post? Both you and mgol seem not to. I've tried usb creator with no luck. It burns the usb memory with no problem but my netbook doesn't boot from it.

Any other ideas?

---

### Post by Mighty_Joe on 2009-10-12
If it is an ISO, you should be able to burn it to a CD.  Boot the CD and if it has the USB Creator, use that to get it on the USB drive.  If not, you could either do a full install to the USB drive (if your drive is big enough) or try to install the Creator from the repository and then use it.
Another option is [UNetBootin]("http://unetbootin.sourceforge.net/"), which takes a live ISO and creates a bootable USB drive.

---

### Post by shiningkenmonster on 2009-10-12
yes, i used to use Jaunty Jacklope netbook remix for many months.

I am using Hardy Heron. yes, the usb-creator doesn't work for some odd reason. I believe its a bug. It did work well on Jaunty.

I also sudo dd the command line and successfully uploaded the iso into the usb flash drive. (the same flash drive that worked with Jaunty Jacklope netbook remix)

for some reason when i turn on the power with the usb flash drive and select it to boot it up. It shows up with a black screen with a white text saying "No OS Found"

it must be some odd bug. I never got this with Jaunty.

btw, ImageWriter only works with .img files, not with .iso files

the other option is download and use UNetBootin. If you want, and if you have access to a Windows machine. you can download the windows version and upload that iso onto the flash drive. and presto it'll work.

---

### Post by frecon on 2009-10-12
> **Mighty_Joe said:**
> If it is an ISO, you should be able to burn it to a CD.  Boot the CD and if it has the USB Creator, use that to get it on the USB drive.  If not, you could either do a full install to the USB drive (if your drive is big enough) or try to install the Creator from the repository and then use it.
Another option is [UNetBootin]("http://unetbootin.sourceforge.net/"), which takes a live ISO and creates a bootable USB drive.

Thanks for taking the time to answer me. UNetBootin was able to successfully burn the ISO but when I try to boot from the usb memory it doesn't work. I tried UNetBootin in both Ubuntu 9.04 and in Windows XP. To round everything up I've tried UNetBootin, USB-Creator (in Ubuntu), convert to img and use imagewriter and W32-image-writer (in win xp). After all this testing there must be something wrong with the UNR 9.10 beta iso. Where should I file bugs?

---

### Post by shiningkenmonster on 2009-10-12
not sure what is your computer level is, but....

did you upload the correct iso files? or did you covert the iso into img and use unetbootin? we all assume you uploaded the untouched iso file.

did you hit the right key upon the BIOs startup screen? and select the load USB-Device or Removable-Drive? which ever indicates your USB flash drive.

How old is your pc?

If your pc is really old. Your BIOs are outdated and it won't let hit the correct key with the "Boot with" screen.  and you will need to flash your BIOS to take advantage of this features. (if you can, you don't need to flash your BIOS)

btw, i've read on ubuntumini.com blog that the author wrote some USB flash drives won't live boot with ubuntu. I don't know if it is correct or not, but many users did comment about what usb flash drives they have used and listed the brand and model number that worked.

Did you try another usb flash drive?

---

### Post by Mighty_Joe on 2009-10-12
> **shiningkenmonster said:**
> btw, i've read on ubuntumini.com blog that the author wrote some USB flash drives won't live boot with ubuntu. 

I've seen [others complain ]("http://ubuntuforums.org/showthread.php?t=1266014")about the same thing, but haven't seen any proof (note the fellow in that post actually had a BIOS setting problem).  The one drive I had a problem with didn't have a partition table, which turned out to be a known bug with [the USB Creator]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/277865")

---

### Post by frecon on 2009-10-12
> **shiningkenmonster said:**
> 
did you upload the correct iso files? or did you covert the iso into img and use unetbootin? we all assume you uploaded the untouched iso file.

I used ubuntu-9.10-beta-netbook-remix-i386.iso. MD5 checked. The only time I converted it was when I tested imagewriter (which only accepts img files). 

> **shiningkenmonster said:**
> 
did you hit the right key upon the BIOs startup screen? and select the load USB-Device or Removable-Drive? which ever indicates your USB flash drive.

Yes. I know how to boot. I've booted UNR 9.04 on the same netbook with no problem.

> **shiningkenmonster said:**
> 
How old is your pc?

If your pc is really old. Your BIOs are outdated and it won't let hit the correct key with the "Boot with" screen.  and you will need to flash your BIOS to take advantage of this features. (if you can, you don't need to flash your BIOS)

The netbook I'm using is Asus 1005HA. It was released this summer. I have also tried booting from my stationary computer which has a mb that released spring 2009.

> **shiningkenmonster said:**
> Did you try another usb flash drive?
No. But I don't think there's a problem with the usb memory. I've successfully booted unr 9.04 from it.

Have anyone of you tried burn unr 9.10 beta onto a usb memory and successfully booted? Please try.

Btw, where do I file bug reports?

---

### Post by Mighty_Joe on 2009-10-12
> **frecon said:**
> Btw, where do I file bug reports?

The link is at the top of the page: [launchpad.net]("https://launchpad.net/").  [Read this]("https://help.ubuntu.com/community/ReportingBugs") first.

---

### Post by Mighty_Joe on 2009-10-12
> **frecon said:**
> 
Have anyone of you tried burn unr 9.10 beta onto a usb memory and successfully booted? Please try.


I just downloaded UNR 9.10 Beta, used UNetBootin to copy it to an Imation 1GB USB flash drive and booted it on an HP desktop.  Works fine.  I'm posting from it now.

---

### Post by frecon on 2009-10-12
> **Mighty_Joe said:**
> I just downloaded UNR 9.10 Beta, used UNetBootin to copy it to an Imation 1GB USB flash drive and booted it on an HP desktop.  Works fine.  I'm posting from it now.

Ok great.

I have installed 9.04 and then upgraded to 9.10. I can't bother to give this issue more time so I'll just wait to when the final is out (hopefully as an img).

---

### Post by hardkorek on 2009-10-18
I have the same problem. I was trying with imagewriter and dd command. 
No such problem on jaunty nbr. 
What is bug number on launchpad?

---

### Post by frecon on 2009-10-18
> **hardkorek said:**
> I have the same problem. I was trying with imagewriter and dd command. 
No such problem on jaunty nbr. 
What is bug number on launchpad?

I didn't file the bug. I was too lazy. But please create it yourself.

---

### Post by Mighty_Joe on 2009-10-19
> **hardkorek said:**
> I have the same problem. I was trying with imagewriter 

Imagewriter is for .img files.  It doesn't work with .iso images.
As I posted above, I used UNetBootin and it worked fine.

---

### Post by sk8dork on 2009-10-27
just chiming in. i didn't necessarily have the same problems booting, but i found this thread while doing research as to what i should do with the UNR iso i was downloading. wtf, why didn't they make a UNR img file if they're going to suggest it in the instructions? anyway, i used unetbootin in windows (version 312 i think, old one i have always had) and it worked beautifully. i booted to it and am installing right now. i used a patriot mini-II xporter 4GB flash drive and am installing to my acer aspire one, so i can't speak to exactly what the problem was for the OP.

---

