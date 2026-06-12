---
title: "Driver for Promise FastTrack TX8660, TX4660, TX8668"
date: 2010-08-21
forum: Hardware
---

### Post by joerg_ac on 2010-08-21
Hi,

I am desperately trying to get a SATA/SAS Hostadapter Promise FastTrack TX8660 working with Ubuntu. I did try for two days now and I hope somebody here might have an Idea. 

First of all the basics:

Mainboard is MSI H55-GD65
The bootdisk is attached to the SATA host integrated in the mainboard. I do not want to boot from the Promise host. It is supposed to be the based for a software raid.

3 disks are attached to the TX8660 and the adapter recognizes them. They are comfigured as JBOD.

Installation of Ubuntu desktop did go smoothly, but the 3 disks on the TX8660 are not available.

sudo lspci -vv

provides the following for this adapter

[FONT=Courier New]01:00.0 RAID bus controller: Promise Technology, Inc. Device 3781
    Subsystem: Promise Technology, Inc. Device 3781
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 10
    Region 0: I/O ports at bc00 [size=128]
    Region 2: I/O ports at b800 [size=256]
    Region 3: Memory at fbcff000 (32-bit, non-prefetchable) [size=4K]
    Region 4: Memory at fbcc0000 (32-bit, non-prefetchable) [size=128K]
    Region 5: Memory at fbcfc000 (32-bit, non-prefetchable) [size=8K]
    Expansion ROM at fbc80000 [disabled] [size=256K]
    Capabilities: [50] Power Management version 2
        Flags: PMEClk- DSI+ D1+ D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [70] Express (v1) Legacy Endpoint, MSI 00
        DevCap:    MaxPayload 256 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
            ExtTag- AttnBtn- AttnInd- PwrInd- RBE- FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
            MaxPayload 128 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr- UncorrErr+ FatalErr- UnsuppReq+ AuxPwr- TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x4, ASPM L0s L1, Latency L0 <128ns, L1 <2us
            ClockPM- Suprise- LLActRep- BwNot-
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk-
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x4, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt-
    Capabilities: [94] SATA HBA <?>
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [140] Virtual Channel <?>
    Capabilities: [160] Device Serial Number 01-00-00-00-02-00-00-00
    Capabilities: [170] Power Budgeting <?>[/FONT]


lsmod provides the following

[FONT=Fixedsys][FONT=Courier New]ls_iso8859_1           4633  1 
nls_cp437               6351  1 
vfat                   10866  1 
fat                    55350  1 vfat
binfmt_misc             7960  1 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9857  1 vga16fb
snd_hda_codec_intelhdmi    13090  1 
snd_hda_codec_realtek   279040  1 
ohci1394               30260  0 
usbhid                 41084  0 
snd_hda_intel          25677  2 
i915                  321160  3 
snd_hda_codec          85759  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87882  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   6375  0 
snd                    71106  17 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         30742  1 i915
parport_pc             29958  1 
intel_agp              29095  2 i915
drm                   199268  4 i915,drm_kms_helper
i2c_algo_bit            6024  1 i915
video                  20623  1 i915
output                  2503  1 video
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
lp                      9336  0 
parport                37160  3 ppdev,parport_pc,lp
hid                    83440  1 usbhid
usb_storage            49833  1 
ahci                   37870  2 
ieee1394               94771  1 ohci1394
pata_jmicron            2747  0 
r8169                  39650  0 
mii                     5237  1 r8169[/FONT]
[/FONT]
So I am sure that I am missing a driver for the Promise TX8660
Promise provides binary drivers for some older SUSE and RHEL on the drivers CD, so there must be some Linux support.

I did call the Promise support and they sent me the sources for compiling the driver myself. It is actually only partly open source. It contains an closed source object to be linked into the driver. it contains a makefile so I tried to compile it. 

This is the /usr/src

[FONT=Courier New]joerg@marvin:/usr/src$ ll
total 20
drwxrwsr-x  5 root src  4096 2010-08-21 01:47 ./
drwxr-xr-x 10 root root 4096 2010-04-29 14:17 ../
lrwxrwxrwx  1 root src    31 2010-08-21 01:47 linux -> linux-headers-2.6.32-24-generic/
drwxr-xr-x 24 root root 4096 2010-08-21 00:11 linux-headers-2.6.32-24/
drwxr-xr-x  7 root root 4096 2010-08-21 11:38 linux-headers-2.6.32-24-generic/
drwxrwsrwx  6 root root 4096 2010-08-21 13:32 t8sas/[/FONT]

what promise did provide is in t8sas/
there is also linux linked to the installed kernel version.

in the t8sas solder I did a make clean. It looks like this:

[FONT=Courier New]joerg@marvin:/usr/src/t8sas$ sudo make clean
rm -rf *.o *.ko .*.cmd .?*.o.d .*tmp* linux/*.o linux/*.ko linux/.*.cmd linux/.?*.o.d linux/.*tmp* *.mod.c ftlib.obj *.symvers
rm ./partial/* -rf
ln -s ftlib/ftlib.obj.64 ftlib.obj
joerg@marvin:/usr/src/t8sas$ ll
total 44
drwxrwsrwx 5 root root  4096 2010-08-21 18:42 ./
drwxrwsr-x 5 root src   4096 2010-08-21 01:47 ../
drwx--S--- 2 root root  4096 2010-08-21 00:57 ftlib/
lrwxrwxrwx 1 root root    18 2010-08-21 18:42 ftlib.obj -> ftlib/ftlib.obj.64
drwxrwsrwx 2 root root  4096 2010-08-21 00:57 include/
drwxrwsrwx 2 root root  4096 2010-08-21 18:39 linux/
-rwxr-xr-x 1 root root 10532 2010-08-21 18:41 Makefile*
-rw-r--r-- 1 root root    31 2010-08-21 13:32 modules.order
-rwxr-xr-x 1 root root    57 2010-08-21 01:32 products.h*
-rwxr-xr-x 1 root root  2475 2010-08-21 01:32 README*[/FONT]

Now I did compile it with the following result

[FONT=Courier New]joerg@marvin:/usr/src/t8sas$ sudo make
make ARCH=x86_64 V=0 CC=cc LD=ld ARCH=x86_64 DRIVER_SRC_DIR=/usr/src/t8sas -C /usr/src/linux SUBDIRS=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
  CC [M]  /usr/src/t8sas/linux/osd_main.o
  CC [M]  /usr/src/t8sas/linux/osd_cmpi.o
  CC [M]  /usr/src/t8sas/linux/osd_cmpm.o
  CC [M]  /usr/src/t8sas/linux/osd_ioctl.o
  CC [M]  /usr/src/t8sas/linux/osd_timer.o
  CC [M]  /usr/src/t8sas/linux/osd_wrap.o
  LD [M]  /usr/src/t8sas/t8sas.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /usr/src/t8sas/.ftlib.obj.cmd for /usr/src/t8sas/ftlib.obj
WARNING: modpost: Found 1 section mismatch(es).
To see full details build your kernel with:
'make CONFIG_DEBUG_SECTION_MISMATCH=y'
  CC      /usr/src/t8sas/t8sas.mod.o
  LD [M]  /usr/src/t8sas/t8sas.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'[/FONT]

The folder content after the make is:

[FONT=Courier New]joerg@marvin:/usr/src/t8sas$ ll
total 876
drwxrwsrwx 6 root root   4096 2010-08-21 18:46 ./
drwxrwsr-x 5 root src    4096 2010-08-21 01:47 ../
drwx--S--- 2 root root   4096 2010-08-21 00:57 ftlib/
lrwxrwxrwx 1 root root     18 2010-08-21 18:46 ftlib.obj -> ftlib/ftlib.obj.64
drwxrwsrwx 2 root root   4096 2010-08-21 00:57 include/
drwxrwsrwx 2 root root   4096 2010-08-21 18:46 linux/
-rwxr-xr-x 1 root root  10532 2010-08-21 18:41 Makefile*
-rw-r--r-- 1 root root     31 2010-08-21 18:46 modules.order
-rw-r--r-- 1 root root      0 2010-08-21 18:46 Module.symvers
-rwxr-xr-x 1 root root     57 2010-08-21 01:32 products.h*
-rwxr-xr-x 1 root root   2475 2010-08-21 01:32 README*
-rw-r--r-- 1 root root 402156 2010-08-21 18:46 t8sas.ko
-rw-r--r-- 1 root root    209 2010-08-21 18:46 .t8sas.ko.cmd
-rw-r--r-- 1 root root   3388 2010-08-21 18:46 t8sas.mod.c
-rw-r--r-- 1 root root   7248 2010-08-21 18:46 t8sas.mod.o
-rw-r--r-- 1 root root  22291 2010-08-21 18:46 .t8sas.mod.o.cmd
-rw-r--r-- 1 root root 395808 2010-08-21 18:46 t8sas.o
-rw-r--r-- 1 root root    298 2010-08-21 18:46 .t8sas.o.cmd
drwxr-sr-x 2 root root   4096 2010-08-21 18:46 .tmp_versions/
[/FONT]
There is now the t8sas.ko file, which is according to my understanding the driver's kernel module. We can have a closer look at it with modinfo:

[FONT=Courier New]joerg@marvin:/usr/src/t8sas$ modinfo t8sas.ko
filename:       t8sas.ko
license:        GPL
version:        1.2.0.58
description:    Promise Technology FastTrak T8 Series Controllers
author:         Promise Technology, inc. LTD
alias:          pci:v0000105Ad00003781sv0000105Asd00003783bc*sc*i*
alias:          pci:v0000105Ad00003781sv0000105Asd00003782bc*sc*i*
alias:          pci:v0000105Ad00003781sv0000105Asd00003781bc*sc*i*
alias:          pci:v0000105Ad00003781sv0000105Asd00003780bc*sc*i*
depends:        
vermagic:       2.6.32.15+drm33.5 SMP mod_unload modversions [/FONT]

The README instruction said the driver can be loaded with

# modprobe -a sd_mod
# insmod t8.ko

I guess they meant t8sas.ko instad of t8.ko

so I did the following to try out the driver

# sudo modprobe -a sd_mod
# sudo insmod t8sas.ko

This made the system crash and freeze.

Please help! 

I first of all wonder if the driver was correctly built, because there were warnings.

Then I would highly appreciate your opinion what I might try and where to look for a solution. I guess there are also no maintained driver packages for this hardware in some repositories. At least google does not find anything when searching for the product name or when searching for "t8sas"

Your help is very much appreciated. Sorry for the long post, I hope these details help more than they confuse. I thought Promise is not too exotic hardware and they claim to have Linux support, so I was a little surprised to have these problems to get it working and to find any info.

best regards, Joerg







...

---

### Post by braky on 2010-08-21
Hi there,
I am in the process of installing this card in Ubuntu 10.04 lts.

Can you send me the sourcecode, I need it also.
I'll try and build it.
Mail it to braky @ dommel.be

I think the problem is that you did a sudo make clean which erased the .cmd file that is needed for the compilation.

Regards,
Braky

---

### Post by joerg_ac on 2010-08-21
Hi Braky,

I did sent an email to you with what I got from promise.

I guess there are some errors in the README. For example t8sas.ko is generated rather than t8.ko and the module name should be t8sas rather than t3sas.

There is also no .cmd file in the provided archive. All cmd file were generated when doing the make. 
I did also also edit my makefile (you have the original) in order to set VERBOSE to 1. it provides more detailed output.

I am also not sure if the ftlib.obj was really linked into the final driver. That may be the problem.

I am looking forward to read about your experience. It is good to have somebody to exchange ideas with when facing problems like this. 

best regards and good luck, Joerg

---

### Post by braky on 2010-08-21
Compiling went ok, just the same warning as you had.

I can do an insmod of t8sas ONLY if there are no disks connected to the controller.
If I try to do it when there is a disk connected, I hear the disk doing something and the system just freezes and caps and scroll-lock start to blink.

Did the same on fedora 2.6.33.6-147.2.4.fc13.x86_64 : same effect.

Help :-(

---

### Post by joerg_ac on 2010-08-22
Hi,

So it is at least not me being too stupid or something like that. 

I have also no idea what I can try now. I think I will give the promise support another call tomorrow. 

However, after I bought that card a colleague did already warn me that Promise products might be a problem together with Linux because they support it badly. I thought I would be safe, because they have some Linux distributions in their driver and compatibility list for this card.

If nobody else has an idea I might go for a different hostadapter card and call this a lesson learned.

Please, if somebody has an idea, please help.

best regards, Joerg

---

### Post by braky on 2010-08-22
If you do contact support, first do the following:

[LIST=1]
[*]remove all disks from the controller
[*]do insmod of t8sas
[*]poweroff
[*]attach the disks
[*]boot
[*]after the grub screen press ESC so that the graphical bootscreen is gone
[*]wait for the kernel panic
[*]take a photo of your screen (or write it down)
[*]send this info to support, and maybe they'll have enough info to help
[/LIST]

If they ask for setting acpi=off or acpi=3Doff ... it doesn't help.

To get your system back to normal, boot without disks attached to the controller, and remove the t8sas module.

Cheers

---

### Post by joerg_ac on 2010-08-22
hi, 

thanks for the hint.

I tried, but after reboot the module seems to be gone. Does insmod only load it temporarily? I did

sudo insmod t8sas.ko 

from /lib/src/ ... /driver/scsi where I have copied the file

also lsmod shows t8sas. after a reboot with disks attached the module is missing again.

What do I need to do in order to make it permanent or surviving a reboot? 
I also have to refer to the actual file. I cannot just do "sudo insmod t8sas"

Did I miss a step?

best regards, Joerg

---

### Post by braky on 2010-08-22
Some progress made....

If you put the controller in SAS HBA MODE then it WORKS! (alt-F on boot)
Well it doesn't do a kernel panic and I can see the drive connected to the controller.
I'm doing some stability tests now to be sure it doesn't fail on me when there is heavy load on the disks.

Cheers

---

### Post by joerg_ac on 2010-08-22
That seems to be the trick, I can confirm that I see the disks now. (sudo fdisk -l)

to make it more clear for everybody, press ctrl-F at initialization of the adapter a t system startup before OS booting. This enters the card's BIOS configuration. Change the HBA mode to "SAS HBA". This disables the build-in RAID functions and presents the disks as JBOD. That is fully ok with me, because I anyway wanted to use software raid.

What tools do you use for verification of reliability and performance?

I still have problems to make the driver module load automatically. How will I do that? I guess I have to update some configuration file, or is there a tool/command for that?

Has anybody experience with module-assistant? That tool seems to be quite useful to automatically re-compile and install the driver in case there is a new kernel.  Or can a .deb package be made from it? Or is there another tool for making the compilation of the driver automatic?

best regards, Joerg

---

### Post by braky on 2010-08-22
No specials tools for testing:
I'm first going to do some basics like formatting the drives, copying some 2TB of data around.
Some mdadm tests to see how it reacts with the controller on drive failures and such.
My current homeserver Fedora/Ubuntu has 6 satadisks connected on the mainbord (1bootdisk 160GB and 5 x 1TB in raid5 mdadm) + 1-port Sil3531 (esata) + 8-port TX8660 and 5 x 2TB WD 20EARS disks for testing...

Concerning the module, (in Fedora) 

I copied the t8sas.ko to /lib/modules/$(uname -r)/kernel/drivers/scsi/
I copied the t8sas.ko to /lib/modules/$(uname -r)/updates/
#execute depmod
depmod $(uname -r) -v
#make a new initramfs that has the new module
mkinitrd /boot/initrd-$(uname -r).new.img $(uname -r)
#!!edit /boot/grub/grub.conf so that the new generated .img is used

I think in Ubuntu there is an easier way to do this, but it should work also ... (i hope)

Cheers,
braky

---

### Post by IcarusR on 2010-08-22
Been following this thread, but not had any positive input so kept quiet.

braky

> My current homeserver Fedora/Ubuntu has 6 satadisks connected on the mainbord (1bootdisk 160GB and 5 x 1TB in raid5 mdadm) + 1-port Sil3531 (esata) + 8-port TX8660 and 5 x 2TB WD 20EARS

Thats some home server you've got there !! Makes mine look simple, which it is, with 2 x 1TB WD green drives (on a  2 port 3Ware hardware raid mirror) & a 100Gb boot drive.
Will have to upgrade soon as am running out of space for my music collection.

How do you keep the server cool with all those disks in it ??

---

### Post by joerg_ac on 2010-08-22
Hi,

I missed to use depmod. It seems to "re-register" all modules in the /lib/modules/<kernal>/ subtree. 

After that I can refer to the module by its name (t8sas) in modprobe and modinfo.

To load it automatically I added t8sas to /etc/modules

I guess I have a look into module-assistant now in order to handle this driver automatically.

best regards, Joerg

---

### Post by braky on 2010-08-22
No heat problems, all the drives are WD green and they run all at 36C, 39C on heavy disk access.
I have 2 backplanes of 5 disks each and each backplane is custom cooled by a silent 80mm fan.
The 2 noname backplanes are (5 x 3.5" Hard Disks) like the IcyBox IB-555SK.
Just make sure that you use backplanes with 80mm fans, and not 2x 40mm. These 40mm tend to make more noise. But the stock 80mmm also makes a lot of noise, so I replaced them with a silent papst fan 80mmx15mm. The server is feeding my PCH-C200 and is whisper silent and cool.

I also started my first raid with 2x 500Gb (synology ds207+), but it just keeps on growing... Video takes a lot of space, maybe I shouldn't have digitized all my dvd and bluray :-)

Cheers

---

### Post by joerg_ac on 2010-08-22
@ [IcarusR]("http://ubuntuforums.org/member.php?u=179763")

I am building a new server now, which might soon have a higher number of disks. I was also worries about the cooling although the disks are also green ones (Samsung HD203WI). I am using the Lian Li case PC-B70. It has 5 external 5.25" bays plus 7 internal 3.5" bays in the front behind two big fans, plus 3 more 3.5" internal disk bays in the back above the mainboard. All disks are installed with fans next to them and with some space between each other. So it has space for 10 well cooled disks and can even be extended using the 5 external bays if more is needed.

best regards, Joerg

---

### Post by braky on 2010-08-23
Joerg,

I contacted support today and did not even receive the driver to compile myself.
NO linux support sir, Suse and Redhat only.
SO I didn't bother any further...

Hmm, this will be my first and last promise controller, I promise! ;-)

Is there like a kind of driver page/site where I can put this driver on for other people using the TX8660 ?

PS Installed the webpam interface also but it doesn't provide detailed smart data like temperature of the drives, which is a pitty.

Cheers

---

### Post by joerg_ac on 2010-08-23
Braky,

I thin the same about promise now. To me, they seem to be at least ten years behind the competition when it comes to Linux support. I think I might go for a different card now and sell the promise card. We have a driver now, but what about updates and support in the future. I do not want to risk to be without a driver again in the future. 

That we have a driver now is only because I was lucky to get somebody on the phone who does not tell me the official "not supported" reply. I also wonder how their support for Redhat and SUSE enterprise servers would work with driver modules generated only against a particular kernel version. Do they really think there will never be security updates and bug-fixes in those kernels. 

I had a look already at other products and I found for example the Intel SASUC8I. It has also a reasonable prize comparable to the one we have from Promise and it seems to be supported by Ubuntu and many other Linux versions out of the box due to its LSI SAS1068E Chip. There is the mptsas driver module, which should work. Can somebody confirm this? This card does not support RAID5, but I anyway plan to go for a software raid. When deciding what to buy I had these two options and I did go for the wrong one.

I have not decided yet how to proceed from now, but I do not really trust the current solution based on this promise driver. 

best regards, Joerg

---

### Post by joerg_ac on 2010-08-23
Braky,

me again. I was so upset about Promise that I did forget to answer your question. 

I am not sure where to upload it. Does this Forum have space for something like this. I could attach the driver sources to this thread. However I am not so sure about the license and i do not want to cause trouble to this board.

I think the Driver said something about being GPL, but i am not sure if this implies the included binary object can also be distributed. On the other hand they did give it to me for free without any restrictions I am aware of. 

Can a board admin comment on this? 

Perfect would be to get this driver as a package together with Ubuntu. I am new to this kind of questions, but can this be done based on the partial-open source driver I got from Promise?

best regards, Joerg

---

### Post by braky on 2010-08-23
I looked also at the LSI SAS1068E Chip based cards, but found to many problems on the forums with stability with mdadm and smartctl.
I'm keeping this card (bought it on ebay for half price) 
My video server is not connected to the internet and I just use it as storage so kernel updates are no issue.  I just need a stable NFS / CIFS server to stream video.

It is a shame that there are no cheap mainbords with 8 or more sata onboard...

Cheers

---

### Post by joerg_ac on 2010-08-23
Hi again,

I wrote a couple of emails to Promise support in Germany and Taiwan to make them aware of this thread and to invite them to join in this discussion. let's see if somebody shows up here. I would be very interested in a n statement from Promise. 

To me it seems so easy for Promise to significantly improve the Linux support. Just put the latest driver sources on the server for download. Promise anyway has such a driver package. If they would also allow to include this into Linux distributions being provided as driver packages, the situation would change from practically no reasonable support to something I could very well accept. It is also Ok with me that the driver is partly binary. Many graphic card drivers seem to be distributed similarly. I would be very happy with this kind of support.

Regarding being safe in the future:
I guess if I set up a software raid with Linux, the adapter can be replaced by any model that presents the disks as JBOD later without loosing the software RAID. Is this correct? 

best regards, Joerg

---

### Post by braky on 2010-08-23
That's correct. I just put my software raid 5x1TB drives from the mainboard sata to the tx8660 for testing purposes.
Booted the server and the software raid starts up without any problems.
That's the reason I went for software raid so I don't run in problems when my controller dies.
There's a file system check running now and after that I'm going to remove a disk from the controller and check how mdadm reacts.

Cheers

---

### Post by joerg_ac on 2010-08-23
Hi, 

I did contact the forum admins regarding the attachment of the driver package to this thread.

I think on Wednesday I will join in again with testing. The mainboard has hardware issues and a replacement is ordered now. 

I have also read now about problems with the LSI chip and its drivers. I am not sure how serious these issues are for my use case, but at least there is a discussion and people seem to work on it.

Adaptec also offers an reasonable entry level 8-port card (Adaptec RAID 2805) and they seem to have good Linux support for that card and in general. However with that card we are at about 200 EUR already. But if you buy cheap you buy twice. Sometimes this is so true. 

best regards, Joerg

---

### Post by Schmov17 on 2010-08-28
Hi all, thankfully stumbled upon this thread after a few weeks of passively tinkering with this card.  So I gather from the responses that you've managed to get it recognized as JBOD to do a software raid but haven't gotten it to recognize the card when set to hardware raid? Any chances on getting it to read as a hardware raid?  

And for that matter, I wouldn't mind same input on software vs hardware raids.  My thinking was always that hardware was better because if the OS goes kaput then the raid is still intact and you can rebuild.  Perhaps my logic isn't quite accurate?

Well done on getting the card this far, and thanks in advance for any feedback.

---

### Post by braky on 2010-09-03
> **Schmov17 said:**
> Hi all, thankfully stumbled upon this thread after a few weeks of passively tinkering with this card.  So I gather from the responses that you've managed to get it recognized as JBOD to do a software raid but haven't gotten it to recognize the card when set to hardware raid? Any chances on getting it to read as a hardware raid?  

And for that matter, I wouldn't mind same input on software vs hardware raids.  My thinking was always that hardware was better because if the OS goes kaput then the raid is still intact and you can rebuild.  Perhaps my logic isn't quite accurate?

Well done on getting the card this far, and thanks in advance for any feedback.
I only get it to work in HBA mode. Since there is totally no support from Promise, I don't expect it ever to work.

Concerning software raid : check out [https://raid.wiki.kernel.org/index.php/Linux_Raid](https://raid.wiki.kernel.org/index.php/Linux_Raid) it contains all the info you need. Pros and cons.

Cheers

---

### Post by braky on 2010-09-03
Some extra info about the use of TX8660:

[LIST]
[*]Looks stable in HBA mode (copied 6TB without problems, rebuild array 4 times)
[*]DOES NOT SUPPORT hotplugging disks, all disks will be detached:frown:
[*]UNPLUGGING disks works :-)
[*]in Ubuntu don't use mdadm v2.x , it will freeze on heavy load even when not using the TX8660 ](*,)
[*]use MDADM V3.1.2
[/LIST]

---

### Post by braky on 2010-09-04
In attachment the driver.
I hope someone can use it.

Cheers

---

### Post by joerg_ac on 2010-09-14
Dear all,

Also my software RAID5 based on the TX8660 is working stable. I did start with 3x2TB disks and extended it two times to now 5x2TB. Also the performance seems to be quite ok. I am using it for a while now and i did not experience any further problems. 

What I still do not like is that the driver is very rudimentary and does for example not even provide smart info of the disks. I also still fear future kernel updates and the need to recompile the driver with a future kernel. I wonder if I can ever manage to get again an updated version of this driver from promise if needed.

best regards, Joerg

---

### Post by donCreat0r on 2011-01-01
I've just got the same issue.

Compiled the driver from the source (thanks, braky!). It works fine on CentOS 5.5 (kernel 2.6.18 ), but freezes the Ubuntu 10.10. I've noticed there's no 'scsi_mod' module in lsmod output in Ubuntu, so the 't8sas' driver appears on the left column (when insmod'ing with detached Promise device). Is it because a scsi compiled into ubuntu kernel, not in a module?

I wonder if one of the kernel magicians can take a look in t8sas sources and resolve any compatibility issues... I suspect the ftlib binary works fine, the problem is in the source (which has a lot of 'TODO' and 'fixme' marks according to my investigations).

I can stay with a CentOS for now (although it take a whole five minutes to boot!), but it's more like Win95 to WinXP being compared with Ubuntu, it appears to be a very oldschool Linux :) But I need it mostly as a host for VMWare Player, so it's ok.

---

### Post by cedric_tux on 2011-01-14
Could somebody give me little howto, because when i try to compile the driver i'm getting error messages on Ubuntu 10.04, while on centos it is much easier.

---

### Post by kains on 2011-01-20
I've found that TX8660 works with AHCI driver, you just have to patch drivers/ata/ahci.c adding to ahci_pci_tbl[] (around line 385 on 2.6.32.2) ID of this card:
{ PCI_VDEVICE(PROMISE, 0x3781), board_ahci }, 

Working with quite heavy usage for a year or so...

---

### Post by donCreat0r on 2011-01-20
> **kains said:**
> I've found that TX8660 works with AHCI driver, you just have to patch drivers/ata/ahci.c adding to ahci_pci_tbl[] (around line 385 on 2.6.32.2) ID of this card:
{ PCI_VDEVICE(PROMISE, 0x3781), board_ahci }, 

Working with quite heavy usage for a year or so...

does it work with a RAID volume configured or just as a plain set of ACHI SATA disks?

I suspect the second option, but hope for a miracle... :)

---

### Post by kains on 2011-01-20
I have not tried it as a RAID, as I don`n need one, but I too suspect that it won`t work. Worth a try anyways, if you have access to one for testing...

---

### Post by Rakyr on 2011-03-11
Hi there,

Can someone send me the source code of the driver too? I tried the support but, of course, the wouldn´t help me. I even tried CentOS, but all the drivers would only work with outdated distris/kernels. I better don´t change too much in the driver files, as i am no expert in linux (and fairly new to ubuntu and this forum). But compile somethin, that i can do.

So could someone please send me the sourcecode?

greetins
Rakyr

---

### Post by joerg_ac on 2011-03-15
Hi Rakyr,

The driver is in the thread in the message from Braky from 4th of  September 2010. This is the file I was lucky to get from Promise  support last summer.

It compiles with a few warnings but it is working as long as the card is configured without hardware RAID. Braky gave this hint. I anyway wanted to use software RAID, so this was no issue for me. 

This driver is running since last September without any major problem with Ubuntu 10.04. I have a 5 disk Software RAID 5 array running. Also the performance of the Array seems to be Ok. Only once in a while after the kernel is updated with an Ubuntu update I need to recompile the driver again manually. So far it still works well with all updates in the Ubuntu 10.04 series.

I guess Promise did not mention to you when they expect the open source driver to be ready? Did they mention if they will produce a freely available open source driver themselves or if they just expect the community to produce one sooner or later and independent of them? 

best regards, Joerg

---

### Post by Rakyr on 2011-03-15
Damn how did i overread this post 3 times? Thanks!!
Good to know the driver seems to be working flawless.

Promise support wouldn´t say when or from whom to expect the driver, exact wording:
"Since this controller is a mainstream product, you could expect an open source code in future."

Rakyr

---

### Post by joerg_ac on 2012-04-21
Hi,

I have upgraded mow mu machine to 12.04 and I cannot get the driver for the TX8660 running. Compiling it from the old sources does lead to errors. I guess the driver was made for the 2.6 Kernel series and does not work with 3.2. Can somebody confirm this?

The other method mentioned in this thread was using the ahci driver and updating ahci.c.
Where do I find this file? Does this mean I need to compile my own Kernel?

Is there any other way of getting this to work?

I would really appreciate some hints.

Best regards, Joerg

---

