---
title: "Asus M3n78-emh"
date: 2008-05-13
forum: Hardware
---

### Post by campbecf on 2008-05-13
Just wondering if anyone knows about the compatability of the:
ASUS M3N78-EMH HDMI AM2+/AM2 NVIDIA GeForce 8200 HDMI Micro ATX AMD Motherboard

Will the HDMI out work from that motherboard in linux?

Thanks

---

### Post by PhatKat on 2008-05-18
Hmm it's gonna be a toss up between GF8200 and 780G for my next rig so i am  interested in this too :P

---

### Post by ias2 on 2008-06-03
I've got this motherboard last week... sadly, the onboard (too) new NVIDIA GeForce 8200 chipset does'nt work at all with Ubuntu (and with Linux in general I think)... no LAN, no sata drive (resolvable), weird sound, no gpu acceleration ecc. ecc. (USB is ok!)
After a lot of googling, the sata disk now work with Ubuntu, but nothing more...
The motherboard is an excellent (and very interesting) piece of hardware, my idea was to build an home made htpc, using the Thermaltake DH101 case (already bought with all the remaining hardware), but I cannot use Ubuntu on it... for now :)

---

### Post by PhatKat on 2008-06-03
Hmm i think i read somewhere that it works with Fedora 9

---

### Post by flecki on 2008-06-04
Hi All,

i run the M3N78-EMH HDMI with Mythbuntu 8.04.

Installation was possible using information from this one:[http://ge.ubuntuforums.com/showthread.php?p=4951554]("http://ge.ubuntuforums.com/showthread.php?p=4951554")

Open Issues:

SATA Disks running in IDE Mode and underperform horribly - i read this is getting better with BIOS 0409 but i can´t install it since it refuses to detect my PCI Cards(Satelco Easywatch DVB-C and a 3Com NIC) - so it´s 0222 till now

Onboard LAN is not recognised - i hear this is part of kernel 2.6.25 so i am currently using an old 3Com Card

Mythbuntu with SD-channels runs stable but HD is not possible right now(recording yes - playing NO). I am using NVIDIA closed-source driver 173.14.05 because 169xx as included in Ubuntu 8.04 won´t recognise the onboard graphics..

With my Toshiba 47Z3030 LCD running 1920 x 1080 50 Hz via HDMI picture looks fine to me - sound is OK over SP/DIF optical with daughter board but only stereo or Dolby 5.1

Since my Athlon 5400+ 2,8 Ghz can´t play HD which i hear is possible on older versions of Mythbuntu with less CPU-power i guess we´ll have to wait a while for mature BIOS and drivers till this bayby runs smooth.

@ias2 - per coincidence i also use the thermaltake case with 2 Samsung F1 750 GB disks - make sure you place some vibrance isolation under the disk cage or the sound will drive you nuts sicne they forgot to decouple the cage from the rest of the case and the feet are just for good looks. 
"sudo hdparm -m 128 /dev/hda" and "sudo hdparm -m 128 /dev/hdb" will help but not solve the problem and it makes the disk even slower as it already is because of IDE mode

Lucky me has a friend who knows his ways around Linux - if not i would be looking at a pile of hardware wasting power :-)

By the way...it draws 60 Watts of power and a maximum of 100 Watts when both Cores on full load

---

### Post by ias2 on 2008-06-09
For flecki: thanks for your suggestions; I have only 1 SATA2 320GB Maxtor HD on my system and the noise is very low; to make it run with Ubuntu 8.04, I've added all_generic_ide to the kernel boot options, but performances are not much high...
I use a second machine as media server, an Ubuntu server 8.04, with an Athlon 64, three 750GB Maxtor SATA2 disks, tied togheter with UnionFS, 1 320GB Maxtor ATA disk as boot and system, Twonky UPnP media server for UPnP streaming (Linux version, installed with help of 32bit support libraries for Ubuntu). The server's disks noise is enough high to be a nuisance, but the server is closed in a little service environment, so is not a problem.
All I need now, is a working kernel version for my ASUS motherboard... :)

---

### Post by Gezza on 2008-06-13
Hi to all,
I must say, for starters, that i do not use Ubuntu.
That said, i do have this Motherboard running Linux (PCLinuxos 2008).
I have had a lot of experiments with this board and at the moment there is only one way to get this beast going.
My setup is as follows,
1...IDE boot drive 250GB (smallest i have)
2...Sata hard drive 750GB + 330Gb (Data drives)
3...Sata dvd/cd
4...8GB ram
Under these condition the system works very well. Very fast.
It is the only way i have found, to date, to get a satisfactory operation with this Motherboard.
All Sata drives are recognised, so i have plenty of data space.
This does work. 
Gezza

---

### Post by ias2 on 2008-06-15
Hi Gezza,

  I'm glad to know about your success with this motherboard and PCLinuxOS! Please give us more details! You can use the onboard LAN? The onboard video card can be used at full speed? What about the digital audio? Thanks!

---

### Post by Gezza on 2008-06-15
Hi guys,
Latest news.
The 2.6.25 kernel will support the AHCI system.
At the moment, I have always thought the kernel and initrd had all the support necessary for booting the system.
This does not seem to be the case.
If you create a /boot partition on an IDE drive and put all other files on a Sata drive, the system will not boot, kernel panic...
If you require a large /home folder the best way is to put / on a small IDE drive say 20MB and /home on the Sata system.
This works very well. The IDE drive does not need to be ultra fast.
At this time i have put a 1G network card in as the on board network is no even recognised.
You do need to install the AMD 64 4GB kernel to get all ram above 4 GB operational. I did not look into the network side of the 2.6.25 kernel,but i would think it will support this board.
As an asside, can anyone tell me why we need AHCI when we have IDE SCSI and SATA. IS this a Windoze thing?
Gezza.
Right, The question about the sound. I am on the machine noe and have set up the sound system paying a DVD and it sounds OK. But i do not hear a difference between the 97 series sound and this advance sound,but then i am approaching 72 so my hearing is not as good as you 20-40 year old people.
Hope this helps
Gezza

---

### Post by Gezza on 2008-06-17
Hi to all,
I have just tried to play a DVD, and although it works it does NOT work well. When i try to go full screen with it i get pixelatition. and it is hard to make out the images properly.
This is not normal for a properly recognised video card.
Tomorrow i am changing the boot IDE drive to a 40GB one. This will release the 250Gb drive for some other tests.
From previous messages, you will see that we will have to wait for 2.6.25+ to get everything working.
I hope this kernel surfaces soon.
All the best
Gezza

---

### Post by flecki on 2008-06-17
Hopefully we do also get a more mature BIOS till 2.6.25 - 409 does not recognise my pci-cards any more where 222 does.

In some forums they say if you plug in a card in slot 2 it won´t be recognised and it will also cause the board to not recognise the slot 1 card. If only one card in slot 1 is used everything should be fine in 409...in 222 2 cards work without any problems.

ASUS is getting worse each year...

---

### Post by coyote2 on 2008-06-25
Cracking ubuntu 8.04 to work with latest nVidia 8200 chipset motherboard
[http://coyotesg.blogspot.com/](http://coyotesg.blogspot.com/)

Upgraded my 2 years old nVidia 6150 motherboard to the new nVidia 8200 motherboard recently.

Using the latest ubuntu 8.04 installation, Hardy Heron's 2.6.24 kernel simply don't work with the new chipset. The basic SATA2 controller, onboard LAN & the onboard 8200 3D chip are all not supported under the 2.6.24 kernel. Although ubuntu 8.04 can be installed with a all_generic_ide option, performance should be degraded substantially & also, no amount of tweaking with the settings can get the onboard LAN & onboard 8200 3D chips to works

The nice surprise is that, Fedora 9's 2.6.25.5 kernel works flawlessly with the new 8200 chispet. SATA2 controller & onboard LAN. The onboard 8200 3D chip requires the latest nVidia 173.14.5 to work though.

It was understood that nvidia 173.14.5 driver will support the 8200 3D chip but will not work with the 2.6.24 kernel in ubuntu 8.04.

So, here is my attempt to install customer kernel in uBuntu to work with my latest motherboard acquisition.

Following the guide from

[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

I've compiled & installed the 2.6.25 kernel in ubuntu.

And with the new kernel , one can finally remove the 'all_generic_ide' option from the kernel option to take advantage of the new SATA2 controller. Edit the grub boot options as follow:

sudo vi /boot/grub/menu.lst

And to install the latest nVidia 173.14.5 driver, one need to boot to native console to install.

In Fedora, one will edit /etc/inittab to change run level from 5 to 3 to boot to native console.

In ubuntu however, one needs to issue

sudo /etc/init.d/gdm stop

then do

sudo sh NVIDIA-Linux-x86-173.14.05-pkg1.run

to install the latest nVidia driver.

Upon reboot. Viola, finally have the nVidia driver working with the 2.6.25 kernel.

According to the Master Kernel Thread at [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

Troubleshooting:

--------------------------------------------------------------
Q. My High Definition sound (Azalia) does not work with the new kernel!:

A. This took me a long time to figure out because I didn't have sound either. You have to enable the Intel HD (Azalia) module in Advanced Linux Sound Architecture, even if it isn't Intel.

--------------------------------------------------------------
So, after recompiling the kernel enabling Device Driver, Sound, PCI Device, Intel HD Audio option, the sound is ok & the OS is perfect now for my nVidia 8200 chipset motherboard. 


-----------------------------

Now, I have a last problem. Disc access is terribly slow with the custom kernel. Anyone can point me to the right direction to fix that with the custom kernel?

---

### Post by ias2 on 2008-07-10
The versio 0507 is ready to be downloaded from here:

[http://support.asus.com/download/download.aspx?SLanguage=en-us&model=M3N78-EMH%20HDMI](http://support.asus.com/download/download.aspx?SLanguage=en-us&model=M3N78-EMH%20HDMI)

Notice the 0506 version, released in the same day...
Hope this helps to solve some problems with PCI cards...

---

### Post by flecki on 2008-07-11
Installed 0507 - PCI Card Problems are gone for good and the kernel now recognises the disks as sata-disks.

For the onboard LAN we´ll have to wait till 2.6.25 as far as i know.

---

### Post by tobiz on 2008-08-11
I now have the have the SATA discs working by setting BIOS to SATA Mode and adding all_generic_ide to boot with kernel 2.6.24-16-generic. I also have the nvidia on board controller working by installing 173.14.12 from Nvida web site using their instructions, 173.14.09 from Ubuntu did not work for me.  On board networking not working.

---

### Post by Bert75 on 2008-10-04
Just tried M3N78-EMH HDMI with latest Beta Ubuntu CD (8.10 I think) and the boot process failed when X server started. I am no specialist, but it seems Gforce 8200 isn't supported yet :-(
As a consequence, I have not been able to confirm that SATA and Ethernet now work correctly (with decent perf fo SATA).

---

### Post by jbman on 2008-10-07
did you try it with alpha 6 or something else?

I have not tried the ethernet since i dont use it, but the sata works fine with the pci string

---

### Post by flecki on 2008-11-11
8.10 with bios 507 works perfectly for me. 

onboard lan recognised
SATA disk running 10 times faster in read (remove pci-string !!)
even the 177.80 nvidia drivers were suggested by the system
there are still some sound issues with mythbuntu but i am a happy camper for now :-)

---

### Post by rstuart on 2008-11-17
What are the Mythbuntu issues you have expirenced?

---

### Post by flecki on 2008-12-03
....had to go back to stereo output but passthrough is still working. Something with ALSA i guess but i am too inexperianced to fix it so i wait on a newer driver release. 

There are some threads about it already

---

### Post by ias2 on 2009-01-01
Hello to everybody and happy new year to all Ubuntu enthusiasts. I'm back to work on this motherboard.
I've updated the BIOS to 0602 version, installed the drivers NVIDIA ver. 177 and activated the Compiz cube + a ton of graphic effects. The system is up, running and stable; the performances are good video and audio (stereo) works without any problem. Soon i go to test the HDMI video output performances and, when I can put my hands on a  "S/PDIF OUT COA+OPT" Asus module, the HD audio output.
Globally, the performances are much better than the previous installation with Vista Home Business 64, so I have good hopes to finally make a decent HTPC system with this board.

---

### Post by ias2 on 2009-01-01
One last thing: during the installation, the process crashed with an error I/O on the CDROM. I tried to burn several CD copies, downloading the ISO image from different locations, without success. After a little googling, I discovered that many other users encountered this problem. I solved everything making a bootable USB stick which I have used to install the system without problems.
For making the usb boot stick, I used unetbootin (Windows version) which is an excellent utility imho.

---

### Post by flecki on 2009-01-12
> **ias2 said:**
> Hello to everybody and happy new year to all Ubuntu enthusiasts. I'm back to work on this motherboard.
I've updated the BIOS to 0602 version, installed the drivers NVIDIA ver. 177 and activated the Compiz cube + a ton of graphic effects. The system is up, running and stable; the performances are good video and audio (stereo) works without any problem. Soon i go to test the HDMI video output performances and, when I can put my hands on a  "S/PDIF OUT COA+OPT" Asus module, the HD audio output.
Globally, the performances are much better than the previous installation with Vista Home Business 64, so I have good hopes to finally make a decent HTPC system with this board.


If you can´t get one of those S/PDIF boards - i got one spare (orderd 2 which took me half a year to get it delivered) - good luck with the board and keep us updated on your progress

---

### Post by ias2 on 2009-01-16
Thanks flecky, but the  module "COAX IN + COAX OUT" is already in my hands and  "COAX + OPT" is on the way :)
In a few days, I will watch my first movie with my Ubuntu media center, and I will post my impressions here!

---

### Post by ias2 on 2009-01-23
Hi flecky, what kind of S/PDIF board do you have? If it's a COAX + OPTICAL out module, then it can be useful for a my friend with a system with the same motherboard. If you want sell the module, please send me an e-mail to "ias2 at libero dot it"

---

