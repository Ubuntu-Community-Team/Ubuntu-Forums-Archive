---
title: "How to get internal mic to work? (Toshiba Satellite L505D S5992)"
date: 2010-08-13
forum: Hardware
---

### Post by Comodín on 2010-08-13
I have a Toshiba Satellite L505D S5992 laptop, dualboot with Windows 7 64-bit and Ubuntu 10.04 64-bit. I installed the speed kernel of Ivanmmj: [http://ubuntuforums.org/showthread.php?t=1301101&page=8]("http://ubuntuforums.org/showthread.php?t=1301101&page=8")

Everything works fine, except the internal microphone, which is important to me as I use Skype a lot. Does anyone have the same problem, and better yet, a solution to this problem?

Another thing that occurs, which may or may not be connected to the mic problem, is that at boot I get the following error message:

> pci 0000:03:00.0: BAR 6: no parent found for of device [0xfffe0000-0xfff]
mount: mounting none on /dev failed: No such device
init: ureadahead main process (350) terminated with status 5 

shpchp 0000.00:01.0 Cannot reserve MMIO region

Any help would be very appreciated!

---

### Post by lidex on 2010-08-14
First, for mic problem, check this.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

Then go to 'Sound Preferences' to select and unmute your mic in 'Input' tab. 
Use Pulse Audio Volume Control (pavucontrol) to unlock stereo sliders for the mic in 'Input Devices' tab. 
Drag the right slider down to zero. The mic is a mono device.

From alsa documentation:
> Capture Problems
~~~~~~~~~~~~~~~~
The capture problems are often because of missing setups of mixers.
Thus, before submitting a bug report, make sure that you set up the
mixer correctly.  For example, both "Capture Volume" and "Capture
Switch" have to be set properly in addition to the right "Capture
Source" or "Input Source" selection.  Some devices have "Mic Boost"
volume or switch.

When the PCM device is opened via "default" PCM (without pulse-audio
plugin), you'll likely have "Digital Capture Volume" control as well.
This is provided for the extra gain/attenuation of the signal in
software, especially for the inputs without the hardware volume
control such as digital microphones.  Unless really needed, this
should be set to exactly 50%, corresponding to 0dB -- neither extra
gain nor attenuation.  When you use "hw" PCM, i.e., a raw access PCM,
this control will have no influence, though.

---

### Post by Marcelo Ruiz on 2010-08-14
I'm not an expert, but I had a similiar problem with a Toshiba M640.
Try to go to the realtek website and download the latest alsa pack: realtek-linux-audiopack-5.15
Follow UBUNTU instructions in the README file to install it.
I hope it helps!

Marcelo.

---

### Post by Comodín on 2010-08-17
Thanks a lot! I followed your advice by first installing the latest alsa pack, which I think I installed correctly. (Is there a way to check this?) 

Afterwards I installed GNOME ALSA Mixer and PulseAudio Volumecontrol and started trying out different settings. Two times I somehow got the mic to work with Sound Recorder and I could hear my voice played back. But every time I restarted I was literally back where I started. No mic, everything else working.  

My sound card has an ALC272 chipset and I read that more people have (had) problems with the mic and sound card. The frustrating thing is I don't remember what I did to make it work...

---

### Post by lidex on 2010-08-17
> **Comodín said:**
> Thanks a lot! I followed your advice by first installing the latest alsa pack, which I think I installed correctly. (Is there a way to check this?) 

Afterwards I installed GNOME ALSA Mixer and PulseAudio Volumecontrol and started trying out different settings. Two times I somehow got the mic to work with Sound Recorder and I could hear my voice played back. But every time I restarted I was literally back where I started. No mic, everything else working.  

My sound card has an ALC272 chipset and I read that more people have (had) problems with the mic and sound card. The frustrating thing is I don't remember what I did to make it work...
What are your motherboard specs:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

---

### Post by Comodín on 2010-08-18
The result of: **sudo dmidecode -t bios**

```
SMBIOS 2.6 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: Insyde Corp.
	Version: 1.10
	Release Date: 12/17/2009
	ROM Size: 2048 kB
	Characteristics:
		PCI is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
		EDD is supported
		Japanese floppy for NEC 9800 1.2 MB is supported (int 13h)
		Japanese floppy for Toshiba 1.2 MB is supported (int 13h)
		5.25"/360 KB floppy services are supported (int 13h)
		5.25"/1.2 MB floppy services are supported (int 13h)
		3.5"/720 KB floppy services are supported (int 13h)
		3.5"/2.88 MB floppy services are supported (int 13h)
		8042 keyboard services are supported (int 9h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		Targeted content distribution is supported
	BIOS Revision: 10.240
```

And: **sudo dmidecode -t baseboard**

```
SMBIOS 2.6 present.

Handle 0x0002, DMI type 2, 16 bytes
Base Board Information
	Manufacturer: TOSHIBA
	Product Name: Portable PC
	Version: Base Board Version
	Serial Number: None
	Asset Tag: No Asset Tag
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis: Base Board Chassis Location
	Chassis Handle: 0x0003
	Type: Motherboard
	Contained Object Handles: 0
```

---

### Post by lidex on 2010-08-18
Try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=auto 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by Comodín on 2010-08-22
Nope, didn't work either, but thanks for the effort. Apart from the mic not working, and the error message at boot, the Toshiba gets really hot using Ubuntu with speed kernel. I read that even this can be bypassed (tutning of visualization) but it's just not worth all the effort. I throw the towel in and sell this laptop and will never again buy a Toshiba. 

By the way, I'm not giving up on Ubuntu. I'm lovin'it. Am running Netbook Remix on my Acer Aspire ZG5 and Xubuntu on a old Armada M300.

---

### Post by lidex on 2010-08-22
Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---

### Post by Comodín on 2010-12-12
I had a long break, but finally installed 10.10 and without any ACPI problem as described before (wit 10.04). The sound, however, is still an issue. I can't capture, have done all of the above (including the bug report) and was hoping you would still help me.

---

### Post by lidex on 2010-12-12
> **Comodín said:**
> I had a long break, but finally installed 10.10 and without any ACPI problem as described before (wit 10.04). The sound, however, is still an issue. I can't capture, have done all of the above (including the bug report) and was hoping you would still help me.

You may want to check for a bios update.Can you post the link to the bug report please? And for me this:
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Comodín on 2010-12-19
BIOS is up to date, if there's an update I should receive an e-mail from Toshiba. But I checked and I have the most recent BIOS. Strange thing is that I tried out the Live-CD of Mint 10 (64 bit) and the microphone captured out of the box, Skype worked. Strange, because I thought they derived Mint 10 from Ubuntu 10.10... 

Methinks this is what you asked for?:

[http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh)

---

### Post by Comodín on 2010-12-19
So, I thought maybe the Mint 10 Live-CD is working because it's a newer kernel or something. I downloaded the Ubuntu Live-CD (64 bit) again, installed it on a USB stick and if I run Ubuntu from the USB my mic is working and I can capture and Skype!! But alas, as soon as I install Ubuntu I'm back where I started, changing all the parameters but to no avail. The mic won't capture.

Maybe it has to do with the comment I get before boot, the same one as in my first post, but only now this line:

> shpchp 0000.00:01.0 Cannot reserve MMIO region

---

### Post by IcarusR on 2010-12-19
> shpchp 0000.00:01.0 Cannot reserve MMIO region 

There is a but report on this here...

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/577842]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/577842")

Does the id 00:01.0 relate to your sound card by any chance ? 
Check output of 

```
lspci
```

---

### Post by lidex on 2010-12-20
> **Comodín said:**
> BIOS is up to date, if there's an update I should receive an e-mail from Toshiba. But I checked and I have the most recent BIOS. Strange thing is that I tried out the Live-CD of Mint 10 (64 bit) and the microphone captured out of the box, Skype worked. Strange, because I thought they derived Mint 10 from Ubuntu 10.10... 

Methinks this is what you asked for?:

[http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh)

No. That's the script, I need the output.

---

### Post by Comodín on 2010-12-20
Sorry Lidex, I'm pretty new at Ubuntu, although the date I joined this community says different. Hopefully you meant this: [https://docs.google.com/leaf?id=0ByumjUy1xvvvODVjY2I2NjMtNzhlZi00MmQ4LTg0NjgtMzRiNDc2YjM2OWU1&hl=es&authkey=CNWOur0B]("https://docs.google.com/leaf?id=0ByumjUy1xvvvODVjY2I2NjMtNzhlZi00MmQ4LTg0NjgtMzRiNDc2YjM2OWU1&hl=es&authkey=CNWOur0B")

I restarted my laptop to see if the numbers of the MMIO region warning are still the same. In my last post I just copied these numbers from my first post, when I was still using 10.04. So I thought I'd check it. For some strange reason this time it did not show this comment, it booted straight from Grub to the desktop without any alert. And guess what, I tried out the sound recorder, opened Pulseaudio and Alsa Mixer and it recorded my voice.

Afterwards I rebooted again and there was again unfortunately a (really quick) message of MMIO region, but I couldn't catch the numbers. And I booted again and again, always MMIO region warning and no capture.

How do I boot with the command line (and with which command) so that I can see the whole boot sequence?

How to check output of lspci??? #-o

---

### Post by lidex on 2010-12-21
That's it. Try this then.
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=auto 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

If you run this command in a terminal, you can see the last boot sequence:
```
dmesg | less
```
The above for scrolling, this next gives the whole thing at once:
```
dmesg
```
lspci is done the same way, simply enter the command in a terminal and press enter.

All your logs can be perused with log file viewer. It's good to have. The filename is gnome-system-log. To install:
```
sudo apt-get install gnome-system-log
```
Resides in the 'Applications>System>Administration' menu

---

### Post by Comodín on 2010-12-21
Something seems to have worked, by inserting the extra line in alsa-base.conf. As soon as I reboot and open PulseAudio, I click on *Input Device* and select *All Input Device*, I can see that the microphone is capturing sound. (Both **Front Right** slides are silenced, by the way.)

Unfortunately, as soon as I try to record with Soundrecorder, or change a setting with Alsamixer, the microphone freezes. I've tried this now several times. 

Thanks for the pointing out the existence of Log File Viewer, that comes in handy. The MMIO region comment seems to have something to do with r8187se, although I have a r8180?!? 

```
[   13.935656] udev[437]: starting version 163
[   14.014369] shpchp 0000:00:01.0: HPC vendor_id 1022 device_id 9602 ss_vid 1022 ss_did 9602
[   14.014374] shpchp 0000:00:01.0: Cannot reserve MMIO region
[   14.033273] r8187se: module is from the staging directory, the quality is unknown, you have been warned.
```

---

### Post by Comodín on 2010-12-24
The solution isn't the most elegant, but it works. I used the "solution" of uaaquarius in this post: [http://ubuntuforums.org/showthread.php?p=10144940]("http://ubuntuforums.org/showthread.php?p=10144940")

I added the extra line in alsa-base.conf and afterwards deleted Pulseaudio from Synaptic Package Manager. It worked and I can use Skype and record sound. Suddenly I have an extra slide in Alsa Mixer called Digital.

Thank you for your assistance!

---

### Post by Comodín on 2011-01-01
The reason I haven't marked this Thread as solved is that I'm still trying to get Pulseaudio somehow to work. The solution mentioned above does work, though the quality of recording is much lower than the few times I got it to work with Pulseaudio and furthermore, the sound adjust button on my laptop doesn't work anymore. 

Every suggestion is welcome. Now planning to try and change model in alsa-base.conf randomly and see to what results that might lead.

---

### Post by demon148 on 2011-01-28
Your laptop hosts a ATI radeon Mobile Graphics and I am quick coming to the conclusion that it is definatly subject to ATI based cards.

---

