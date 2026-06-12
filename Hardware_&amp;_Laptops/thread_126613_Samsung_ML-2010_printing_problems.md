---
title: "Samsung ML-2010 printing problems"
date: 2006-02-06
forum: Hardware &amp; Laptops
---

### Post by ZephyrXero on 2006-02-06
I'm having some weird issues trying to install my Samsung ML 2010 Laser Printer. The printer is Linux compatible and even comes with a CD that has Cups drivers and a Linux GUI installer and scripts. I know it works because I've used it before when I was running Gentoo.

First I tried simply going into the Gnome-cups configuration tool and "adding a printer". Since Ubuntu does not have a driver for it built in, I clicked Install New Driver, upon which I pulled the proper PPD file off the disc. After this it did nothing.

So next, I tried using the Linux installer that comes on the CD. For some reason I could not even run it as root because it said I had a bad interpretor and did not have permission to run the file. I checked the permissions on the file, and I should have all the permissions I could possibly need. This really made no sense to me... So then I copied the contents of the CD onto my hard drive and was finally able to run the installer. It seemed to install properly and told me that it was a sucessful install. Then I tried to print a test page once again, and nothing...

I've found that if I use the ML-200 driver that comes with Ubuntu it kind of works, but the image quality seems very poor (in comparison to past use).

Any ideas? Thanks...

**Update:**
Ok, so the main problem I'm having seems to be with halftone/dithering. The odd thing is the Ubuntu test page's dithering looks prefect, but when I go to print my file (2400 x 3150 jpeg) it looks awful. I tried printing the same file at work, using the same version of Ubuntu and the same applications (gThumb, OpenOffice, GIMP) and it printed just fine. This doesn't make any sense to me :(

---

### Post by kalinga on 2006-02-12
I've hit a similar obstacle course with my Samsung ML-1710P, though so far it's not printed anything at all.

---

### Post by ZephyrXero on 2006-02-17
I've switched to Dapper and I'm still having the same problems :(

---

