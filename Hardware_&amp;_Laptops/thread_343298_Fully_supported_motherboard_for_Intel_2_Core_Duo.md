---
title: "Fully supported motherboard for Intel 2 Core Duo"
date: 2007-01-21
forum: Hardware &amp; Laptops
---

### Post by danpre on 2007-01-21
Hi,

I was searching ubuntuforums and I see a lot of problems with motherboards for Intel 2 Core Duo processor.

I would like to ask anyone who is using a one of motherboards listed below if motherboard is fully supported with ubuntu (Dapper Drake or Edgy Eft)

1. Gigabyte GA-8I945GZME-RH Intel 945G BOX
2. Gigabyte GA-945GMF-S2 Intel 945G BOX
3. Asus P5L-MX Intel 945G
4. Gigabyte GA-946GM-DS2 Intel 946GZ BOX
5. Intel DG965SSCK GLAN bulk
6. Asus P5B-VM Intel G965
7. Asus P5LD2-VM DH/C Intel 945G
8. Gigabyte GA-965GM-S2 Intel G965

I will be running Ubuntu as the host system and with vmware server: windows xp pro (for my desktop needs - ERP and users support) and windows 2000 server (Active Directory backup domain controller)

So I don't need (computer will be located at server room):
good graphic card (onboard is enough)
sound 
firewire
usb controllers

I need:
Intel 2 Core Duo processor
2GB RAM dual channel (I think: 2x Kingston DDR2 1GB 667MHz CL5)
gigabit network card (onboard is enough)
possibility to connect ide cdrom for Ubuntu install
possibility to connect: two  Seagate 160 GB Barracuda 7200.10 (8MB, Serial ATA II) hard drives: one for ubuntu and win xp pro, second one for win 2000 server

Please post me an info if you have managed to get Ubuntu work on one of this motherboards.

List is sorted 1 cheapiest 8 expensive - so lower numer is better :)

DANIeL

---

### Post by PilotJLR on 2007-01-21
I have an Intel DG965WH board, which should be very similar to the Intel branded once you have there. It has a Marvell PATA chipset, and will NOT install from an IDE cdrom.
I installed Edgy on this machine with a USB CD-ROM drive. Once it is installed, I applied the Marvell PATA module, and it works beautifully!

Intel branded boards are very good. If you are okay with the USB install, that is.

---

### Post by RandomJoe on 2007-01-21
The primary issue is the chipset used for the PATA drives.  Intel has left PATA out of their chipsets, so the vendors are selecting various ones.  The one that most people are having problems with is the Jmicron PATA chipset.  It is _supposed_ to be supported, but it appears to be rather flaky in performance.

I would assume this means if you can use a SATA CD/DVD drive you could sidestep the issue entirely...

Your other option is to get a board that uses a different chipset.  I bought an ASUS P5N32-SLI SE Deluxe, which uses the nVidia nForce 4 chipset for everything and works just fine OOTB.  This particular board is higher-end, but there are cheaper models with the nForce chipset as well.  (Of course, there are different nForce versions as well, I can't say they ALL work fine, but the nForce 4 does here.)

---

### Post by danpre on 2007-02-09
I have new computer working.

I have bought Intel DG965SSCK GLAN bulk motherboard.

There was a problem only with CDROM connected via IDE - ubuntu doesn't recognize it.
So I have installed Ubuntu 6.10 Server AMD64 via external USB CDROM.
After installation CDROM still doesn't work - but I don't care - a have made installation of WINXPpro and WIN2000ser with iso images on vmware server.

Both SATA disk are working ok.

DANIeL

---

### Post by robenroute on 2007-02-09
Avoid 965-based boards for the time being. Feisty should be able to deal with the SATA/PATA problems of these boards. If you can hold your Ubuntu breath (you could install ZenWalk until 7.04 comes out), buy one now. If not, 975- or 945-based boards would be better. Of course, you could always juggle a wee bit with an external CD/DVD player....

---

### Post by guerby on 2007-02-10
I just built a mini-PC system with a micro-ATX format Gigabyte GA-965GM-S2 motherboard, Core 2 Duo 2.4 GHz, Seagate SATA drive and Samsung SH-S183A SATA combo cd/dvd writer (yes! no more IDE cables :).

Feisty herd 3 amd64 installed successfully from (SATA) CD, recognized the built-in Gbit ethernet, chose xorg vesa driver. I activated post install xorg i810 (built-in Intel  GMA X3000 graphic card) and it seems to work (1400 FPS for small window glxgears -printfps). 

Only problem so far is that my LCD is 1680x1050 and for now I can't get above 1280x1024 on it (with vesa and i810).

I'm confident that the situation will get better ASAP since Keith Packard and a bunch of cool xorg hackers are working at Intel now, see:

[http://intellinuxgraphics.org/](http://intellinuxgraphics.org/)

I'm discussion with Canonical support on the LCD resolution issue (I'm a paying customer :), they told me they'll open a launchpad bug since feisty isn't officially supported yet (I provided a bunch of config and log files).

---

### Post by guerby on 2007-02-11
Answering myslef, searching a bit more I found this:

[http://www.redhat.com/archives/nahant-list/2006-August/msg00160.html](http://www.redhat.com/archives/nahant-list/2006-August/msg00160.html)

Which indicates OpenSuSE has the problem fixed by default.

Here is what I did on my feisty box:

1/
apt-get install 915 resolution

2/
915resolution -l
=> pick a mode you want to overwrite

3/ edit /etc/default/915resolution
change the mode and X, Y, for me:

MODE=3a
XRESO=1680
YRESO=1050

4/ Edit /etc/X11/xorg.conf and add "1680x1050", for me:

Modes "1680x1050" "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"

5/ do:
/etc/init.d/915resolution start
/etc/init.d/gdm stop
/etc/init.d/gdm start

Et voila, 965G 1680x1050 working on Feisty Herd 3.

---

### Post by Betelgeuse on 2007-03-27
> **guerby said:**
> I just built a mini-PC system with a micro-ATX format Gigabyte GA-965GM-S2 motherboard, Core 2 Duo 2.4 GHz, Seagate SATA drive and Samsung SH-S183A SATA combo cd/dvd writer (yes! no more IDE cables :).

Feisty herd 3 amd64 installed successfully from (SATA) CD, recognized the built-in Gbit ethernet, chose xorg vesa driver. I activated post install xorg i810 (built-in Intel  GMA X3000 graphic card) and it seems to work (1400 FPS for small window glxgears -printfps). 

Only problem so far is that my LCD is 1680x1050 and for now I can't get above 1280x1024 on it (with vesa and i810).

I'm confident that the situation will get better ASAP since Keith Packard and a bunch of cool xorg hackers are working at Intel now, see:

[http://intellinuxgraphics.org/](http://intellinuxgraphics.org/)

I'm discussion with Canonical support on the LCD resolution issue (I'm a paying customer :), they told me they'll open a launchpad bug since feisty isn't officially supported yet (I provided a bunch of config and log files).

Hi,
I'm planning to build a new PC for myself and I was thinking about buying GIGABYTE GA-965GM-S2 or Intel G965WH mainboard. I want intel graphics because intels supports free software so I should buy from them instead of buying ATI or Nvidia. 
Both mainboards are nearly the same but I consider buying intel E6300 cpu so I may want to play with a little bit overclocking too. With intel mainboards, there is no overclocking option.  So, now gigabyte mainboard is top of my list with intel is the second choice. Can you tell us more about your experience with that mainboard? I'll build my new PC at the end of this month and I think I'll use Kubuntu 7.04 on it.

---

### Post by rbm0307 on 2007-04-02
> **RandomJoe said:**
> The primary issue is the chipset used for the PATA drives.  Intel has left PATA out of their chipsets, so the vendors are selecting various ones.  The one that most people are having problems with is the Jmicron PATA chipset.  It is _supposed_ to be supported, but it appears to be rather flaky in performance.

So, this issue is NOT related to the type of processor installed on the board -- like Pentium D, Celeron or Core Duo???

> **RandomJoe said:**
> I would assume this means if you can use a SATA CD/DVD drive you could sidestep the issue entirely...

I bought an ASUS P5B-VM motherboard and Silverstone enclosure used this weekend and don't have the luxury of changing the mobo.  I tried the Ubuntu Edgy LiveCD on the system before committing to the purchase and it booted and ran fine.  The original owner was using a Core Duo E6600, SATA-attached Pioneer DVD/CD and SATA disk (although I believe this had no affect). So, because the system ran as LiveCD mode successfully, can I assume that I may be able to sidestep the issue if I invest in a SATA DVD instead of PATA (IDE) DVD?

Thank in advance.....

Robert

---

