---
title: "Boot process stops"
date: 2010-07-02
forum: Hardware
---

### Post by azangru on 2010-07-02
Hi guys! I desperately need your help!

I got a new machine with no OS preinstalled, specifically to install Ubuntu on it. Everything worked fine, Ubuntu recognized all the hardware, and I couldn't be happier, except for this extremely annoying glitch.

When I start up the computer, it gets to a point where it flashes a message in broken English: "detect drives none, no any drives found", and stops booting! No matter how many times I reboot, it gets to this point and boots no further. If, however, I get to BIOS and, without even changing anything there, press on "Exit without saving", the computer restarts and boots up normally. When I turn it off, it again won't boot.

I recorded the boot process on my phone camera. [Here's]("http://www.youtube.com/watch?v=ofiD6oaxOqM") what it looks like (there is actually no need to watch the recording past 30 seconds).

The model of the motherboard is ECS X58B-A2.
The booting sequence in BIOS is normal: hard drive first, then CD, then other media. Just in case, I disabled the option to boot via network.

Could you please advise what I should do?

Thanks!

---

### Post by robsoles on 2010-07-02
Sounds darn tricky, I got a question to try to move this along for you:

(To confirm answer to my question you should be able to set 'CD/DVD ROM' as first boot device in BIOS and then just consider if you see specified message before or after 'Boot CD/DVD ROM priority' message usually given in modernish machines!)

Question: Do you see the 'detect drives none, no any drives found' message before or after the BIOS has finished it's startup process? (By the time it checks for bootable CD/DVD is usually finished BIOS/POST process...)

What answer to this reveals is whether the message is issued by BIOS or by GRUB....


It sounds like an ASUS M/B to me, but none of the ones I look after at work or at home bomb like you describe - just have 'broken English' regarding what kind of HDDs the BIOS finds before going for 'system from media' boot.

(I googled ECS X58B-A2 to find manufacturer and blurbs of results didn't reveal it and we shouldn't have to work that hard - please be a little more specific about your hardware to get better help!!!)

---

### Post by azangru on 2010-07-02
I must apologize for being a little too rush. Soon after posting my question here I called the technical support service (since my machine is crisp new, and is covered by the warranty) and brought my machine there for diagnostics. As a result I can't answer any specific questions now, till the beginning of the next week. I'll post here when I get the machine back and report on the results of the tests.

What I can say in the meantime is that the motherboard wasn't produced by Asus, but by a Taiwanese company called Elitegroup ([here]("http://www.pcgameshardware.com/aid,680264/Elitegroup-X58B-A2-Core-i7-motherboard-with-OC-features/News/") is a brief review of it). And the strange English phrase after which the boot process stops is somehow related to a thing called JMicron, which, as I was told, has nothing to do with failure to boot.

That's all the information I have for now. Will most likely be back and bump this thread on Tuesday :)

---

### Post by dino99 on 2010-07-02
Asus dont make hardware now, only sell it with its name, packaging and support.

---

### Post by pete79 on 2010-07-02
i just updated ubuntu 20 mins ago and once i done the restart it wouldnt boot and said unknown command type, so i have had to use windows 7 to send this any help

---

### Post by robsoles on 2010-07-02
> **azangru said:**
> ... .  Soon after posting my question here I called the technical support  service (since my machine is crisp new, and is covered by the warranty)  and brought my machine there for diagnostics. ...

Mmmh, pity not to prove it's the hardware before rushing it back to the shop but it really did sound like a hardware issue - betcha they fix it either way and try to bill you if it's a software problem!

jmicron controller seems to declare 'no any drives exist!' when I boot those mobos with no IDE drives installed but I had one declaring a SATA drive for a while yesterday while I had three plugged into one machine for a while so I'm not sure what it's on about!

I think your thread will be well and truly hijacked by the time you get your MC back but it is your thread so don't hesitate to tell us how it went and mark the thread solved if you have a machine that persistently boots the OS of your choice.

> **pete79 said:**
> ... it wouldnt boot and said unknown command type, ...

Was there any text surrounding that? Can you boot off a LiveCD and go and look at /var/log/messages and perhaps search other logs in /var/log (like boot for example) for more info you could give us to work with?

> **pete79 said:**
> ..., so i have had  to use windows 7 to send this ..

If you don't like it that much you could have used a LiveCD with a more controllable and friendly OS on it ;).

---

### Post by azangru on 2010-07-06
> **robsoles said:**
> Mmmh, pity not to prove it's the hardware before rushing it back to the shop but it really did sound like a hardware issue - betcha they fix it either way and try to bill you if it's a software problem!

You turned out to be quite right: tech support guys couldn't find any fault with the machine. They made an educated guess, made some changes in BIOS, tested the machine under WinXP and said that it was all right.

Naturally, to do all this they deleted my Ubuntu install. After I got the machine back with changed BIOS settings and installed Ubuntu on it, it didn't boot from the hard drive at all. So, I reverted the BIOS settings to the initial ones by pressing F9 in BIOS (the "optimized" settings, as BIOS called it), and can now boot Ubuntu by calling up BIOS and exiting from it. Which means that I am now back at square one and need your advice more than ever.

---

### Post by robsoles on 2010-07-06
Can you look for and select 'failsafe settings' in BIOS and give that a whirl - let us know what happens for that one.

---

### Post by azangru on 2010-07-07
> **robsoles said:**
> Can you look for and select 'failsafe settings' in BIOS and give that a whirl - let us know what happens for that one.

I can't find anything like failsafe settings in this BIOS. The only option I see is "Load Default Settings". In fact, there is also an option to press F9 and load "Optimized settings", but General Help (F1) describes this key as loading "Default settings", so I am not at all sure that "Default Settings" are any different from "Default Optimised Settings".

Apart from that, as I said, I don't see any other options in BIOS.

---

### Post by robsoles on 2010-07-07
When I can I will press into BIOS settings on a couple of mobos I have control of that use 'jmicron' controllers.

I will try to find you some settings to 'play with' but in the meantime if the option to take 'default settings' in BIOS is different from the 'F9' thing then please try it out for at least one shot at booting!


The fact that the system needed 'tweaking' in BIOS by the 'shop' to make it boot in Windows may be an indication that the hardware isn't functioning brilliantly anyway.

I should be able to post back with further instructions/help within about 24 hours of now.

---

### Post by azangru on 2010-07-07
> **robsoles said:**
> I will try to find you some settings to 'play with' but in the meantime if the option to take 'default settings' in BIOS is different from the 'F9' thing then please try it out for at least one shot at booting!

I did. Nothing happened.

> **robsoles said:**
> The fact that the system needed 'tweaking' in BIOS by the 'shop' to make it boot in Windows may be an indication that the hardware isn't functioning brilliantly anyway.

Actually, I have only their conclusion that the system works under Windows. I don't know whether they had to tweak BIOS for that - I suspect they didn't. They changed one BIOS setting (having something to do with SATA2 - or was it SATA3, which I don't have anyway) and said that it might help. When they returned the machine to me, Windows had already been erased: since the machine was sold without any OS, they were not going to give me an OS free of charge.

---

### Post by robsoles on 2010-07-07
> **azangru said:**
> ...

Actually, I have only their conclusion that the system works under Windows. ... they were not going to give me an OS free of charge.

That's not a really fair way for them to conduct business. ... That is a Microsoft enslaved way of thinking according to my attitude to this stuff!


I found where to turn off extra jmicron stuff in an ASUS P6T the other day but I can't find it on the motherboards I can access since so I can't think of better settings to play with in BIOS right now.

The system has been blanked (apparently), please reset to defaults in BIOS and attempt to re-install Ubuntu of whatever variation you please - let us know the result you get from restarting after shot at reinstalling please!

---

### Post by azangru on 2010-07-07
> **robsoles said:**
> The system has been blanked (apparently), please reset to defaults in BIOS and attempt to re-install Ubuntu of whatever variation you please - let us know the result you get from restarting after shot at reinstalling please!

Basically, that's what I did: I brought the blanked machine back home and installed Ubuntu on it. Granted, I installed it on a system with one BIOS setting changed, but then I defaulted BIOS. Do you think I should try and reinstall Ubuntu again? I strongly doubt it will, by some miracle, work OK if it hasn't worked before.

Should I experiment with other Linux breeds? Can a different distro (OpenSUSE, for instance) be better suited for my hardware? Do they have any differences in grub, for example?

---

### Post by robsoles on 2010-07-07
Re-reading your initial post really makes it seem like this may be a hardware thing but should be entirely defeatable!

I have drank too much of the amber stuff and have to lay down for eight hours and when I wake I only have an hour or less to look at stuff and post what I think before I work for eight hours but I will follow this up till I admit that I give up or you say that we have found the answer!


Would you please have one last go at setting whatever kind of defaults in BIOS and then re-installing afresh - the mere fact that the installer CD is successful is an interesting indicator, from here we should press into boot logs and such the like but the hardware element of this issue is hard to ignore!

Sorry I can't stay online anymore today, gotta quit - brain is fuzzy enough and I will probably suggest doing something dangerous to someone if I don't quit about now!

---

### Post by azangru on 2010-07-07
Wow! I installed OpenSuse 11.2, and it seems to work. At least I restarted the computer several times, and all those time the system booted properly. After Ubuntu, It looks quite unfamiliar (even the Gnome version does), and doesn't have that novice-oriented feel that Ubuntu does, but what the heck, if it works and if I manage to configure it to my liking, I should be more than happy, right?

I also have another hardware-related question, which perhaps you could help me with. The fan is rather noisy, and it keeps working all the time (I believe, before I brought the machine back to the shop, the fan behaved more intelligently: it went quieter for some time, then noisier). I spotted a menu option concerning the fan in BIOS, something about smart fan behavior, I don't exactly remember the phrasing. It was disabled. Do you think, enabling it might help? Or is a noisy fan just something one should ignore and get used to?

---

### Post by azangru on 2010-07-07
OpenSuse seems to have its quirks... :-(
Now that we confirmed that it's most likely the grub issue, has it become any easier to find a good solution for Ubuntu?

---

### Post by robsoles on 2010-07-07
RE: Fan

Yes, enable the smart fan option but if it remains noisy then open the case and inspect the fan assembly that it is quite tight up against the CPU - if not and if unsure what to do then take it to the shop and ask them to kindly make it tight again.

RE: Grub2

I recently cloned a hard disk onto another drive thereby giving it the same UUID, then I tried to boot with both drives still plugged in and was not able to get the machine started unless I booted from a LiveCD or removed one of the drives.

Got a second hard drive in this machine?


I didn't think it relevant due the fact that your machine would boot when BIOS was visited but wouldn't boot straight from cold but there is a script ( [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) ) that shows boot information that can be used to figure why a system won't boot at all from a HDD that used to boot - just need to boot from an alternative like LiveCD and run the script.

If you re-install Ubuntu to the machine and the problem is still there maybe it is relevant to run that script although the fact it starts after BIOS visit makes me wonder if it will reveal the problem.

---

### Post by azangru on 2010-07-07
> **robsoles said:**
> RE: Fan

Yes, enable the smart fan option but if it remains noisy then open the case and inspect the fan assembly that it is quite tight up against the CPU - if not and if unsure what to do then take it to the shop and ask them to kindly make it tight again.

Yep, enabled it - the fan is much quieter now! :p

> I recently cloned a hard disk onto another drive thereby giving it the same UUID, then I tried to boot with both drives still plugged in and was not able to get the machine started unless I booted from a LiveCD or removed one of the drives.

Got a second hard drive in this machine?

Nope, only one.

> I didn't think it relevant due the fact that your machine would boot when BIOS was visited but wouldn't boot straight from cold but there is a script ( [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) ) that shows boot information that can be used to figure why a system won't boot at all from a HDD that used to boot - just need to boot from an alternative like LiveCD and run the script.

If you re-install Ubuntu to the machine and the problem is still there maybe it is relevant to run that script although the fact it starts after BIOS visit makes me wonder if it will reveal the problem.

After experimenting with Suse, I ended up breaking it (:p) and re-installed the much-more-familiar Ubuntu. The problem persists, but I think I have to restate it:

1. Boots are very unpredictable under Ubuntu: it may boot fine (and then I have time to catch the glance of some phrases telling that it had to kill plymouth), or it may hang up. What I wrote initially (that the system will always boot after visiting BIOS and just exiting from it) is no longer true: the system boots more predictably when during the first seconds of booting I press F11 (Boot order) and explicitly tell the machine to boot from the hard drive (which is the first option anyways).

2. There was no such issue on Suse 11.2 Gnome edition: it booted every time I restarted or started up the computer.

P.S. Actually, despite my two-year experience with Ubuntu I am still unfamiliar with its settings and I know next to nothing about the hardware. Please, treat me like I'm a novice.

---

### Post by azangru on 2010-07-07
Don't know if the screen output during a successful boot can be of any diagnostic help, but just in case - [here]("http://www.youtube.com/watch?v=mguyTrQPYoU") it is.

---

### Post by robsoles on 2010-07-07
That is at least interesting and the stuff that exits with errors no doubt holds clues but before pursuing those, can you download the script from that link I gave last, boot off a LiveCD and run the script off a pen drive (or something like that) and then post the resultant output from it?

The LiveCD should be able to connect you to the internet so you could access the forums here and post the results directly.

---

### Post by azangru on 2010-07-08
> **robsoles said:**
> can you download the script from that link I gave last, boot off a LiveCD and run the script off a pen drive (or something like that) and then post the resultant output from it?

I ran the script from Ubuntu installed on the hard drive. Does it matter? If it does, I'll repeat the procedure after booting from a LiveUSB.

Meanwhile, here is the output:


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   958,676,991   958,674,944  83 Linux
/dev/sda2         958,679,038   976,773,119    18,094,082   5 Extended
/dev/sda5         958,679,040   976,773,119    18,094,080  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        e4639d97-f96d-41be-9153-0decb1d5693a   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        a03cb464-586d-4db3-b1d7-39137527aa88   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set e4639d97-f96d-41be-9153-0decb1d5693a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set e4639d97-f96d-41be-9153-0decb1d5693a
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e4639d97-f96d-41be-9153-0decb1d5693a
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=e4639d97-f96d-41be-9153-0decb1d5693a ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e4639d97-f96d-41be-9153-0decb1d5693a
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=e4639d97-f96d-41be-9153-0decb1d5693a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e4639d97-f96d-41be-9153-0decb1d5693a
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=e4639d97-f96d-41be-9153-0decb1d5693a ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e4639d97-f96d-41be-9153-0decb1d5693a
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=e4639d97-f96d-41be-9153-0decb1d5693a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e4639d97-f96d-41be-9153-0decb1d5693a
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e4639d97-f96d-41be-9153-0decb1d5693a
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=e4639d97-f96d-41be-9153-0decb1d5693a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a03cb464-586d-4db3-b1d7-39137527aa88 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  28.0GB: boot/grub/core.img
  21.6GB: boot/grub/grub.cfg
  28.0GB: boot/initrd.img-2.6.32-21-generic
  28.0GB: boot/initrd.img-2.6.32-23-generic
    .1GB: boot/vmlinuz-2.6.32-21-generic
  28.0GB: boot/vmlinuz-2.6.32-23-generic
  28.0GB: initrd.img
  28.0GB: initrd.img.old
  28.0GB: vmlinuz
    .1GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

---

### Post by robsoles on 2010-07-08
The only problem I can spot in the output there is that for some reason there are 4 device references to HDDs that don't exist in your system.


OK, you seem handy with your video camera and I am determined to figure this out - please get your video camera out and video record every last page of your BIOS settings for me. I will sit through the video and see if I can spot stuff we can shut-off/disable (or even enable) in your BIOS to get through this.


Make me the video, post the link to your video and answer another question for me: Do you have a printer or other PC? (So you can print out my next post after I watch video or perhaps can IM or at least access forums while messing with BIOS)

---

### Post by azangru on 2010-07-08
> **robsoles said:**
> The only problem I can spot in the output there is that for some reason there are 4 device references to HDDs that don't exist in your system.

I think the four drives reporting "No medium found" are from the card reader on the front panel of this machine :)

I have a netbook available, so yeah, I can tinker with BIOS while having access to IM or forums.

I'll try to make that video of BIOS settings for you.

---

### Post by robsoles on 2010-07-08
Maybe we can save you the bother of making that Video by using something like Skype video, I gotta go to work now but I can probably even do it from there.

---

### Post by azangru on 2010-07-08
> **robsoles said:**
> Maybe we can save you the bother of making that Video by using something like Skype video.

I've already made the [[COLOR="Blue"]_video_[/COLOR]]("http://www.youtube.com/watch?v=s0vNTGw8MH8") :p Shot it on the phone camera, so it's far from perfect, but the BIOS options seem legible. I cycled through different BIOS settings; if something catches your eye or if I missed something, just let me know.

> I gotta go to work now but I can probably even do it from there.

We are terribly out of sync - it is already way past my bed time :)

---

### Post by robsoles on 2010-07-08
mmmh, it's a long video, will wait till home from work then. Quick preview of vid shows me you did your best to be thorough!

I will try to hold off spouting instructions till I've sat through it all the way at least once...

---

### Post by robsoles on 2010-07-09
OK, the video of your mobo BIOS settings was nearly entertaining as such things go.

I see you have HDD plugged into port 2 and Optical Disc plugged into port 4 on your SATA controller - pretty much shouldn't be important but for the sake of ruling things out could you please shift them to HDD on port 1 and CDROM on port 6.

Having all settings for HDDs under "Standard CMOS Setup" to AUTO should be fine.

Under "Advanced Setup" I see you have the HDD set as first boot item and whereas that should be a fine way to get your system to boot a few seconds sooner than having the optical drive first, would you please try booting a few times in a row with the optical drive (DVD ROM) set to be first boot item - am interested to know what effect this has on your booting experience.

"1st Boot Device         Optiarc DVD RW AD-7"
"2nd Boot Device        WDC WD50000AADS-00S9"
"3rd Boot Device        (IS IT POSSIBLE TO CHOOSE NONE/DISABLED?)"

For another experiment could you set "Boot Other Devices" to "No" for a couple of restarts and let me know if that seems to influence the problem - I imagine you know it is referring (or, IMOH, should be referring) to USB sticks and USB floppy drives that can boot.

(If you are going to run Virtual Machines on this machine later it could be worth something to enable "Intel VT-d", I'll risk being wrong without checking but by memory it is about virtualisation enhancements.)

Under "Integrated Peripherals" there may be some value in setting "SATA Configuration" to "AHCI" though your system may behave as if the HDD is not formatted after installing under "IDE" and then switching to "AHCI" - I haven't actually had this happen but one or two BIOS manuals I have read promise that their motherboard will do that - if you will ever set up a RAID (stripe, mirror, mirrored stripe - whatever) then it is worthwhile to set this to RAID now instead.

I didn't spot anything else that I'd immediately suspect of influencing your problem although bad timing etc for RAM can be a plague - I don't think that is going on.


Let me know how that goes, I have other suggestions to try stuff but I'd prefer to know the results of trying this stuff first.

---

### Post by azangru on 2010-07-09
> **robsoles said:**
> I see you have HDD plugged into port 2 and Optical Disc plugged into port 4 on your SATA controller - pretty much shouldn't be important but for the sake of ruling things out could you please shift them to HDD on port 1 and CDROM on port 6.

Pardon the stupid question, but do you mean you want me to get inside the machine, unplug some wires and plug them to different slots? To my shame, I have no experience whatsoever of handling computer hardware, and I am a bit scared to do that now.


It's funny that three or four last times in a row that I started up or rebooted the computer, it booted up without a hiccup (except for those error messages about killing plymouth). I wonder whether some miracle happened or was I just being lucky.

---

### Post by robsoles on 2010-07-09
> **azangru said:**
> Pardon the stupid question, but do you mean you want me to get inside the machine, unplug some wires and plug them to different slots? To my shame, I have no experience whatsoever of handling computer hardware, and I am a bit scared to do that now.

...

I do mean that but if you are at all nervous of it then skip it, nevermind - if you can be bold about it then roughly speaking (without viewing a picture of the motherboard) the 1st port is usually in the top left of the group and the last port is usually in the bottom right of the group - this rule may be broken a thousand times by a dozen or more manufacturers and you should just press me to look at a picture of mobo (no doubt all over internet already :)) and be more specific about your hardware if you are terribly interested in pursuing this.


> **azangru said:**
> ...

It's funny that three or four last times in a row that I started up or  rebooted the computer, it booted up without a hiccup (except for those  error messages about killing plymouth). I wonder whether some miracle  happened or was I just being lucky.

Not necessarily so much a miracle but the (rather slim) chance that some or other piece of code (whether 'firmware' in mobo or something in Linux boot stuff) was written to detect the failure you've been experiencing and modify a behavior which improves the chance of 'clean' booting - of course could be random chance that last four in a row were clean(ish).


Shut it all the way down and start up after minimum 10 second break a few times in a row and then pursue other changes I suggested above if problem returns - I'll be pleased enough if this problem is apparently miraculously solved but I won't be rushing down to my bookie to back that one!

It's my bedtime pretty much, hope day is going marvelously for you there - catch you (or at least your thread here) in about 8 hours.

---

### Post by azangru on 2010-07-09
Fifth consecutive successful boot in a row :p I'll just observe the computer's behavior for a while now. Maybe I'm in luck, for a change, and things have magically improved by themselves. Not very likely, but who knows?

---

### Post by robsoles on 2010-07-09
You may have changed a setting in BIOS accidentally (I think SMART was disabled for HDD when you first entered it in the video but enabling that isn't likely to have this effect).

If it doesn't give you the trouble again in the next week perhaps you will remember to come back and mark this thread solved - if you identify for sure what it was that did it for you then letting others know in this thread is a cool thing to do as well.

---

### Post by azangru on 2010-07-11
Nah, as today's failure to boot made it clear for me, it was just a chain of lucky coincidences :)
I changed the boot order in BIOS, as you recommended (CD-ROM > Hard Drive > No device) and will observe the system's behavior for some time. If nothing happens, I'll try the KDE version of Open Suse 11.3 due to be released in three days: I had partial luck with Open Suse 11.2 with Gnome desktop; perhaps, this time I will be luckier.

If not, I'll be back :p

---

### Post by robsoles on 2010-07-12
So, 20 hour mark, how is it going - still using above settings or moved onto next suggestion?

---

### Post by azangru on 2010-07-13
> **robsoles said:**
> So, 20 hour mark, how is it going - still using above settings or moved onto next suggestion?

Well, as I learned today, changing boot order to CD-ROM > Hard Drive > No device doesn't help.
I am overawed by the unpredictability of all this and by the between-distro variation. At least, OpenSuse booted without any error messages, and did so quite predictably. I'm thinking whether I should change the distro for a while and see how that goes. Perhaps, the most painless change would be Linux Mint, but since it's based on Ubuntu Lucid, I would be really surprised if it behaved differently.

---

### Post by robsoles on 2010-07-13
Ok, I'll look into plymouth if you don't specify I shouldn't bother - would be interesting to know if any earlier version of Ubuntu does a better job of smooth startups on this hardware. I really wish I had direct access to it because I just have this knack if I can I can directly access a system 'having a poor time of it'.

---

### Post by azangru on 2010-07-13
> **robsoles said:**
> Ok, I'll look into plymouth if you don't specify I shouldn't bother

Yeah, looks like the prime suspect.

---

### Post by robsoles on 2010-07-14
Been trying to find plymouth as your kind of culprit and one thread I was reading makes me think to ask if you follow the practice outlined in the post [*http://ubuntuforums.org/showpost.php?p=9170906&postcount=33*]("http://ubuntuforums.org/showpost.php?p=9170906&postcount=33") or do you set graphic options before updating after clean install etc etc?

---

