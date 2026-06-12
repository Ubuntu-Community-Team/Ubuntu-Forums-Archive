---
title: "HP ProLiant Microserver £100 cash back."
date: 2012-03-30
forum: Hardware
---

### Post by rk0r on 2012-03-30
Hi 

Has anyone bought a HP ProLiant Microserver with the £100 cashback offer from HP ?.
I am thinking to buy one of these little servers and kit it out for home backup, has anyone got one or had experience with one ?


Would there be a lot of configuration involved for setting up SATA drives on Ubuntu Server edition ? Or would you recommend using an alternative OS for media storage server backup.

Any information would be great.

---

### Post by Magnificent 7 on 2012-05-10
Hi,

probably replying way too late for you, but just purchased two of these for small web-hosting environments attached to ADSL2+ lines.

Information on the RAID controller was difficult to get from the various fora, and ambiguous. Turns out that it is a PDC software RAID, rather than a true hardware device. As a consequence, both /dev/sda and /dev/sdb of a 2-disk RAID 1 array are visible in an "fdisk -l", in addition to the /dev/mapper/xxxx device behind which the software RAID hides. That said, some claim that the CPU overhead is minimised by a dedicated AMD FakeRAID chip on the mobo but I've no way to test this.

Most commentators claim that the controller can only do RAID 0 and 1, but additional options for RAID 10 and JBOD were also available via the BIOS setup. I was successful using RAID1 under Ubuntu, with the gigabyte block set to OFF and FULL initialisation. Having bought three 1TB disks to configure as a maximally-resilient RAID1 array, the BIOS setup would only allow a maximum of two to be configured in RAID1.

Many posters to Internet fora use WHS and its variants without specifying this when they post, so they would have pressed F6 to load an HP RAID driver for Windows at the very beginning of a Windows Server installation. After that point, I'm presuming that the controller appears to the OS as equivalent to a hardware RAID and there is no further access to the individual physical disks. They report no problems, leading to confusion when Linux/Ubuntu users post their RAID woes.

HP's embedded driver documentation claims that the controller can't be used in a Linux environment, when this is in fact not true; I successfully installed Ubuntu Server 12.04 LTS 64-bit and it picked up and supported the PDC Software RAID device 'out of the box'.

It was second time lucky, the first attempt having failed at the stage of installing GRUB2 to the RAID. You have to note down the string describing the RAID mapper device at the partitioning/formatting stage, which is of the form 'pdc_zyxwvutsrq' or similar, and append it to the default /dev/mapper target offered by GRUB2's installer, with a partition number (i.e. change /dev/mapper to /dev/mapper/pdc_zyxwvutsrq1 if you only have one partition configured as '/').

My first attempted install failed because I assumed that the RAID device should appear as /dev/sda and changed the GRUB2 installation target to /dev/sda from /dev/mapper. GRUB2 then trashed the special RAID sectors set up on /dev/sda, in addition to making the contents of the two drives inconsistent. After that point the RAID mapper device could not be selected as a target regardless of how far I backed up, and I had to delete, recreate and re-initialise the RAID device in the BIOS to recover the situation.

To finish this report/summary, most Ubuntu-ers using this box as a NAS, small webserver or testing environment tend to do so with Ubuntu's built-in software RAID in RAID5, which I'll do with my second box once HDD prices become sensible again. The current two-disk RAID1 configuration of the first MicroServer is really aimed at finding out whether the BIOS is able to pick up and handle any problems on Ubuntu's behalf, and in the case of disk failure whether the BIOS can do a successful rebuild.

As I was browsing the fora, a few users were praising the remote management card. Looking this up, it costs only GBP60 (May 2012) so I may include this once I have ironed out the other wrinkles.

---

### Post by kamaji792 on 2012-05-16
Hi,

Have been using one of these at home as a file server and small development server for me to play with.  It is one based on an Athlon processor.  It was easy to set up and and has worked a treat.

So good in fact I am replacing a failed server in a small office at the moment.  This system uses an AMD processor.  Again the installation is going well.

I can't say if any other OS would be better for a file server I have pretty much only used Ubuntu for servers.  The home and work ones will have Samba for file serving; a LAMP stack for database work and Getmail/Dovecot system for mail.  They are hard to beat at the price and have for some time come with £100 cash back in the UK.

k

---

