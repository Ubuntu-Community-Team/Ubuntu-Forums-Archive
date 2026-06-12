---
title: "Your Experiences With Ubuntu on HP DV2000T ?"
date: 2006-11-02
forum: Hardware &amp; Laptops
---

### Post by cwf on 2006-11-02
Hi folks,

I'm finally going to enter the notebook community and buy a DV2000T.

I'm all about Ubuntu and am asking people to share their experiences with Ubuntu on a DV2000T. Mainly about hardware compatibility (sound, wireless, webcam, etc.)

Thanks,
Siva

---

### Post by lots_of_entropy on 2006-11-20
Hi 

I recently got one too. It really like it. I run Edgy and
my key specs are:
- Intel(R) Core(TM)2 CPU T5600  @ 1.83GHz
- Nvidia GeForce Go 7200
- Intel ICH7-M chipset

What does not work:
- Alsa mixer controll:
  It does output sound but alsamixer only shows PCM and
  Master volume. Furthermore the headphone jacks and the
  build in microphone do not work.
- ACPI fan controll is missing. This means that the fan
  is running most of the time. It is quiet however it
  decreases the battery life and you cannot put it on
  soft surfaces when idle ... annoying.

Not tested:
- Bluetooth:
  Ubuntu detects the hardware and BT looks in working
  order.
- Modem: Well - I don't need it.
- Suspend to Disk and suspend to RAM:
  Worked a few times - however doesn't work right now ...
  ... still have to track this down - but seems possible.

Everything else:
- Works fine.

I really hope the above problems are corrected in the next ACPI and ALSA release. I googled for it and it seems that some reverse engineering is going on on this.

If you are a developer and you know more please let us know.

P.S.: The notebook fits almost perfectly in a 14" "Crumpler The Gimp" neoprene sleeve.

---

### Post by julioromano on 2006-11-21
I can confirm everything cwf said.
Same experience on a dv2172ea (european version of 2000t with core2duo 1.66, 1gb ram, 120gb hdd, geforce7200, webcam, wifi, bluetooth, ligthscribe dvd writer).

bluetooth works out of the box with edgy eft.
integrated webcam needs uvcvideo driver [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/) (you have to compile it by hand).

The next alsa release will surely address the audio issues.

However I'm not so sure that we will see better fan management.

I get 2 hours battery life with edgy eft.

Bye
Marco

---

### Post by sarc on 2006-11-23
I have the DV2000 and the webcam was working fine with Dapper...

Is there an easy howto on how to compile and install the driver?  Thanks!

---

### Post by heffo_j on 2006-11-25
I've just installed LinuxMint on my dv2000vt. LinuxMint is a re-badged U 6.10. 

I got the nvida working okay, the wireless is good, bluetooth seems okay although I haven't got around to actually transferring anything yet.

The webcam doesn't work. 

Dvd is fine (LinuxMint runs all the codecs from scratch - altough the RealPlayer didn't work so I installed MPlayer).

The battery seems to go forever, which is great. The screen immediately dims on battery power.

I get sound okay, but I can't get it to remember that it is shut off, so I get the start up sound even though I switch it off once running.

VMware doesn't recognise the video driver, so if I'm running another os though vmware it doesn't make the best use of the screen. I'm goig to load Mandriva 2007 as a virtual machine later. It is supposed to support nvidia drivers.

I'm overall very happy with Edgey/Linux Mint running on the dv200 series.

Regards
John

---

### Post by stragatto on 2006-11-27
All problems solved.:D 
With Dapper, no cam, no microphone. I found a driver (uvcvideo) still in alpha stage for the Microdia cam, I had some trouble to compile it (I had to set a symlink in order the makefile could find the kernel headers directory) ... but it was not working with 2.6.15 kernel. 
I was informed by a friend that the uvcvideo driver was ok if compiled versus 2.6.17, so i upgraded to Edgy, compiled the driver, and the cam was ok. 
Now the mic. Yesterday I installed some alsa-related packages:

libfltk1.1
alsamixergui
alsaplayer-esd
gnome-alsamixer
mpg123-alsa
alsa-firmware-loaders

When I started gnome-alsamixer, I could find that:
- The Master control was muted (and I unmuted it)
- The Capture control had an unchecked checkbox named Rec 
(and I checked it)

After that, I tried the Sound Recorder and - surprise! - the mic was working. After that, I installed skype and ... working, even if the test robot was claiming that my audio quality was not perfect (but anyway quite intelligible).

---

### Post by maddocks on 2007-03-22
I have a dv2000 everything works awesome!! camera, sound, the wireless card with the latest dscape drivers. The only thing not working is MS /pro reader the mmc reader works fine and future driver releases will support it. When I upgraded to feisty the uvcvideo driver now freezes any app trying to use it.

---

### Post by sarc on 2007-03-22
How did you get everything to work, expecialy the webcam?

---

### Post by penvzila on 2007-05-09
> **maddocks said:**
> I have a dv2000 everything works awesome!! camera, sound, the wireless card with the latest dscape drivers. The only thing not working is MS /pro reader the mmc reader works fine and future driver releases will support it. When I upgraded to feisty the uvcvideo driver now freezes any app trying to use it.


About the sound.... did it just work immediately or did you have to do something extra?  I have sound out of the speakers only, and when I patch alsa to fix that, I get bad distortion on the headphone jack.  If anyone has this laptop, please tell me how you resolved this, if you had it.

BTW, I'm using 64bit edgy.

---

### Post by lexarrow on 2007-05-26
About the sound, maybe [this]("http://ubuntuforums.org/showthread.php?t=455147") could help

---

