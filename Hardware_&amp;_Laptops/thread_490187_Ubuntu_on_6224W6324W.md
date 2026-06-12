---
title: "Ubuntu on 6224W/6324W"
date: 2007-07-02
forum: Hardware &amp; Laptops
---

### Post by michel_iwaniec on 2007-07-02
Hi, I have just purchased my first laptop in many years, the Znote 6224W by Zepto Computers. (which for the notice seems to be identical to its sibling the 6324W, apart from the color)

Having seen Ubuntu install without much hassle on a desktop a few years back, I was looking forward to trying out Ubuntu 7.04 on my new laptop as soon as it arrived. But the problems have been lining up. Just getting the installation to run was problematic, but worked fine after I set the SATA HDD to compatibility mode in the BIOS setup. But once it installed, it was starting to look just like my first Linux experience with Debian many years back. 

The sound won't work at all. (the sound device is listed as "Realtek HD audio" in XP, and it only worked in XP after I installed the included drivers from the included CD)

The drivers from Nvidia won't install. This is somewhat expected as both the laptop and the 8600M GT haven't been around very long. But I would like to ask anyone with an Geforce 8M laptop to share his/her experience with getting it to work in Ubuntu.

However, the most annoying problem of them all is that the mouse cursor is "noisy", in the sense that it sometimes (far too often) jumps around when moving it. This makes it extremely frustrating to troubleshoot the other problems. I have briefly tested it with a USB mouse at a friend's place, and it seemed to give similar results. In XP, there are no problems of this kind.

I have not tested the wireless adapter, bluetooth, IR or other components yet, as I want to get the vital parts working before spending any more time on this.

As my post may show, I have very little experience with troubleshooting Linux in general, and my hopes of getting Ubuntu to work on this laptop are currently fading. I am posting here in the hope that someone may have gotten Ubuntu to work on this model (or a similar one) already. Or that someone may recognize my problems as general problems concerning Linux on laptops. I feel I do not have the skills nor the free time to figure this out on my own.

A product page (including a link to data sheet with specs) can be found here: 
[http://uk.zepto.com/Shop/Notebook.aspx?notebookid=644](http://uk.zepto.com/Shop/Notebook.aspx?notebookid=644)

Again, the problem with the jumping mouse cursor is the most severe. It feels pointless to even try to troubleshoot the other stuff until I have a working mouse cursor. Anyone who can help me get rid of this bug gets a digital hug.

// Michel Iwaniec

---

### Post by robert@debian on 2007-07-02
Oh, thats really sad to hear. Coz I'd like to buy the 6224w aswell. 
It should be a Linux only machine though, however it seems very unstable ;-(

Can you please tell us in detail, whats the problem with the nVidia installation?
Could it be a configuration problem within the xorg.conf? Since the mouse 
seems to function at least a little bit ;-)

For the sound problem, there are probably no kernel modules loaded. 
Can you please check if the proper modules are configured in your kernel.

I hope you can get Ubuntu running as you wish.

---

### Post by jorma2010 on 2007-07-04
> **michel_iwaniec said:**
> ... but worked fine after I set the SATA HDD to compatibility mode in the BIOS setup. ....


For some reason I have not been able to install 7.04 to Zepto 6224w, no matter how I have played with the bios settings. Would you be kind enough to give me a hint what settings you changed in the bios in more detail. 
Thanks.

---

### Post by robert@debian on 2007-07-05
Well I don't know anything about the Zepto 6224w BIOS settings, since I have none. 
 
Didn't the installer recognise the HDD? You may want to try with **qtparted**, if there is something 
wrong.

---

### Post by michel_iwaniec on 2007-07-06
> **jorma2010 said:**
> For some reason I have not been able to install 7.04 to Zepto 6224w, no matter how I have played with the bios settings. Would you be kind enough to give me a hint what settings you changed in the bios in more detail. 
Thanks.
Do not take these words as fact, as I may have randomly changed other settings as well, but I do think that the crucial BIOS setting was going to Intel->ICH Control Sub-Menu->Integrated Device Control Sub-Menu->ICH Sata Pata Control Sub-Menu and changing the "SATA - Device 31, Function 2" field to "Compatible".

If this enables you to install Ubuntu, please tell me how the mouse cursor works on your machine.

---

### Post by jespdj on 2007-07-06
Hmmm. The Zepto laptops are really nice. I'm thinking of getting the 6625WD, which is quite similar to the 6224W.

Ofcourse these are Santa Rosa laptops full of brand new hardware, so you can expect for some things not to work. Lots of people are buying Santa Rosa laptops now so I'd expect there to be drivers for all this new hardware within a few months.

---

### Post by whirl on 2007-07-06
Oh man Im disappointed hearing this. 6224W was suppose to be my first laptop. I was thinking of buying it this fall and I was so excited that I wouldnt have to buy any windows for it and could just cleanly put ubuntu on it.. But I guess not. What a bummer :(

cheers for the info though and do tell us if things chance.

---

### Post by jorma2010 on 2007-07-08
> **michel_iwaniec said:**
> Do not take these words as fact, as I may have randomly changed other settings as well, but I do think that the crucial BIOS setting was going to Intel->ICH Control Sub-Menu->Integrated Device Control Sub-Menu->ICH Sata Pata Control Sub-Menu and changing the "SATA - Device 31, Function 2" field to "Compatible".

If this enables you to install Ubuntu, please tell me how the mouse cursor works on your machine.

Hi,

Thousand thanks, I had completely missed that menu on BIOS & after changing the setting I was able to install ubuntu, there were some complications though when installing:

Just after boot I had to change resolution to 1440x990 by pressing the f4

Then X failed to initialize & threw me to console, after I edited /etc/X11/xorg.conf to to use "vesa" instead of the nvidia driver I was able to get the graphical installation started.

I haven't yet tested how things work but at least wireless lan works out of the box. I have no problems with with cursor movement using the touchpad or external mouse. As a temporary solution try to use some other driver for X?

---

### Post by jorma2010 on 2007-07-09
I managed to install the latest NVidia drivers, 3D works ok, still no problems with mouse movement. Only thing that is bit more trickier to get to work is the sound card

---

### Post by crj on 2007-07-09
> **whirl said:**
> Oh man Im disappointed hearing this. 6224W was suppose to be my first laptop. I was thinking of buying it this fall and I was so excited that I wouldnt have to buy any windows for it and could just cleanly put ubuntu on it.. But I guess not. What a bummer :(

cheers for the info though and do tell us if things chance.

After contact with Zepto Computers I was informed that they don't support Linux. Unbelievable indeed! 

That explains why people have experienced problems to install Ubuntu on Znote 6224W. For me it has been quite impossible to install Ubuntu Feisty Fawn on my  brand new Znote 6625WD irrespective of BIOS settings and installation approach. In contrast I have installed Feisty Fawn on my HP Compaq NX 7000 without any problem.

Now I consider to buy a Dell computer dedicated to work with Ubuntu. More info is to be found at [http://direct2dell.com/one2one/archive/category/1021.aspx](http://direct2dell.com/one2one/archive/category/1021.aspx).

---

### Post by crj on 2007-07-11
After contact with Zepto's Swedish sales manager I was informed that Zepto's new computers, based on the Santa Rosa platform, follows the computer industry standard for this platform. Earlier message from the support department that Zepto does not support Linux, implied that Zepto does not give any software support concering Linux. As far as new Linux drivers are developed for the Santa Rosa platform Linux will work on the newest Zepto computers the sales manager told.

Until these drivers are realized I will try to instlall Ubuntu Feisty Fawn by means of the alternate installation CD that can be downloaded from Ubuntu. The installation procedure on Acer TravelMate 6292 is well described at

[http://ubuntuforums.org/showthread.php?t=497686&highlight=Santa+Rosa](http://ubuntuforums.org/showthread.php?t=497686&highlight=Santa+Rosa).

Hope this procedure will work on Zepto Znote 6625WD as well.

---

### Post by brolzwerver on 2007-07-11
Let us know if this works! I'm thinking of buying a Zepto, too...
It's a pity it is that hard to have Ubuntu running. : ( I hope new drivers will solve these problems soon!

---

### Post by michel_iwaniec on 2007-07-12
jorma2010:
Hmm, it seems really strange to me that the cursor problem appears on my machine and not on yours. Are you sure about this? To be more specific, the bug appears when if I move the cursor by "scratching the pad". That is, making a stroke over the pad to move the cursor, then lifting my finger from the pad and taking it back to a repeated stroke. This will sometimes make the cursor jump to another position. If I keep my finger firmly pressed on the pad at all times it never jumps around though.

It might be that my odd method of using the touchpad exposes this problem more than others do, but I find it odd if the bug cannot be reproduced at all on your machine. Have you tried moving the mouse around with the "scratch-method"?

I also suspect the bug may stem from the horrible "tap feature", which is enabled by default. I want to turn this one off, but running tpconfig just gives me the error message "could not open PS/2 port". Do you know how to get tpconfig working?

For the time being, I bought myself a cheap USB mouse which seems to remove the problem. I had a faint memory that it didn't when I had a chance to try that earlier, but that might have just been me tripping on the pad while typing. ;)

I just managed to install the Nvidia drivers btw. Have you managed to get the sound working as well? 

Last, I would like to ask you a personal favor. A big reason why I spent lots of extra cash on a Geforce 8-laptop was to be able to use Nvidia's CUDA. However, I have not been able to get CUDA working fully in XP. Programs that just run calculations work fine, but any program that uses graphics interoperability (i.e. drawing stuff in the same program) fails to work, and the Nvidia employees do not offer any help on this. 

I am thus hoping the Linux version of CUDA might perform better, but CUDA is "not officially supported for Ubuntu", and I'm too much of a Linux-newbie to be able to find out how to get things working on a different distribution, if it's at all possible. If you can manage to install and run the SDK samples and tell me how you did it, I would be very grateful. 

The CUDA webpage is located at [http://developer.nvidia.com/object/cuda.html](http://developer.nvidia.com/object/cuda.html)

---

### Post by odovacer on 2007-07-15
Hi!

I`ve just bought the 6224W, and wanted to try Ubuntu for the first time. But I`m getting an error that say something like this "failed to locate memresourcess" or something like it. Then it starts to load the ubuntu, and after it seems to finished loading the screen goes blank. I`ve set the SATA settings as "instructed" in this thread.

I`m a complete neewbie to linux and ubuntu, are there anyone who have experienced the same? Anyoen who has a sollution?

---

### Post by ilkkal on 2007-07-15
Hi!

I have Znote 6024W which is basicly the same laptop than 6224W, only the graphics card is different. I don't know about the nvidia problem, but I managed to install intel graphics driver and wlan drivers on gutsy (ubuntu 7.10) only. But still, at least you can get WLAN working.

The sound card isn't supported by ALSA yet. We have to wait for the next version of ALSA, sorry!

At the moment the sound is only thing on this laptop which doesn't work, so I'm pretty happy with this zepto.

---

### Post by digicomp on 2007-07-20
Hi all,

We will start Ubuntu support (from Ubuntu 7.10) in Finland on Zepto laptops (fi.zepto.com). The idea is to inform you dear Linux lovers what is working "out of the box" on each model and what has to be manually configured (with how-to's from us and hopefully also experienced users will share their knowledge with us all through this forum).

Forum support will start after Assembly in Helsinki (2.8.2007 [http://www.assembly.org/summer07/](http://www.assembly.org/summer07/)). For those who are interested we will present at least one Zepto model which is running Ubuntu 7.04 at ASM.

Comments and thoughts are as I said more than welcome!

Best regards,
DigiComp / Christian

---

### Post by jorma2010 on 2007-07-26
Hi,

Sorry for the bit late answer, been busy with work lately. Configuring audio to work for zepto 6224w seems to be possible with the patch found [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/116326/comments/61](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/116326/comments/61)

Just copy it over the original file, configure, make & install. Works perfectly.

---

### Post by nille on 2007-08-22
Thanks jorma! It works great, but I still think that the speakers won't be muted when you plug in your headphones. Maybe it'll get fixed before the official Gutsy-release, but it's not too certain, unfortunately.. :(

After some testing (not extensive, but at least some) I've found out that it's recommended to run Gutsy instead of Feisty on the Znote 6224W. I had a lot of slowdowns, hangups and misbehaviour using Feisty (especially when using the CD-drive) but that seems to be fixed in Gutsy! Yeah! :D

There's maybe a HOWTO coming up (I have written it, but it's for Feisty, and I'm not too fond of Feisty right now...), but I'll se what happens.

---

### Post by shador on 2007-08-23
> **digicomp said:**
> Hi all,

We will start Ubuntu support (from Ubuntu 7.10) in Finland on Zepto laptops (fi.zepto.com). The idea is to inform you dear Linux lovers what is working "out of the box" on each model and what has to be manually configured (with how-to's from us and hopefully also experienced users will share their knowledge with us all through this forum).

Forum support will start after Assembly in Helsinki (2.8.2007 [http://www.assembly.org/summer07/](http://www.assembly.org/summer07/)). For those who are interested we will present at least one Zepto model which is running Ubuntu 7.04 at ASM.

Comments and thoughts are as I said more than welcome!

Best regards,
DigiComp / Christian

Ok so now that it's over how did it work out. Any new info on what model that supports ubuntu?

---

### Post by puddu on 2007-08-27
I've just bought a Znote 6324W and i'm really interested to use Ubuntu on it. 
When it will be in my hands i will try to install and use it.

---

### Post by daller on 2007-09-09
Anyone having sound working on the Znote 6024W?

The card is:

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

How do I use the patch?

---

### Post by sebastiansjoberg on 2007-09-11
> **whirl said:**
> Oh man Im disappointed hearing this. 6224W was suppose to be my first laptop. I was thinking of buying it this fall and I was so excited that I wouldnt have to buy any windows for it and could just cleanly put ubuntu on it.. But I guess not. What a bummer :(

cheers for the info though and do tell us if things chance.

I've been running gutsy on my 6324W since middle/end of june. Everything works perfectly now except sound, which you have to compile yourself. It was a pretty rough ride in the beginning but now it's great. :)

---

### Post by daller on 2007-09-11
> **sebastiansjoberg said:**
> I've been running gutsy on my 6324W since middle/end of june. Everything works perfectly now except sound, which you have to compile yourself. It was a pretty rough ride in the beginning but now it's great. :)

How to i compile the sound-driver, or what it is you are referring to?

---

### Post by nille on 2007-09-11
I'm not sure about the 6324W, but on my 6224W I had to download the alsa-driver, alsa-lib and alsa-utils from the ALSA-Project:
[http://www.alsa-project.org/](http://www.alsa-project.org/)

Pick version 1.0.15 and then follow the "Update to the latest version of alsa"-instructions (replacing 1.0.14 with 1.0.15rc1):
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

After that I had to manually edit the file /etc/modprobe.d/alsa-base, adding the following line at the end of the file:
**options snd-hda-intel model=toshiba**

---

### Post by Lars Skovbo on 2007-09-12
Sorry to highjack, but i have problems with my Znote 6224W too. The problem is that when i have installed ubuntu/kubuntu (tried both) the system won't boot from the hdd. Only black screen with blinking courser and a busy hdd LED. Anyone had that problem?
Btw. i also had to use the vesa driver instead of nv, so i guess we have to wait for an updated driver. Some have gotten the 3d graphics working tho.

---

### Post by Lars Skovbo on 2007-09-12
I found a solution to my problem. The problem was that the hdd wasn't detected correctly in fisty. I downloaded gusty and followed a swedish guide to get the system installed... :guitar:
The trick is to press f6 in the cd bootmenu and add
```
all_generic_ide
```
to the parameter, and then your laughing :)

Kubuntu version i downloaded:
[http://cdimage.ubuntu.com/kubuntu/releases/gutsy/tribe-5/gutsy-alternate-i386.iso](http://cdimage.ubuntu.com/kubuntu/releases/gutsy/tribe-5/gutsy-alternate-i386.iso)

Swedish guide:
[http://www.ubuntu-se.org/drupal/node/345](http://www.ubuntu-se.org/drupal/node/345)

---

### Post by nille on 2007-09-12
That's my guide ;) Good to hear that it actually helped somebody!

I originally wrote it in english, but didn't know where to upload it, so I put a version in swedish on our swedish LoCo-website. If I find a great place to put the english version, I'll tell you!

Any suggestions on where to put it, btw?



The only things that I have yet not managed to get working is suspend (hibernate works, but is as slow as shutting down and reboot the computer, so it's not that usable). And the volume-buttons (Fn-F7 = mute, Fn-F8 = vol. down and Fn-F9 = vol. up) worked only for half a day in Xubuntu, but suddenly they stopped working, probably after a reboot..

Does anyone know anything about those problems?

---

### Post by Lars Skovbo on 2007-09-14
Oh that's great m8! :) About where to put the then English version i guess that's out of my league :confused:
KMix reacts when I press the mute/vol-up/vol-down buttons, so I guess they work on my pc... for now :lolflag: But I on the other hand have problems with getting the wifi up and running (this works in windows so a little tingeling needs to be done :))

---

### Post by jespers on 2007-09-18
I'm interested in getting a 6024W too.
But before I do it there's a few things I'd like clarified (if possible). So here are my questions.

Does anyone in here know if the following features work?
- hibernate and/or suspend
- bluetooth

Cheers :),
Jesper

---

### Post by martinrandau on 2007-09-18
Hi, I have a Zepto Znote 3415 with similar hardware to 6224W/6324W. I too can't get the sound to work.

I have tried to installed the latest alsa alsa drivers (15rc2) and adding model=toshiba at the end of /etc/modprobe.d/alsa-base, but this screws alsa up completely:

```
martin@znote3415:~$ sudo modprobe snd-hda-intel 
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.22-11-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

```
martin@znote3415:~$ dmesg | grep snd
[   33.731100] snd_hda_intel: disagrees about version of symbol snd_ctl_add
[   33.731230] snd_hda_intel: Unknown symbol snd_ctl_add
[   33.731372] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[   33.731496] snd_hda_intel: Unknown symbol snd_pcm_new
[   33.731639] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[   33.731774] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[   33.731916] snd_hda_intel: disagrees about version of symbol snd_card_register
[   33.732050] snd_hda_intel: Unknown symbol snd_card_register
[   33.732189] snd_hda_intel: disagrees about version of symbol snd_card_free
[   33.732313] snd_hda_intel: Unknown symbol snd_card_free
[   33.732450] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[   33.732587] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[   33.732739] snd_hda_intel: disagrees about version of symbol snd_card_proc_new
[   33.732875] snd_hda_intel: Unknown symbol snd_card_proc_new
[   33.733074] snd_hda_intel: disagrees about version of symbol snd_ctl_find_id
[   33.733204] snd_hda_intel: Unknown symbol snd_ctl_find_id
[   33.733369] snd_hda_intel: disagrees about version of symbol snd_ctl_new1
[   33.733493] snd_hda_intel: Unknown symbol snd_ctl_new1
[   33.733652] snd_hda_intel: disagrees about version of symbol snd_component_add
[   33.733787] snd_hda_intel: Unknown symbol snd_component_add
[   33.733930] snd_hda_intel: disagrees about version of symbol snd_card_new
[   33.734053] snd_hda_intel: Unknown symbol snd_card_new
[   33.734211] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages
[   33.734346] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[   33.734491] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl
[   33.734626] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[   33.734765] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages
[   33.734900] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[   33.735049] snd_hda_intel: Unknown symbol snd_ctl_elem_read
[   33.737649] snd_hda_intel: Unknown symbol snd_ctl_elem_write
[   33.737786] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops
[   33.737916] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[   33.738058] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_list
[   33.738193] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list
[   33.738338] snd_hda_intel: disagrees about version of symbol snd_device_new
[   33.738462] snd_hda_intel: Unknown symbol snd_device_new
[   33.738609] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all
[   33.738745] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[   33.738891] snd_hda_intel: disagrees about version of symbol snd_card_disconnect
[   33.739026] snd_hda_intel: Unknown symbol snd_card_disconnect
[   33.739162] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
[   33.739297] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[   33.739506] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
[   33.739641] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[   33.739777] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
[   33.739912] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step
[   77.040288] snd_hda_intel: disagrees about version of symbol snd_ctl_add
[   77.040300] snd_hda_intel: Unknown symbol snd_ctl_add
[   77.040378] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[   77.040383] snd_hda_intel: Unknown symbol snd_pcm_new
[   77.040461] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[   77.040466] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[   77.040536] snd_hda_intel: disagrees about version of symbol snd_card_register
[   77.040541] snd_hda_intel: Unknown symbol snd_card_register
[   77.040604] snd_hda_intel: disagrees about version of symbol snd_card_free
[   77.040609] snd_hda_intel: Unknown symbol snd_card_free
[   77.040667] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[   77.040672] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[   77.040736] snd_hda_intel: disagrees about version of symbol snd_card_proc_new
[   77.040741] snd_hda_intel: Unknown symbol snd_card_proc_new
[   77.040998] snd_hda_intel: disagrees about version of symbol snd_ctl_find_id
[   77.041003] snd_hda_intel: Unknown symbol snd_ctl_find_id
[   77.041384] snd_hda_intel: disagrees about version of symbol snd_ctl_new1
[   77.041390] snd_hda_intel: Unknown symbol snd_ctl_new1
[   77.041521] snd_hda_intel: disagrees about version of symbol snd_component_add
[   77.041526] snd_hda_intel: Unknown symbol snd_component_add
[   77.041602] snd_hda_intel: disagrees about version of symbol snd_card_new
[   77.041607] snd_hda_intel: Unknown symbol snd_card_new
[   77.042272] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages
[   77.042278] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[   77.042356] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl
[   77.042361] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[   77.042425] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages
[   77.042430] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[   77.042515] snd_hda_intel: Unknown symbol snd_ctl_elem_read
[   77.042600] snd_hda_intel: Unknown symbol snd_ctl_elem_write
[   77.042656] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops
[   77.042661] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[   77.042733] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_list
[   77.042739] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list
[   77.042821] snd_hda_intel: disagrees about version of symbol snd_device_new
[   77.042825] snd_hda_intel: Unknown symbol snd_device_new
[   77.042915] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all
[   77.042920] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[   77.043007] snd_hda_intel: disagrees about version of symbol snd_card_disconnect
[   77.043012] snd_hda_intel: Unknown symbol snd_card_disconnect
[   77.043068] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
[   77.043073] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[   77.043366] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
[   77.043371] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[   77.043424] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
[   77.043429] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step
[  104.342520] snd_hda_intel: disagrees about version of symbol snd_ctl_add
[  104.342531] snd_hda_intel: Unknown symbol snd_ctl_add
[  104.342632] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[  104.342637] snd_hda_intel: Unknown symbol snd_pcm_new
[  104.342716] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[  104.342720] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[  104.342791] snd_hda_intel: disagrees about version of symbol snd_card_register
[  104.342796] snd_hda_intel: Unknown symbol snd_card_register
[  104.342860] snd_hda_intel: disagrees about version of symbol snd_card_free
[  104.342865] snd_hda_intel: Unknown symbol snd_card_free
[  104.342924] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[  104.342930] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[  104.342994] snd_hda_intel: disagrees about version of symbol snd_card_proc_new
[  104.342999] snd_hda_intel: Unknown symbol snd_card_proc_new
[  104.343258] snd_hda_intel: disagrees about version of symbol snd_ctl_find_id
[  104.343262] snd_hda_intel: Unknown symbol snd_ctl_find_id
[  104.345929] snd_hda_intel: disagrees about version of symbol snd_ctl_new1
[  104.345935] snd_hda_intel: Unknown symbol snd_ctl_new1
[  104.346081] snd_hda_intel: disagrees about version of symbol snd_component_add
[  104.346085] snd_hda_intel: Unknown symbol snd_component_add
[  104.346161] snd_hda_intel: disagrees about version of symbol snd_card_new
[  104.346166] snd_hda_intel: Unknown symbol snd_card_new
[  104.347200] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages
[  104.347206] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[  104.347284] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl
[  104.347288] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[  104.347352] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages
[  104.347357] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[  104.347450] snd_hda_intel: Unknown symbol snd_ctl_elem_read
[  104.347535] snd_hda_intel: Unknown symbol snd_ctl_elem_write
[  104.347591] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops
[  104.347596] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[  104.347670] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_list
[  104.347675] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list
[  104.347757] snd_hda_intel: disagrees about version of symbol snd_device_new
[  104.347762] snd_hda_intel: Unknown symbol snd_device_new
[  104.347852] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all
[  104.347857] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[  104.347944] snd_hda_intel: disagrees about version of symbol snd_card_disconnect
[  104.347949] snd_hda_intel: Unknown symbol snd_card_disconnect
[  104.348004] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
[  104.348009] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[  104.348302] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
[  104.348307] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[  104.348361] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
[  104.348366] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step
[  220.947067] snd_hda_intel: disagrees about version of symbol snd_ctl_add
[  220.947079] snd_hda_intel: Unknown symbol snd_ctl_add
[  220.947157] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[  220.947162] snd_hda_intel: Unknown symbol snd_pcm_new
[  220.947240] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[  220.947245] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[  220.947315] snd_hda_intel: disagrees about version of symbol snd_card_register
[  220.947320] snd_hda_intel: Unknown symbol snd_card_register
[  220.947383] snd_hda_intel: disagrees about version of symbol snd_card_free
[  220.947388] snd_hda_intel: Unknown symbol snd_card_free
[  220.947447] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[  220.947452] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[  220.947516] snd_hda_intel: disagrees about version of symbol snd_card_proc_new
[  220.947521] snd_hda_intel: Unknown symbol snd_card_proc_new
[  220.947737] snd_hda_intel: disagrees about version of symbol snd_ctl_find_id
[  220.947742] snd_hda_intel: Unknown symbol snd_ctl_find_id
[  220.950850] snd_hda_intel: disagrees about version of symbol snd_ctl_new1
[  220.950858] snd_hda_intel: Unknown symbol snd_ctl_new1
[  220.950990] snd_hda_intel: disagrees about version of symbol snd_component_add
[  220.950995] snd_hda_intel: Unknown symbol snd_component_add
[  220.951071] snd_hda_intel: disagrees about version of symbol snd_card_new
[  220.951076] snd_hda_intel: Unknown symbol snd_card_new
[  220.952058] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages
[  220.952064] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[  220.952142] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl
[  220.952147] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[  220.952211] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages
[  220.952216] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[  220.952303] snd_hda_intel: Unknown symbol snd_ctl_elem_read
[  220.952390] snd_hda_intel: Unknown symbol snd_ctl_elem_write
[  220.952445] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops
[  220.952450] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[  220.952525] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_list
[  220.952530] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list
[  220.952611] snd_hda_intel: disagrees about version of symbol snd_device_new
[  220.952616] snd_hda_intel: Unknown symbol snd_device_new
[  220.952706] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all
[  220.952711] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[  220.952798] snd_hda_intel: disagrees about version of symbol snd_card_disconnect
[  220.952803] snd_hda_intel: Unknown symbol snd_card_disconnect
[  220.952859] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
[  220.952864] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[  220.953157] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
[  220.953162] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[  220.953215] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
[  220.953221] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step
```

Any ideas?

---

### Post by sebastiansjoberg on 2007-09-19
> **michel_iwaniec said:**
> Hi, I have just purchased my first laptop in many years, the Znote 6224W by Zepto Computers. (which for the notice seems to be identical to its sibling the 6324W, apart from the color)

However, the most annoying problem of them all is that the mouse cursor is "noisy", in the sense that it sometimes (far too often) jumps around when moving it. This makes it extremely frustrating to troubleshoot the other problems. I have briefly tested it with a USB mouse at a friend's place, and it seemed to give similar results. In XP, there are no problems of this kind.

...

Again, the problem with the jumping mouse cursor is the most severe. It feels pointless to even try to troubleshoot the other stuff until I have a working mouse cursor. Anyone who can help me get rid of this bug gets a digital hug.

// Michel Iwaniec

Hey Michel

I just started to have a little jumpy mouse cursor in the latest update i gutsy... I think this is due to the configuration of the synaptics touchpad. It's actually pretty easy to mess around a little bit with the settings via synclient or gsynaptics.

This is my current settings, just replace your Synaptics section in your xorg.conf with this and see if you like it.

```

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "true"
        Option  "LeftEdge"      "1500"
        Option  "RightEdge"     "5600"
        Option  "TopEdge"       "1200"
        Option  "BottomEdge"    "5000"
        Option  "FingerLow"     "18"
        Option  "FingerHigh"    "23"
        Option  "MaxTapTime"    "400"
        Option  "MaxTapMove"    "220"
        Option  "MaxDoubleTapTime"      "180"
        Option  "SingleTapTimeout"      "180"
        Option  "ClickTime"     "100"
        Option  "FastTaps"      "0"
        Option  "EmulateMidButtonTime"  "75"
        Option  "VertScrollDelta"       "60"
        Option  "HorizScrollDelta"      "0"
        Option  "VertEdgeScroll"        "1"
        Option  "HorizEdgeScroll"       "0"
        Option  "VertTwoFingerScroll"   "0"
        Option  "HorizTwoFingerScroll"  "0"
        Option  "MinSpeed"      "0.0822368"
        Option  "MaxSpeed"      "0.197368"
        Option  "AccelFactor"   "0.00164474"
        Option  "EdgeMotionMinZ"        "30"
        Option  "EdgeMotionMaxZ"        "160"
        Option  "EdgeMotionMinSpeed"    "1"
        Option  "EdgeMotionMaxSpeed"    "304"
        Option  "EdgeMotionUseAlways"   "0"
        Option  "UpDownScrolling"       "1"
        Option  "LeftRightScrolling"    "1"
        Option  "UpDownRepeat"  "1"
        Option  "LeftRightRepeat"       "1"
        Option  "ScrollButtonRepeat"    "100"
        Option  "TouchpadOff"   "0"
        Option  "GuestMouseOff" "0"
        Option  "LockedDrags"   "0"
        Option  "RTCornerButton"        "2"
        Option  "RBCornerButton"        "3"
        Option  "LTCornerButton"        "0"
        Option  "LBCornerButton"        "0"
        Option  "TapButton1"    "1"
        Option  "TapButton2"    "2"
        Option  "TapButton3"    "3"
        Option  "CircularScrolling"     "0"
        Option  "CircScrollDelta"       "0.01"
        Option  "CircScrollTrigger"     "0"
        Option  "CircularPad"   "0"
        Option  "PalmDetect"    "1"
        Option  "PalmMinWidth"  "10"
        Option  "PalmMinZ"      "200"
        Option  "CoastingSpeed" "0"
        Option  "PressureMotionMinZ"    "30"
        Option  "PressureMotionMaxZ"    "160"
        Option  "PressureMotionMinFactor"       "1"
        Option  "PressureMotionMaxFactor"       "1"
EndSection

```

---

### Post by nille on 2007-09-19
I think the Bluetooth works fine. At least I have used my Wiimote with Compiz Fusion without problem (Why? Oh, I just had to ;)).

Start a terminal and type **lsusb**, and hopefully your Bluetooth-device will show up. If it doesn't, try pressing Fn-F10 (the button with the Bluetooth-symbol on, that is). Then run lsusb again, and your bluetooth-device should be listed.

Then you can install some bluebooth-programs (bluez, or something, I think).

Good luck!

---

### Post by nille on 2007-09-20
Hello martinrandau!

There are some instructions in this thread:
[http://ubuntuforums.org/showthread.php?t=545318](http://ubuntuforums.org/showthread.php?t=545318)

And the most interesting in your case is probably this one:
[http://ubuntuforums.org/showpost.php?p=3392900&postcount=16](http://ubuntuforums.org/showpost.php?p=3392900&postcount=16)

Good luck!

---

### Post by nille on 2007-09-27
Since I still haven't managed to get suspend to work on my 6224W I filed a bug in lauchpad:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/144454]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/144454")

If you can't get suspend to work, please post the output from the following commands:

[B]dmesg
sudo dmidecode
lspci -vvnn
uname -a[/B]

(put them in a text file by running the commands as **command > command.log**)

And post the following logfile:
**/var/log/kern.log**

Read some more:
[https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend)
[https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI)

---

### Post by sebastiansjoberg on 2007-09-27
> **nille said:**
> Since I still haven't managed to get suspend to work on my 6224W I filed a bug in lauchpad:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/144454]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/144454")

If you can't get suspend to work, please post the output from the following commands:

[B]dmesg
sudo dmidecode
lspci -vvnn
uname -a[/B]

(put them in a text file by running the commands as **command > command.log**)

And post the following logfile:
**/var/log/kern.log**

Read some more:
[https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend)
[https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI)

I've got suspend and resume working but it's a bit buggy. NetworkManager seems to be compeletely confused... I've not investigated it further though. I believe the solution was to change the video repost options in bios and add the options that this page talks about: [https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend)

I have VIDEO_REPOST set to true... anyway it should work after that, at least you'll have a working screen.

---

### Post by sebastiansjoberg on 2007-09-27
> **sebastiansjoberg said:**
> I've got suspend and resume working but it's a bit buggy. NetworkManager seems to be compeletely confused... I've not investigated it further though. I believe the solution was to change the video repost options in bios and add the options that this page talks about: [https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend)

I have VIDEO_REPOST set to true... anyway it should work after that, at least you'll have a working screen.

Actually, I just tried it again and nothing works after resume... :( well, the screen resumes ok but there seems to be something wrong with the disk. I got loads of errors about busy inodes and stuff.

---

### Post by nille on 2007-10-03
Another 6224W-user told me to set "Video Repost" to "Disable", and that seems to have solved my suspend-problems! Great!

That is, change **from** Linux/Enable **to** Disable.

---

### Post by ilkkal on 2007-10-03
> **jespers said:**
> I'm interested in getting a 6024W too.
But before I do it there's a few things I'd like clarified (if possible). So here are my questions.

Does anyone in here know if the following features work?
- hibernate and/or suspend
- bluetooth

Cheers :),
Jesper

Both work for me. I have been using bluetooth link daily. I have dsl on my cellphone :)

---

### Post by Lars Skovbo on 2007-10-11
My laptop locks when i try to use hibernate and sleep, havent got the bluetooth working, not that i realy need it. If anyone have got a clue i'd like to know.

---

### Post by jandrews82 on 2007-10-23
Ubuntu 7.10 now installs as easily as ever on the 6224W with working sound, beautiful 3D desktop effects (i'm spinning my cubed desktop as I sit here) but the only problem you will have is if you order your Znote 6224W with the standard Atheros wireless card.  As of late, I have not been able to get this working using any of Atheros' apparently supported drivers (Madwifi) using any of the techniques suggested round the web.  If you can do without wireless connectivity for the moment then I recommend buying the 6224W extremely highly.

I have also used hibernate and it booted up and ran perfectly but haven't tried suspending.

I personally dual boot between Vista (for games and currently wireless access if no wired is available) and Ubuntu 7.10 for everything else.

Hope this helps.

---

### Post by Lars Skovbo on 2007-10-24
Actually it makes me sad ^^

---

### Post by Tom G on 2007-10-24
I have a suspend problem with my 6625WD, too.. Going INTO suspend ain't a problem, coming out gives a darn black screen, no video output whatsoever... Harddrive led is on, and stays on, and my laptop just won't resume...:mad:

Oh, and i DID do the modifications already (editing certain files)...

---

### Post by xdream on 2007-12-02
Hi!

Im new here and i was hoping to find a solution on how to install ubuntu 7.10 on my Zepto 6224w, i downloaded the 64-bit version and try to install it, it takes a while, and then shows a "window" because it can't find the right graphic driver and I put it in "low-graphic mode" and then after a couple of seconds I end up in the console??

What can i do?? I tried the BIOS thing and it changed nothing.. Sooo?

---

### Post by nille on 2007-12-02
Hello xdream!

I'm not quite sure what you mean. Is it a post- och pre-installation problem?

**If it's a pre-installation problem:**
I have not tried to install the 64-bit version, but you can always try to install Ubuntu using the [alternate-cd]("http://releases.ubuntu.com/gutsy/ubuntu-7.10-alternate-amd64.iso") instead of the LiveCD. In that way you'll eliminate the graphics card problem during installation, and it almost always works, no matter what graphics card you've got.

**If it's a post-installation problem:**
Make a backup of your xorg.conf and run the following command:
```
sudo dpkg-reconfigure xserver-xorg
```

Choose *vesa* and restart X (i.e. with **sudo /etc/init.d/gdm start** and/or **stop/restart**). Now you can install the proprietary driver if you want to. (This method could also be used if you really want to use the LiveCD).

---

### Post by xdream on 2007-12-02
> **nille said:**
> Hello xdream!

I'm not quite sure what you mean. Is it a post- och pre-installation problem?

**If it's a pre-installation problem:**
I have not tried to install the 64-bit version, but you can always try to install Ubuntu using the [alternate-cd]("http://releases.ubuntu.com/gutsy/ubuntu-7.10-alternate-amd64.iso") instead of the LiveCD. In that way you'll eliminate the graphics card problem during installation, and it almost always works, no matter what graphics card you've got.

**If it's a post-installation problem:**
Make a backup of your xorg.conf and run the following command:
```
sudo dpkg-reconfigure xserver-xorg
```

Choose *vesa* and restart X (i.e. with **sudo /etc/init.d/gdm start** and/or **stop/restart**). Now you can install the proprietary driver if you want to. (This method could also be used if you really want to use the LiveCD).

Thx for a fast reply ;)

Im trying to install with the liveCD. I would just try it out without messing with the unstable vista that i've got... So the problem is before the desktop gets on the screen with the liveCD boot..
Is there a version of the liveCD that I can use for my 6224w??

---

### Post by Lars Skovbo on 2007-12-03
Like nille said. Use the alternate install cd instad.  Theres no reason to waste your time trying to install from the liveCD! You dont have to remove vista, tho i think its easier to split the hdd in whatever pieces you want and then install the OS'es. Use the 32-bit version.

---

### Post by Bossieman on 2008-03-18
I run 8.04 Alpha on  my Znote 6224W and everything works perfect here. I was a little bit surprised that the sound works right out of the box now. Had to compile ALSA in 7.10.

Now 6224W seems like a perfect Ubuntu laptop.

---

### Post by Lars Skovbo on 2008-03-19
Hows the suspend working out for you?

---

### Post by Bossieman on 2008-03-19
> **Lars Skovbo said:**
> Hows the suspend working out for you?

It works great, but you need to have atleast as much swap as ram.

---

### Post by Lars Skovbo on 2008-03-23
Ok nice. Thanks for the tip.

---

### Post by motin on 2008-05-29
Guys, it would be AWESOME if you could rally a laptop testing report on the Zepto at [https://wiki.ubuntu.com/LaptopTestingTeam](https://wiki.ubuntu.com/LaptopTestingTeam)

That would really help any Ubuntu user considering the Zepto laptops... including me :)

---

### Post by Lars Skovbo on 2008-05-30
Hope to be able to do that after the exams

---

