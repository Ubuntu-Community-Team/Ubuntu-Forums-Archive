---
title: "Need to compile sound drivers. How?"
date: 2010-02-09
forum: Hardware
---

### Post by Lord Stig on 2010-02-09
Hi. Apologies for a long post but I'm trying to keep it all relevant and give people as much info as possible in advance. I'm using Kubuntu 8.04 (for ATi video driver support reasons) but don't have any sound. The sound works under Windows XP and I've tried experimenting with KMixer and the ALSA mixer but had no joy. It's nothing really obvious like me plugging headphones/speakers into the wrong socket or anything.

I've read the comprehensive sound sticky in this forum but I got different results from those listed in pass or fail and got lost with where to go next.
I've determined that my (onboard) soundcard is a Realtex ALC260 and I understand I will need to compile the driver into the kernel to get this working (please correct me if I'm wrong but I've read that). Problem is, whatever instructions I follow I get stuck. I've never done something like this before.

I am at the stage where I have an ALSA sound driver from a .tar.bz2 file extracted. This driver's documentation specifically states it can be used for the ALC260.

I think my problem lies in not understanding how compiling works.

I tried to extract the bz2 file using Dolphin but it said there was an error in the archive. I read that bz2 is newer and less common than gz so I figured it might be a newer format than Dolphin on 8.04 can read.
I don't know how to use the command line to extract  the bz2 into /usr/local/src/ (I couldn't get bunzip2 [filename] to work (reports it cannot find filename), couldn't sudo apt-get install bunzip2 or bzip2 and couldn't find it in the add/remove programs). I installed p7zip instead but have same problems as with bunzip2. So in the end I booted into Mint, used it to extract the folder effortlessy and then booted back into Kubuntu.
I then opened the usr/local/src folder using Dolphin as root and pasted the extracted folder in there. Will that work? Now what?

There is a shell script on there (install.sh) but even though the permission for executable is set all that happens when I run from Dolphin is I get it opened in a text editor. If I navigate to the folder and try to execute it in a CLI (I don't know how - I've tried "install.sh", "install" and "./install" nothing appears to happen. I've tried "./configure" as the readme file says as part of the compilation procedure but nothing happens). On the offchance that it had in fact done something but not told me I typed in "make" but nothing happened and I realised I am completely lost. I'm not sure if "make" is supposed to be followed by something else!!!???

Help! Please! I've been blessed with out-of-the=box sound on my other PCs with various versions of Ubuntu, but Mint 7 doesn't play any sound either.

Some outputs for you:

"lspci -v":

```
carl@carl-desktop:/usr/local/src/alsa-driver-1.0.18a-5.09$ lspci -v
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
        Subsystem: Fujitsu Siemens Computers Unknown device 10cc
        Flags: bus master, 66MHz, medium devsel, latency 64
        Memory at <ignored> (64-bit, non-prefetchable)

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 99
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=70
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: d0000000-d00fffff
        Prefetchable memory behind bridge: c0000000-cfffffff
        Capabilities: <access denied>

00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA (prog-if 01 [AHCI 1.0])
        Subsystem: Fujitsu Siemens Computers Unknown device 10f5
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
        I/O ports at 8440 [size=8]
        I/O ports at 8434 [size=4]
        I/O ports at 8438 [size=8]
        I/O ports at 8430 [size=4]
        I/O ports at 8400 [size=16]
        Memory at d0409000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) (prog-if 10 [OHCI])
        Subsystem: Fujitsu Siemens Computers Unknown device 10d1
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at d0404000 (32-bit, non-prefetchable) [size=4K]

00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) (prog-if 10 [OHCI])
        Subsystem: Fujitsu Siemens Computers Unknown device 10d1
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
        Memory at d0405000 (32-bit, non-prefetchable) [size=4K]

00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) (prog-if 10 [OHCI])
        Subsystem: Fujitsu Siemens Computers Unknown device 10d1
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 20
        Memory at d0406000 (32-bit, non-prefetchable) [size=4K]

00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) (prog-if 10 [OHCI])
        Subsystem: Fujitsu Siemens Computers Unknown device 10d1
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
        Memory at d0407000 (32-bit, non-prefetchable) [size=4K]

00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) (prog-if 10 [OHCI])
        Subsystem: Fujitsu Siemens Computers Unknown device 10d1
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 20
        Memory at d0408000 (32-bit, non-prefetchable) [size=4K]

00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) (prog-if 20 [EHCI])
        Subsystem: ATI Technologies Inc SB600 USB Controller (EHCI)
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at d0409400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)
        Subsystem: Fujitsu Siemens Computers Unknown device 10d1
        Flags: 66MHz, medium devsel
        I/O ports at 8410 [size=16]
        Memory at d0409800 (32-bit, non-prefetchable) [size=1K]

00:14.1 IDE interface: ATI Technologies Inc SB600 IDE (prog-if 8a [Master SecP PriP])
        Subsystem: Fujitsu Siemens Computers Unknown device 10d1
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 8420 [size=16]
        Capabilities: <access denied>

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
        Subsystem: Fujitsu Siemens Computers Unknown device 10cf
        Flags: bus master, slow devsel, latency 64, IRQ 18
        Memory at d0400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
        Subsystem: Fujitsu Siemens Computers Unknown device 10d1
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=64
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: d0100000-d01fffff

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200] (prog-if 00 [VGA controller])
        Subsystem: Fujitsu Siemens Computers Unknown device 10cc
        Flags: bus master, 66MHz, medium devsel, latency 255, IRQ 19
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at 9000 [size=256]
        Memory at d0000000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at d0020000 [disabled] [size=128K]
        Capabilities: <access denied>

0c:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Fujitsu Siemens Computers Unknown device 10b1
        Flags: bus master, medium devsel, latency 64, IRQ 21
        I/O ports at a000 [size=256]
        Memory at d0100000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

0c:05.0 Network controller: RaLink RT2561/RT61 802.11g PCI
        Subsystem: Belkin Unknown device 700e
        Flags: bus master, slow devsel, latency 64, IRQ 22
        Memory at d0108000 (32-bit, non-prefetchable) [size=32K]
        Capabilities: <access denied>

```

And "aplay -l":
```
carl@carl-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC260 Analog [ALC260 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
carl@carl-desktop:~$

```

Thanks for sticking with me on this very long post. Many thanks if anyone can help me get this sorted.

---

### Post by IcarusR on 2010-02-10
For future reference this is how it is done...

Move tarball to /usr/local/src/

```
sudo cp tarball.tar.bz2 /usr/local/src/tarball.tar.bz2
```

```
cd /usr/local/src/
```

```
sudo tar xvjf tarball.tar.bz2
```

Now you should have extracted files in a subdirectory of /usr/local/src/

Before you can complie the source you need to install 'build-essential' which contains the compiler etc.

```
sudo apt-get update
```

```
sudo apt-get install build essential
```

Within the extracted source there should be a readme, or install file, find it & follow the instructions howto install.

---

### Post by Lord Stig on 2010-02-15
Thanks for the instructions. I've installed "build-essential".

Here's an extract pasted from the installation instructions, which I find hard to follow:
> Note: Ubuntu OS, please use manual install.
      Run commands need to add sudo at first words.   

Manual install:
Step 1. unzip source code
        tar xfvj alsa-driver-1.0.xx.tar.bz2

Step 2. Turn on sound support from kernel config 
	(soundcore module, default turn on)

Step 3. Complied source code
	a. cd alsa-driver-1.0.xx
	b. ./configure
	c. make
	d. make install
	e. alsaconf
	f. ./snddevices (Only kernel 2.4 does it)

Step 4. Edit your /etc/modules.conf or conf.modules depending on the distribution
 	(Please refer to the attached modules.conf)
	 
        snd-xxxx is the card ID.

	-- Azalia controller --ALC880 ALC882 ALC260 ALC262 ALC883 ALC885 ALC888
	   --- Intel ICH6 ICH7 ---------
               snd-hda-intel

        -- AC97 controller --ALC655 ALC650 ALC250 ALC255
           --- Intel ICH6 ICH7 , SiS 7012 and NVidia----------
               snd-intel8x0
           --- Via8233 Via686a  -------------------------------    
	       snd-via82xx
           --- ATI Chipset  -------------------------------
	       snd-atiixp

        Copy and paste this to the bottom of your /etc/modules.conf or /etc/modprobe.conf file.
	# ALSA portion
          alias char-major-116 snd
          alias snd-card-0 snd-xxxx     
        # OSS/Free portion
          alias char-major-14 soundcore
          alias sound-slot-0 snd-card-0
        # card #1
          alias sound-service-0-0 snd-mixer-oss
          alias sound-service-0-1 snd-seq-oss
          alias sound-service-0-3 snd-pcm-oss
          alias sound-service-0-8 snd-seq-oss
          alias sound-service-0-12 snd-pcm-oss

Step 5. reboot your machine

Step 6. Use the alsamixer the disable mute (All audio line default is mute)
        *Must to compile and to install the ALSA library and utility. (Use automatic install is already install)
        excute alsamixer


I don't know how to do step 2! That might explain why the following didn't work? Or have I got the syntax wrong anyway?
```
carl@carl-desktop:~/Desktop/x/alsa-driver-1.0.18a-5.09$ make
make: *** No targets. Stop.
carl@carl-desktop:~/Desktop/x/alsa-driver-1.0.18a-5.09$ make install
make: Nothing to be done for `install'.
carl@carl-desktop:~/Desktop/x/alsa-driver-1.0.18a-5.09$ make a
acinclude.m4  acore/        aoa/
aclocal.m4    alsa-kernel/  arm/
carl@carl-desktop:~/Desktop/x/alsa-driver-1.0.18a-5.09$ makefile
bash: makefile: command not found
carl@carl-desktop:~/Desktop/x/alsa-driver-1.0.18a-5.09$ make install
make: Nothing to be done for `install'.
carl@carl-desktop:~/Desktop/x/alsa-driver-1.0.18a-5.09$ alsaconf
bash: alsaconf: command not found
```

---

### Post by Lord Stig on 2010-02-16
By the way, in the same way that a generic, no-Compiz video driver seems to be chosen by the distro to get you up and running, is there an equivalent for sound? Something already in the kernel I could try to enable on my hardware?

---

### Post by spiritson on 2010-02-16
Hey!

Download the latest Realtek drivers from the following link  

[HTML]http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false[/HTML]

And follow the guide from this link :

[HTML]http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/[/HTML]

IN the guide above do not use "wget" steps skip them.
Instead extract the downloaded drivers from realtek website into "/usr/src/alsa"  directory and follow the guide correspondigly.

Your problem will be solved.

---

### Post by Lord Stig on 2010-02-16
Thanks spiritson.
Before I get started on this, is the process different for 8.04 Hardy? I know my profile says I'm using Karmic - and I am on my main machine - but this is a newer PC which uses Hardy because of its support for the old ATi video driver. Trying to get this one up and running, too!
I've tried searching for a hardy driver installation guide on the link you gave me (since the instructions do look more complete and very helpful) but not had any joy.
Don't want to try these instructions for Karmic and break Hardy!

Thanks for posting.

---

### Post by dabl on 2010-02-16
I'm not sure compiling a driver is necessary - it appears the HDA Intel driver, with an option, will work:

[http://ubuntuforums.org/showpost.php?p=6878453&postcount=3](http://ubuntuforums.org/showpost.php?p=6878453&postcount=3)

---

### Post by spiritson on 2010-02-18
sorry Lord stig had been sick for two days!!

The link which i gave does say KARMIC but it works well in hardy
after all you are just upgrading the ALSA drivers by a new compilation specific for your HARdy installation.

and as long as you follow the guide exactly no worries go on and enjoy the sound.

---

### Post by Lord Stig on 2010-02-22
Thanks spiritson.

I'll take a look at this soon. Didn't want you to think I had got it sorted and not bothered to thank you or anyone else or not marked it as solved!

---

### Post by Lord Stig on 2010-02-22
I followed your instructions and everything worked! 
I ran alsaconf and let it do its autodetecting/modifying config files etc. then navigated to usr/src/alsa and did aplay test.wav

At first I didn't think it had worked becuase the new ALSA driver was 1.0.22 and keying in cat /poc/asound/version after a full restart of PC still reported 1.0.16, but it does work so I'm thrilled!

Thanks very much to spiritson and dabl for their time and effort!!

---

