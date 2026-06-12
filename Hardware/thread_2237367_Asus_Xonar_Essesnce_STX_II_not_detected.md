---
title: "Asus Xonar Essesnce STX II not detected"
date: 2014-08-01
forum: Hardware
---

### Post by redrumrogue on 2014-08-01
Hi folks,

I've just bought an Asus Xonar Essesnce STX II sound card for my machine, running Ubuntu 14.04.1.  Installed it in the PCI Express slot on my mobo and ... the card is not detected.  Only after buying the card I saw on the ALSA supported sound card list that the Xonar Essence STX is supported but the new STX II is not on the list [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Asus](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Asus)

I hate to think that the card is simply not supported AT ALL ... this could mean moving back to Windows when I've become so fond of Ubuntu (and linux in general).  I'm just wondering if anybody else has had this issue and/or can offer some solution to get it working?  Do I perhaps need to manually load some kernel module or something?

Any help troubleshooting would be much appreciated.

BR - Justin

---

### Post by slimsbims on 2014-08-02
Hello redrumrogue,

Stupid question: Did you plug in the additionally required power cable into the soundcard? Because this could explain this behaviour. 

As I use the STX, and the STX II is technically as to my understanding quite similar, and also Ubuntu 14.04, the card is normally instantaneously recognized by the system. Alternatively, may I suggest you try another PCIx-slot?

---

### Post by redrumrogue on 2014-08-03
Hi slimsbims!  Thanks for the reply.  Yes, I've got a 4 pin molex connected (and also the front panel audio connector).  I initially plugged the card into a spare PCIx x 16 slot and ubuntu did seem to recognize an extra audio device which showed up as an HDMI device - is this what you've seen on your machine with your STX?.  It seemed flakey though in that one minute it was in the list of audio devices and then next time i opened the audio settings it wasn't ... also seemed to appear and disappear after reboots.  I couldn't make any sense of it.  On top of that I was getting no sound out of it at all even when I was able to select it as the audio device to use.  So i ended up taking the card out of the PCIx x 16 slot and putting it into the smaller PCIx X 1 (as it's labelled in my mobo manual).  This has resulted in the card not being detected at all.

After trying all of this I ended up taking an image of my hard drive to back up ubuntu, and installing Windows 8.1 so I could install the drivers from the CD.  I wanted to check if the card was actually working or not.  After installing the drivers in windows I noticed the card making a few clicking noises during boot-up (still plugged into the small PCIx x 1 slot).  I hope this noise is normal - does your STX make any noises during boot-up?  I actually got no sound out of the card even in Windows but I've read on other forums that people have had this issue at first and had to change some settings in the software delivered with the card.

I'll trying switching to a different PCIx slot again just to check.

---

### Post by Vladlenin5000 on 2014-08-03
You may need to change something at BIOS also (and before anything else). In some scenarios the add-on card won't be recognized unless explicitly selected as such in BIOS/UEFI settings along with disabling the onboard one. That would explain why it isn't working in Windows either.

The HDMI device you noticed as nothing to do with your new card or the onboard one. It is the audio chip in you graphics card which may or may not appear listed depending on whether there's a HDMI cable connected or not.

---

### Post by slimsbims on 2014-08-03
Hello redrumrogue,

Firstly, Vladlenin5000 might be right. In Windows you could also check if the default output-device is not the interal soundcard, but the STX II. What mainboard are you using?

Regarding the clicking: Yes, this is normal on these cards, these are little relays working which is a sign of quality used in the components. It prevents the "plopp" in the loudspeakers when turning on or off or rebooting the PC.

In Linux, you could type "alsamixer" in the terminal (press <Ctrl>+<Alt>+<t>), and check with <F6> if the card appears there?

---

### Post by redrumrogue on 2014-08-03
Guys - thanks for your suggestions.  My motherboard is an Asus Sabertooth 990fx r2.0.  I'll get into the bios later and see if I can find any options to disable the sound from the motherboard.  At the moment alsamixer doesn't show the sound card, only the motherboard and nvidia graphics card audio.  But I've still got the STX II plugged into the small PCIx x 1 slot so I'll move it to one of the other slots as well and see what happens.  Will report back soon.

---

### Post by slimsbims on 2014-08-03
Hello redumrogue,

I googled a bit, and I think Vladlenin5000 is perfectly correct. Check in your bios, if the slot you put in the card has been set "enabled". Here a quote from tomshardware.com with a person also with sabbertooth and the STX:

[http://www.tomshardware.com/forum/342705-28-asus-xonar-essence-detected-help]("http://www.tomshardware.com/forum/342705-28-asus-xonar-essence-detected-help:")

Man i had the very same problem with my card  it was like no power was  going to the card but what it was just a setting for the pciex1 slot  it  wouldnt even load the drivers because my motherboard Asus Sabertooth  Z77 didnt recognized the card but i had a guy figure it out for me it  was a setting in the bios it was like the pci-e x1 slot i choose to use  was disabled..if im not mistaken when you plug the card in you have to  go into the bios and asign that slot to your card...soon as it was done  the drivers took off and loaded...Tell you that card can be a real bitch  to install..

---

### Post by redrumrogue on 2014-08-03
Still no luck so far ... i just put the card in a different PCIx slot, also found out how to disable the motherboard audio.  Now in Ubuntu the nvidia audio is being detected and STX II is still not detected (looking at alsamixer F6 option).  The weird thing is that when i booted this machine up with windows 8.1 i heard the STX II clicking during boot but with Ubuntu i'm hearing nothing.  It's almost as though there is no power going to the card when booting into Ubuntu?  I've double, triple, quadrouple checked the power connected on the card and it seems fine. One thing I have found is that if I run "lspci -v" in the terminal I get this amongst the results ...

 07:04.0 Multimedia audio controller: C-Media Electronics Inc CMI8788 [Oxygen HD Audio]
    Subsystem: ASUSTeK Computer Inc. Device 85f4
    Flags: medium devsel, IRQ 10
    I/O ports at b000 [disabled] [size=256]
    Capabilities: <access denied>

I believe this is the new card.  Anyone know what "I/O ports at b000 [disabled]" means?  And "Capabilities: <access denied>"??

---

### Post by slimsbims on 2014-08-03
Hello redrumrogue,

What I can confirm is that this is the card. For the output, sorry, I cannot help. Did you check to enable the PCIx-Slot in the BIOS? To me it seems it is not activated, and Windows maybe overriding the BIOS-settings, while Ubuntu maybe follows the BIOS-settings? Alternatively, maybe try (if possible) disable the UEFI mode and try booting in legacy mode?

Does it make sense to update the BIOS? Or alternatively, try booting with the pre-set BIOS-values? For any reason, I would look in the BIOS to resolve this issue.

---

### Post by redrumrogue on 2014-08-04
Hi slimsbims - at least the lspci command output suggests that the card and PCIx slot are physically OK ... otherwise I assume the card wouldn't have been listed under lspci.  So ... it's got to be either a BIOS setting or the driver is not being loaded during boot.  As far as BIOS settings go I haven't been able to find any way of enabling / disabling specific PCIx slots.  I've only found a way of disabling the motherboard sound, and that's made no difference.  I've flashed the BIOS with the latest firmware update as well.  No offence but I highly doubt booting with pre-set BIOS settings will help as I've not really changed a lot in the BIOS except for fan speed profiles and CPU power settings.  I guess I really need to get this card working under windows first to be absolutely sure it's not faulty.  I'll be all over this tonight when I get home from work!

---

### Post by Yellow Pasque on 2014-08-04
I don't think it's supported. The PCI ID (85f4) should probably be in this file: [https://github.com/torvalds/linux/blob/master/sound/pci/oxygen/virtuoso.c](https://github.com/torvalds/linux/blob/master/sound/pci/oxygen/virtuoso.c)

Send mail to the address here to inquire whether this card will be supported: [https://lists.sourceforge.net/lists/listinfo/alsa-user](https://lists.sourceforge.net/lists/listinfo/alsa-user)


> I believe this is the new card. Anyone know what "I/O ports at b000 [disabled]" means? And "Capabilities: <access denied>"?? 
The Ports might be disabled because no driver is loaded and <access denied> means you didn't use sudo.

---

### Post by slimsbims on 2014-08-04
Hello redrumrogue,

Sorry to hear it is still not working. One last idea came to my mind: You could try and boot with the live-DVD of Ubuntu. Normally, the DVD also activates the STX. So in case it does not, maybe the card is broken, or, if it does, your Ubuntu-installation might be having a problem and you could resolve the non-recognizing-issue by simply re-installting the system, if this would not be too much hassle. Sorry for not being able to provide more input. :(

---

### Post by redrumrogue on 2014-08-05
Update:  I got my STX II working under Windows 8.1 last night (at 2:30am!!) using the standard windows drivers downloaded from Asus website.  It worked without making any changes in the BIOS.  For me this confirms that the card is not yet supported by Ubuntu / ALSA .... now my choices are:

1.  to either return the card and get a supported one
2.  stick with Ubuntu and wait for drivers to roll in
3.  move to Windows and wait for linux drivers .............. (would rather not!)

Thanks for all your help guys - much appreciated.

---

### Post by slimsbims on 2014-08-05
Hello redrumrogue,

May I suggest in case you opt for option 2) to contact [https://lists.sourceforge.net/lists/listinfo/alsa-user](https://lists.sourceforge.net/lists/listinfo/alsa-user) as Temüjin proposed?

In case you decide for option 1), I can tell you the STX is working out of the box.

May I also suggest you involve the Asus-support, filing a bug-report? In my opinion I do not see a reason that they sell a premium product without drivers for Linux.

---

### Post by slimsbims on 2014-08-09
Hello redrumrogue,

supported in kernel 3.17:

[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Asus](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Asus)

---

### Post by redrumrogue on 2014-08-09
Interesting!  Looks like it may be a while before Ubuntu uses kernel 3.17 or higher ....  I'm actually in the process of compiling kernel 3.16 on a VM.  Never done it before and just curious as to what Sound card driver options there are. Doesn't look like 3.17 is even available yet :-(

---

### Post by redrumrogue on 2014-09-05
I just compiled kernel 3.16.2 from kernel.org and the Xonar STX II is now detected and working perfectly!

---

