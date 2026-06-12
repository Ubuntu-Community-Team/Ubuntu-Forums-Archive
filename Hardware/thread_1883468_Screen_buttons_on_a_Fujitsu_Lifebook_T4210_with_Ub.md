---
title: "Screen buttons on a Fujitsu Lifebook T4210 with Ubuntu 11.10"
date: 2011-11-19
forum: Hardware
---

### Post by Scarlath on 2011-11-19
Hello!

I recently installed Ubuntu 11.10 on my Fujitsu Lifebook T4210 (a tablet PC) and everything's working like a charm, including the touch functions with the stylus and so forth. However, I still haven't gotten the buttons on the screen to work (picture: [http://i00.i.aliimg.com/photo/v0/109561910/Fujitsu_Lifebook_TabletPC_T4210.jpg](http://i00.i.aliimg.com/photo/v0/109561910/Fujitsu_Lifebook_TabletPC_T4210.jpg)). The buttons are supposed to rotate the screen as well as having mappable buttons for other functions.

I searched for this issue and found [this thread]("http://ubuntuforums.org/showthread.php?t=1274324") regarding the same subject. The replies in that thread directed me to the following websites/sources:

[https://sourceforge.net/projects/fjbtndrv/](https://sourceforge.net/projects/fjbtndrv/)

[https://launchpad.net/~khnz/+archive/ppa](https://launchpad.net/~khnz/+archive/ppa)

However, I noticed there is no PPA for Ubuntu 11.10. If I add a PPA for 11.10 and then try to install the fjbtndrv package the terminal simply returns "package not found". Anyone know of a workaround on this or if the package is going to be made available for 11.10? Or am I simply just doing something wrong? Haven't spent that much time with Linux yet. ;)

---

### Post by Favux on 2011-11-19
Hi Scarlath,

My guess is Robert Gerlach no longer has a Fujitsu tablet to test the fjbtndrv on, which is why he hasn't updated the PPA.

Someone needs to download the package and decompose it into the button assignment script and the rotation script etc. and test them.  Fix/update anything that needs it and start another PPA.  I've seen some of that stuff and it doesn't seem like it would be terribly difficult.

---

### Post by Scarlath on 2011-11-20
Aw.That is too bad. Anyone else with experience with this somewhere that's sitting on a workaround/fix? :D

---

### Post by Favux on 2011-11-20
Well how 'bout that!  Robert Gerlach just updated the PPA for Oneiric yesterday.  See:
[https://launchpad.net/~khnz/+archive/ppa?field.series_filter=oneiric](https://launchpad.net/~khnz/+archive/ppa?field.series_filter=oneiric)
[http://sourceforge.net/projects/fjbtndrv/files/](http://sourceforge.net/projects/fjbtndrv/files/)

Still no version for Natty, but since you have Oneiric you're not going to care, are you?

So you should be good to go once you add the PPA.  Let us know if it works.

---

### Post by Scarlath on 2011-11-23
Well, well. I ran 'sudo apt-get install fjbtndrv' and it seems to have installed properly. Now the question is how I get these scripts to function, hehe. Trying to find some documentation but to no avail! (oh, and I rebooted after install)

---

### Post by Favux on 2011-11-23
Huh.  No rotation or buttons?

Run in a terminal this command:
```
lsmod
```
That will list the kernel modules present.  In addition to fujitsu-laptop you should now see the kernel module that fjbtndrv installs fujitsu-tablet.  Is it there?

---

### Post by Scarlath on 2011-11-24
> **Favux said:**
> Huh.  No rotation or buttons?

Run in a terminal this command:
```
lsmod
```
That will list the kernel modules present.  In addition to fujitsu-laptop you should now see the kernel module that fjbtndrv installs fujitsu-tablet.  Is it there?

Can't see any fjbtndrv in that list! :o

```
ludvig@ludvig-LIFEBOOK-T4210:~$ lsmod
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
snd_hda_codec_idt      60049  1 
snd_hda_intel          24262  4 
snd_hda_codec          91754  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
arc4                   12473  2 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
iwl3945                73360  0 
pcmcia                 39822  0 
iwl_legacy             71499  1 iwl3945
wacom_w8001            12851  0 
joydev                 17393  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
i915                  505108  3 
drm_kms_helper         32889  1 i915
drm                   192226  4 i915,drm_kms_helper
mac80211              393459  2 iwl3945,iwl_legacy
serport                12808  1 
psmouse                73673  0 
serio_raw              12990  0 
i2c_algo_bit           13199  1 i915
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
cfg80211              172392  3 iwl3945,iwl_legacy,mac80211
snd                    55902  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
fujitsu_laptop         18504  0 
soundcore              12600  1 snd
irda                  185428  0 
crc_ccitt              12595  1 irda
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
sky2                   49317  0 
ludvig@ludvig-LIFEBOOK-T4210:~$ 

```

---

### Post by Favux on 2011-11-24
Yep, just see *fujitsu_laptop*.  So first run this command in a terminal:
```
sudo depmod -a
```
and reboot.  That will rebuild all module dependencies.  Let's see if that gets *fujitsu_tablet* to auto-load.  I'm assuming it installed correctly and is there.  If not add it, *fujitsu_tablet* (or *fujitsu-tablet*?) to the end of the list in the modules file in /etc:
```
gksudo gedit /etc/modules
```
and reboot.

---

### Post by Scarlath on 2011-11-24
Well, 

'depmod' - reboot - nothing

adding 'fujitsu_tablet' to /etc/modules - reboot - nothing

adding 'fujitsu-tablet' to /etc/modules - reboot - nothing

:(

Should I try to just remove/add the PPA and reinstall the entire thing over again? If so, how do I proceed? Or is there anything left for us to try? :)

---

### Post by Favux on 2011-11-24
Well I see there is a dkms thing in there.  So the fujitsu-tablet is likely implemented through dkms at a guess.  See if there is a folder containing it in /usr/src or if it is showing up in your current kernel's /lib/modules/`uname -r`/updates/dkms directory.

Also check if something related to it is showing up in Startup Applications.

---

### Post by Scarlath on 2011-11-24
```
ludvig@ludvig-LIFEBOOK-T4210:~$ ls /usr/src
fujitsu-tablet-2.3.1            linux-headers-3.0.0-13
linux-headers-3.0.0-12          linux-headers-3.0.0-13-generic
linux-headers-3.0.0-12-generic
ludvig@ludvig-LIFEBOOK-T4210:~$ 

```

For "ls /lib/modules/`uname -r`/updates/dkms" it claims the folder doesn't exist. As in, "/lib/modules/3.0.0-13-generic/updates/dkms" does not exist. 

In start up programs I have two entries for "fscd ("Tablet PC Helper")".

---

### Post by Favux on 2011-11-24
Alright, some progress.  So there is a dkms implemented in /usr/src.  The product of that, the kernel module/driver fujitsu_tablet.ko, is what should be in /lib/modules/3.0.0-13-generic/updates/dkms or maybe updates.

What are the command lines for the two "fscd ("Tablet PC Helper")" Startup entries?  In other words what are they trying to invoke?

Boy, I'm learning more than I wanted to.  All I was thinking is if anyone was interested we could try adding Fujitsu rotation support to Magick Rotation:  [https://launchpad.net/magick-rotation](https://launchpad.net/magick-rotation)  Provide another alternative, with maybe a few more features.  So mainly I'm interested in the switch output of fujitsu_tablet.ko.  See if we can parse it.  Once it is working I'd like to see if there is a "hotkey" related to it in say *xinput list*.

---

### Post by Scarlath on 2011-11-24
Haha, I'm glad you're enjoying it. ;)

The startup entries contain
```

/usr/bin/fscrotd

```
and 
```

/usr/bin/fscd

```

There is no 'updates' folder in */lib/modules/3.0.0-13-generic/* as far as I can see.

---

### Post by Favux on 2011-11-24
OK, maybe I'm guessing the wrong location.  According to dkms.conf.in:
> DEST_MODULE_LOCATION="/kernel/driver/input/misc"
So I guess check in the current kernel's lib/modules/kernel/drivers/misc and see if it is there.

Otherwise try a search for the fujitsu-tablet.ko.

---

### Post by Scarlath on 2011-11-24
```
ludvig@ludvig-LIFEBOOK-T4210:/lib/modules/3.0.0-13-generic/kernel/drivers/misc$ ls
ad525x_dpot-i2c.ko  bh1780gli.ko  enclosure.ko   isl29003.ko  ti_dac7512.ko
ad525x_dpot.ko      bmp085.ko     hmc6352.ko     isl29020.ko  tifm_7xx1.ko
ad525x_dpot-spi.ko  c2port        hpilo.ko       iwmc3200top  tifm_core.ko
apds9802als.ko      cb710         ibmasm         lis3lv02d    ti-st
apds990x.ko         ds1682.ko     ics932s401.ko  pch_phub.ko  tsl2550.ko
bh1770glc.ko        eeprom        ioc4.ko        phantom.ko   vmw_balloon.ko

```

Hmmm... 

```
find / fujitsu-tablet.ko
```
returns... no such file or directory. :(

---

### Post by Favux on 2011-11-24
Alright, that implies something is going wrong with the module build/compile.

If I look in fjbtndrv-2.3.1 folder in the src/linux directory nothing in the Makefile jumps out.  Other than the uninstall command is:
```
rm -f /lib/modules/$(KERNELRELEASE)/extra/fujitsu-tablet.ko
```
Where did extra come from?

Anyway Oneiric has a new tool chain so if you use the old syntax and put libraries the compile is dependent on first before the object, which was standard before the new tool chain, instead of after it it won't compile.  So I'm wondering if that is the problem.  Except I don't see anything in the compile instructions that would do that:
```
obj-m		+= fujitsu-tablet.o

all: fujitsu-tablet.ko
modules: fujitsu-tablet.ko
modules_install: install

fujitsu-tablet.ko: fujitsu-tablet.c
	$(MAKE) -C $(KERNEL_SOURCE) M=$(PWD) modules

install: fujitsu-tablet.ko
	$(MAKE) -C $(KERNEL_SOURCE) M=$(PWD) modules_install
```

I guess you can't file a bug report on a PPA but you can on the SourceForge site or otherwise contact him.  That's probably your best bet.  Or the other option would be to take a walk into the unknown and try to compile it manually and see what happens.  If an error is thrown up or something.

---

### Post by Scarlath on 2011-11-24
I'll try to contact him this weekend then! Thanks for your help! I'll be sure to post here again as soon as I have more information or just run into another wall ;)

---

