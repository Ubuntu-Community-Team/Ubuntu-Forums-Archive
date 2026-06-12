---
title: "Audio and HeadPhones on Fujitsu Siemens v3515 [solved]"
date: 2007-07-13
forum: Hardware &amp; Laptops
---

### Post by santoxyz on 2007-07-13
Hi guys, i'm running 7.04 (xubuntu) and i had troubles with audio.

My laptop has a VIA chipset (VN896)  that have an integrated Audio chip of the Intel/Realtek/Via/Conexant family, the "High Definitio Audio Controller (rev. 10) " - the alsa kernel module modprobed ( lsmod |grep snd ) is  ' snd_hda_intel ' . 


After standard installation i had sound (some people have absolutly no sound)... but when i plugged my headphones... integrated speakers continued to speak !!!! 

This is NOT Good... 

This is what i done: (most of the information below are copied from other forums/discussion on internet.... Google is always our best friend!)

1. downloaded latest alsa drivers:
      [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc4.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc4.tar.bz2)

2. tar xvf alsa-driver-1.0.14rc4.tar.bz2

3. patched the file
      alsa-driver-1.0.14rc4/alsa-kernel/pci/hda/patch_conexant.c

     circa at line 787, i changed
     

//////////////////////////////////////////////////////////////////////////////
static struct snd_pci_quirk cxt5045_cfg_tbl[] = {
	SND_PCI_QUIRK(0x103c, 0x30b7, "HP DV6000Z", CXT5045_LAPTOP),
	SND_PCI_QUIRK(0x103c, 0x30bb, "HP DV8000", CXT5045_LAPTOP),
	SND_PCI_QUIRK(0x1734, 0x10ad, "Fujitsu Si1520", CXT5045_FUJITSU),
	SND_PCI_QUIRK(0x8086, 0x2111, "Conexant Reference board", CXT5045_LAPTOP),
	{}
};
//////////////////////////////////////////////////////////////////////////////

with


//////////////////////////////////////////////////////////////////////////////
static struct snd_pci_quirk cxt5045_cfg_tbl[] = {
	SND_PCI_QUIRK(0x103c, 0x30b7, "HP DV6000Z", CXT5045_LAPTOP),
	SND_PCI_QUIRK(0x103c, 0x30bb, "HP DV8000", CXT5045_LAPTOP),
	SND_PCI_QUIRK(0x1734, 0x10ad, "Fujitsu Si1520", CXT5045_FUJITSU),
	SND_PCI_QUIRK(0x1734, 0x10cb, "Fujitsu Si3515", CXT5045_FUJITSU),
	SND_PCI_QUIRK(0x8086, 0x2111, "Conexant Reference board", CXT5045_LAPTOP),
	{}
};
//////////////////////////////////////////////////////////////////////////////

(added the 4th line...)

4. saved the file, compiled and installed the new alsa-drivers:
   ./configure --with-cards=hda-intel
   make
   make install

5. added to the file 
       /etc/modprobe.conf

   these lines:

###################################     
       options snd-hda-intel model=laptop
       alias snd-card-0 snd-hda-intel
       alias sound-slot-0 snd-hda-intel
 ###################################


6. saved and rebooted.



Now when i plug headphones speakers are muted and i'm happy!

Good Luck !!!!


p.s. : if you have any trouble google these keywords: hda high definition audio alsa v3515
           and take a look to

                    /usr/share/doc/alsa-base/driver/ALSA-configuration.txt
                    /usr/share/doc/alsa-base/driver/hda_codec.txt

           (there are chances you ave to gzip -d them first....) 
               

            here there are other informations and options to pass to kernel module that can help !!!

---

### Post by scrooge_74 on 2007-07-13
just open a terminal type alsamixer

Then change jack sene which probably is off

---

### Post by santoxyz on 2007-07-13
hi scrooge...
i have nothing similar to  'jack sene' in my mixer:
my volumes are Master, Pcm , Int Mic and Ext MIc .

For the moment the only solution i found is the one i posted up there.

---

### Post by scrooge_74 on 2007-07-13
hum strange that you cant see it on the alsamixer under headphones

---

### Post by agsamek on 2007-11-08
I have got v3515 and ubuntu 7.04 (not xubuntu). In this scenario it is enough to add a line:

options snd-hda-intel model=laptop

to /etc/modprobe.d/alsa-base with the following command:

sudo bash -c 'cd /etc/modprobe.d ; cp alsa-base alsa-base.2 ; echo -e "\noptions snd-hda-intel model=laptop\n" >> alsa-base'

And you are done.

---

### Post by jader2toesbumpy on 2007-11-19
> **agsamek said:**
> I have got v3515 and ubuntu 7.04 (not xubuntu). In this scenario it is enough to add a line:

options snd-hda-intel model=laptop

to /etc/modprobe.d/alsa-base with the following command:

sudo bash -c 'cd /etc/modprobe.d ; cp alsa-base alsa-base.2 ; echo -e "\noptions snd-hda-intel model=laptop\n" >> alsa-base'

And you are done.

HP dv6000 and this worked, thanks so much dude

---

### Post by JetPack on 2007-11-24
Adding in the line at the end of alsa-base worked for me, too..!!!

I have a Fujitsu Siemens Amilo Pro (V3515).

Thanks so much (it's the little things that count) :guitar:

---

### Post by jancek on 2008-02-20
Hi.

I also had this problem with headphones on my Fujitsu Siemens Esprimo Mobile V5545 with Ubuntu 7.10. And now it is gone. Thanks. Now I just have to solve my Wireless card problem.

---

