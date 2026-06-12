---
title: "HP Pavilion dv5t Compatibility Information"
date: 2008-12-04
forum: Hardware
---

### Post by egawrangler on 2008-12-04
[SIZE="4"]HP Pavilion dv5t Compatibility[/SIZE]
(Intrepid Ibex)

I'm starting this thread as a repository for compatibility information, for the HP dv5t series laptops.  This is a list of the major end items.  I've omitted the System Bus, Floppy/HD Controller, PCIe controller, etc that are natively supported in the OS.  Format is outlined below.  If you've got updates/tutorials/whatever, please just post it and I'll update this (original) post so that googler's don't have to mess with 50 pages of discussion.  Additionally, if I've got any of the hardware specs wrong, be sure to flag that as well.

LAST UPDATE: 090414


[SIZE="3"]JMicron JMB38X Card Reader[/SIZE]
Supported?: Yes
Package: Native
Notes:

[SIZE="3"]Power Subsystem (Intel Cantiga PM45)[/SIZE]
Supported?: Yes
Package: Native (ACPImap)
Notes: Suspend/Standby has issues with nVidia graphics cards, edit "/etc/default/acpi-support" and set flag "POST_VIDEO=false" so that
       laptop will successfully enter standby.  However, resume will cause a restart.
Fix: [here]("http://www.linlap.com/wiki/HP+Pavilion+dv5-1000+Series")
Contributor: [Aussieartist]("http://ubuntuforums.org/member.php?u=730350"), [snowguy]("http://ubuntuforums.org/member.php?u=589821")

[SIZE="3"]Intel GMA X4500[/SIZE]
Supported?: Yes
Package: Intel xf86 Open Source, [http://intellinuxgraphics.org/download.html](http://intellinuxgraphics.org/download.html)
Notes:

[SIZE="3"]nVidia 9600M GT/9200M GS (NB9P-GS, NB9M-GEB)[/SIZE]
Supported?: Yes
Package: Native, Restricted Drivers
Notes: Intrepid includes the 176/177 packages from Nvidia, as restricted drivers options
Recommendations: Latest release (180.44) from nVidia.com 1) Ctrl-Alt-F1 2) "sudo /etc/init.d/gdm stop" 3) "sudo sh ./nVidia_package_filename"

[SIZE="3"]Realtek RTL8168C Network Interface[/SIZE]
Supported?: Yes
Package: Native, 8168C/8111C (r8169)
Notes:

[SIZE="3"]HP Webcam (Ricoh)[/SIZE]
Supported?: Yes
Package: Native, video4linux
Notes: Tested with VLC, Ekiga, Skype 2.0
Contributor: [Aussieartist]("http://ubuntuforums.org/member.php?u=730350")

[SIZE="3"]Intel Wi-Fi Link 5100 802.11a/b/g/n[/SIZE]
Supported?: Yes
Package: Native
Notes:

[SIZE="3"]Broadcom 4321 802.11a/b/g/n[/SIZE]
Supported?: ?
Package: ?
Notes:

[SIZE="3"]Validity Systems VFS101 Fingerprint Reader[/SIZE]
Supported?: No
Package: None
Best Hope: fprint, [http://www.reactivated.net/fprint/wiki/Unsupported_devices](http://www.reactivated.net/fprint/wiki/Unsupported_devices)
Notes:

[SIZE="3"]Ricoh IEEE 1394a Device[/SIZE]
supported?: ?
Package: ?
Notes:

[SIZE="3"]Agere HDA Modem[/SIZE]
Supported?: Yes
Package: Native
Notes:

[SIZE="3"]AverMedia A317-B  (NXP SAA7136E chipset) Hybrid TV Tuner Card[/SIZE]
Supported?: No
Package: None
Best Hope: Released source code, [here]("http://jusst.de/hg/saa716x/rev/a5dc0309adc7"), and [here]("http://ubuntuforums.org/showthread.php?t=785240").
Notes: This TV tuner uses the Phillips 7160 chipset

[SIZE="3"]IDT Integrated Audio[/SIZE]
Supported?: Yes
Package: Native
Notes: Mute button on touchpanel works, audio slider does not, SP/DIF out port is untested

[SIZE="3"]High-Definition Multimedia Interface (HDMI) v1.3[/SIZE]
Supported?: Somewhat
Package: None
Notes: nVidia driver set works and supports HDCP/auto-negotiation, audio is currently unsupported

[SIZE="3"]QuickTouch Buttons[/SIZE]
Supported?: Somewhat
Package: None
Notes: Kernel message handling appears to support mute button and wireless button, volume slider and play/pause/quickplay/etc not working

---

### Post by Aussieartist on 2008-12-29
Thank you for starting this thread... :P
I'll subscribe and contribute in any way I can.

I believe the Ricoh webcam is supported... Mine works with Intrepid. BUT is this the only webcam HP used for the dv5t?

BTW I have started thread to add:
[http://ubuntuforums.org/showthread.php?t=1025192]("http://http://ubuntuforums.org/showthread.php?t=1025192")
(It's about trying to get the dv5t webcam to work with Virtualbox.)

Cheers
Aussie

---

### Post by egawrangler on 2008-12-30
Updated, THANKS!!!

---

### Post by gm__ on 2008-12-31
Hi

Ive got a dv7 1050ef, same serie like the dv5 only 17" and my HDMI works,
though a bit buggy. Had to find out in administration/NVIDIA X server settings how to put it out on my tv screen.

You forget about the audio, working too. You cant find driver for Windows XP but its working under Ubuntu. Thats really great.

This thread is a great idea.

---

### Post by egawrangler on 2008-12-31
> **gm__ said:**
> 
You forget about the audio, working too. You cant find driver for Windows XP but its working under Ubuntu. Thats really great.



Do you mean the HDMI digital audio output or the IDT on-board audio system? ... Thanks!

---

### Post by gm__ on 2008-12-31
I meant the driver for the IDT on-board audio system.
Everybody's looking for it because HP isnt supporting XP and everybody wants to downgrade Vista to XP.

But the audio driver prevents everybody for doing so.

---

### Post by egawrangler on 2008-12-31
> **gm__ said:**
> I meant the driver for the IDT on-board audio system.
Everybody's looking for it because HP isnt supporting XP and everybody wants to downgrade Vista to XP.

But the audio driver prevents everybody for doing so.

Well, I've actually had plenty of success installing XP onto my dv5t, including the IDT audio package.  A simple tutorial can be found [here]("http://forum.notebookreview.com/showthread.php?t=291787").  In short, the IDT audio package has a mere few "vista-only" extensions that won't work on XP.  However, they are all related to older direct audio dependencies so most people shouldn't have a problem.

There are a few things I've never gotten to work under XP though:
1) Power Management for nVidia GPU
2) QuickPLAY button
3) Fingerprint reader software (must upgrade to DigitalPersona Personal 4.0 to use the reader in XP)

Hope that helps....thanks for contributing!  Send me a mesage if you need help installing anything in XP, as I'd like to keep this thread Linux related only....

---

### Post by 2hot6ft2 on 2008-12-31
Actually hp has a forum now and it's hopping with people switching from vista to xp and they'll help with drivers. [http://h30434.www3.hp.com/psg/?category.id=Notebook](http://h30434.www3.hp.com/psg/?category.id=Notebook)

---

### Post by egawrangler on 2008-12-31
> **2hot6ft2 said:**
> Actually hp has a forum now and it's hopping with people switching from vista to xp and they'll help with drivers. [http://h30434.www3.hp.com/psg/?category.id=Notebook](http://h30434.www3.hp.com/psg/?category.id=Notebook)

Thanks!  Check the link in post #7, it should answer all your questions if you intend to install XP on a dv5/dv7.

---

### Post by gm__ on 2008-12-31
Thanks to both of you, highly appreciated, i'll give it a go!

---

### Post by Aussieartist on 2009-01-07
Hey there, 
I just found this resource:
[http://www.linlap.com/wiki/HP+Pavilion+dv5-1000+Series]("http://www.linlap.com/wiki/HP+Pavilion+dv5-1000+Series")
I haven't read it all yet but looks good so far. I have cross linked to their forum so we should get a few more people in the 'Think Tank'
:D
Aussie

---

### Post by egawrangler on 2009-01-07
I added the audio controller to the list as I had problems with the audio slider.  I successfully *connected* to the GPIOAudioSlider and logged input to the system bus, but have no idea how to write a driver package to make this functionality built in.  End result - I added it to the list.

Aussie - I checked that link out....are you having problems with standby/resume?  If so, I'll add a bullet for ACPI functionality as that is what is most likely triggering the standby issue.  However, I haven't experienced it??  

Again, thanks for the contribution!

---

### Post by Aussieartist on 2009-01-07
I hate the audio slider too! Can't help you with compiling a package yet... Need to learn that as well!
I don't actually use the standby/hibernate stuff... My computer is either on or off~!
I was just looking around for more info and found that site, thought it mught be useful to have a list of specific forums to help with the dv5t.
Cheers
Aussie

---

### Post by snowguy on 2009-01-08
quicktouch buttons worked for me out of the boxe (volume and wireless work anyway--I haven't tried the others)

webcam doesn't work for me, but I don't really care and haven't bothered trying to trouble shoot it. I agree w/ a previous poster--I think that different version of this model come w/ different webcams. Mine is one w/out a fingerprint reader.

I'm using Linux Mint 6 Felicia so I assume the same things noted above be true on Ubuntu 8.10 Intrepid Ibex.

Also I have tried a couple of things but haven't gotten the suspend to work. I read somewhere else that this is a documented bug.

---

### Post by Aussieartist on 2009-01-09
Hi all,

I'm going back to a Vista/Ubuntu dual boot to see if the device manager on each comes up with a different list. I know Vista is a spooky world... but it will be nice to compare the device managers from Ubuntu and Vista... I'll keep a log.

I'll also be traveling home to Australia in a week so forgive me if I'm not being very 'intrepid' but I need the laptop to run VoIP and my old Powerpoints etc for my transition back home and back to work. My wife (who is a Doctor of Molecular Biology and gave up her G5 Mac for a Dell XP machine!) will be staying in the US for about 6 months more and will not let me 'play' with Linux without the dual boot.

Go figure!!! 
Aussie

---

### Post by egawrangler on 2009-01-09
Aussie -
  Thanks for the update!  I'm actually a triple-booter.  Vista (x64), XP (x86) and Ubuntu (x64).  Sadly Ubuntu has had the smallest amount of support for hardware, but this is not uncommon with linux and a new PC.  I've gone through the device logs as well, when booted into Vista, and haven't found much.  I think the main problem is mapping the hardware I/O to a driver/message handler.  I've been digging a lot into fprint in an attempt to get the VFS101 fingerprint reader up and running, but unfortunately I'm in the military and my time is not at a premium....what we really need is a developer!

Fly safe!
-EGA

---

### Post by egawrangler on 2009-01-11
This may be a bit of old knowledge but....I always experienced a lot of lag with the X server, along with the built in nVidia driver packages.  Graphics were just never as "snappy" as with my windows boxes.  

So, I scrapped the built in drivers and downloaded the latest release from nVidia (180.22).  Now X runs with NO lag and the "snappyness" is back!

Note that I had to compile new source modules, but I already had all the libraries and tools needed for this.  The nVidia installer is quite robust and flags any errors every step of the way, so the novice installer should be fine.

-EGA

---

### Post by Aussieartist on 2009-01-11
Hi Ega,
I forgot to include that my dv5t only has the basic display adapter:
Mobile Intel(R) 4 Series Express Chipset Family
Supported, native, but no Linux upgrades available and does not like OpenGL, esp in games. 

Cheers
Aussie

---

### Post by egawrangler on 2009-01-11
Gotcha.  I had it listed as Intel GMAX4500, as this is what intel referenced as its mobile adapter.  Have you tried compiling drivers available from the Intel website to fix your OpenGL woes?

---

### Post by Aussieartist on 2009-01-12
Yeah, Intel Linux support page does not apply to my chipset. (El Cheapo)
The Vista drivers do support OpenGL, I think I need to go back to the Ubuntu Package manager and see if there are any OpenGL libraries that I didn't have...
Cheers
Aussie

---

### Post by Aussieartist on 2009-01-12
Oh, here's another curiosity: (probably not related to anything we've discussed yet...)

[http://h30434.www3.hp.com/psg/board/message?board.id=OS&thread.id=3043]("http://h30434.www3.hp.com/psg/board/message?board.id=OS&thread.id=3043")

My "New" machine, which I bought in November, shows event logs back to June!
Cheers
Aussie

---

### Post by Aussieartist on 2009-01-12
**Lightscribe** I have tested:

My DVD/CD Burner: 
HL-DT-ST DVDRAM GSA-T50L (Hitachi/LG)
(Supported, native)

Lightscribe (for Linux) info and download:

[**Lightscribe System Software**]("http://www.lightscribe.com/downloadSection/linux/index.aspx?id=814") (Tested, works!)

[**Lightscribe Simple Labeler**]("http://www.lightscribe.com/downloadSection/linux/index.aspx?id=815") (Tested, works!)

NB: The above works well for simple labels (text on their included design templates). Make sure you have TrueType fonts package.

BUT the ability to insert your own graphics offered by [**3rd party software**]("http://www.lightscribe.com/products/index.aspx?id=105") doesn't seem to recognise the burner... I have tested laCie, Roxio and Nero. My mate (who has a similar but older HP laptop) tested all of the above with the same results. 

Cheers
Aussie

---

### Post by egawrangler on 2009-01-12
Gotcha, I'll update the front page accordingly.  I can answer your questions about your event log too!

This problem is very common when looking at windows system files as well.  Often times a file/log/whatever will have a modified datestamp that occured before the creation time!  So...how can the file have been modified before it was created??  It boils down to how Windows (the NTFS timestamps in particular) mark files as they are accessed.  In essence, the creation date only applies to the hard drive on which the file is stored, where the modified date is irrespective of this and can thus reflect previous accesses/creations/modifications, etc.  So, system files that are very infrequently accessed will display a modified date of when they were created by Micro$soft.  However, their creation date is the date they were copied to your computer which is probably much more recent.  This same behavior applies to system logs.

The hard drives from HP are all "ghosted" at the factory.  HP builds one system complete, with all the necessary software, then creates an image of that hard drive, and clones the image to every hard drive subsequently installed.  The original image will show event logs going back to *whenever* and your "ghosted" image is no different, even if you bought your computer recently.  This is SOP in this industry.

I saw someone said that HP takes PC's out of the box and "updates" them.  This is 100% not true.  And yes, I've worked with HP's production facilities extensively.  Anytime a computer is taken out of the box, after production, it becomes refurbished and must be sold as such.  Once the hard drive is imaged and installed in your machine, IT IS NEVER REMOVED, unless for technical problems, and the same rule above applies.  HP keeps the hard drive images pretty current, so one user may have newer timestamps than another, but this is due to a completely different hard drive image and not HP "taking it out of the box".

---

### Post by egawrangler on 2009-01-12
> **Aussieartist said:**
> Yeah, Intel Linux support page does not apply to my chipset. (El Cheapo)


I think your chipset is fine.  If I'm correct it's an Intel PM45, just like mine.  The Intel G45 is akin to this...so for all intents and purposes, you've got a G45.  The controllers are exactly the same in terms of bus addressing, signal interrupts, etc.  The difference is memory allocation, resolution, scaling, etc most of which are software dependent/specific.  I'd give it a go, even though it might be painful....[Issues with Intel G45 on HP DV5-1000us running hardy 64 ]("http://ubuntuforums.org/showthread.php?t=944185")

---

### Post by umhelp on 2009-01-15
I was just wondering if anyone had any luck with HDMI Sound with dv5t??

I tried alsa-1.0.18a and 2.6.29-rc1-git5 and I couldn't get any sound over HDMI.



Just as a side note: I have HDMI video output working and also esata seems to work as well.

---

### Post by egawrangler on 2009-01-16
> **umhelp said:**
> I was just wondering if anyone had any luck with HDMI Sound with dv5t??

I tried alsa-1.0.18a and 2.6.29-rc1-git5 and I couldn't get any sound over HDMI.


I've had no issues with the HDMI audio output.  However, I'm also using the nVidia driver package, and not the ubuntu restricted release.  I don't think the alsa (any flavor) kernel modules will help, as the HDMI audio output is technically (modulated) by the GPU.  Thus, it's the GPU drivers that do the trick.  I could be way off though, my experience with alsa is limited!

-EGA

---

### Post by umhelp on 2009-01-16
I am running 180.22 nvidia drivers and i am getting no HDMI audio. I am pretty sure it has something to do with alsa.

```
chris@Chris-Laptop ~ $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
chris@Chris-Laptop ~ $ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.18a.
```

What do you get when you do an aplay -l?? I really would love to get HDMI audio working because the headphone sound ports are bad quality.

---

### Post by egawrangler on 2009-01-16
> **umhelp said:**
> 
```
chris@Chris-Laptop ~ $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```



Those are your analog and digital audio outputs from the southbridge IDT audio, not HDMI.  Otherwise known as the 1/8" analog jacks on the front of the palmrest bezel.  Wish I had a picture, but I'm sure you know what I'm talking about.

Unfortunately I had to fly to NC this morning (I'm in the military and occasionally have to travel on short notice) so I'm away from my laptop until this evening.  As soon as I get back, I'll let you know what I uncover though....

-EGA

---

### Post by umhelp on 2009-01-17
> Those are your analog and digital audio outputs from the southbridge IDT audio, not HDMI. Otherwise known as the 1/8" analog jacks on the front of the palmrest bezel. Wish I had a picture, but I'm sure you know what I'm talking about.

I know what your talking about and I know my "aplay -l" is not showing HDMI sound support. If it way then I would be very happy :). I run a 1/8" plug to RCA to my Pioneer 1018 reciever and get my sound that way. The sound quality is very sub-par. I have been fighting very hard to get my HDMI-sound working. I believe that with your help I can finally get it working!! Thanks, and I will await your return.

---

### Post by egawrangler on 2009-01-17
Ugh, I'm still in NC.  Probably won't be back to CA until the end of the week.  Too many issues that I need to sort out.  Sorry for the delay.  Once I get home I'll look into this.  If I remember correctly, I had to force the azalia audio module to load along with the intel sound module...something like this...

options snd-hda-intel module=azalia order=1

The above is wrong...so don't add it to alsa options!  HA!:)

What does this produce on your machine?
"sudo lspci -v | grep -A8 Audio"

-EGA

---

### Post by umhelp on 2009-01-17
> What does this produce on your machine?
"sudo lspci -v | grep -A8 Audio"

```
00:1b.0 Audio device: Intel Corporation HD Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 3603
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at df300000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel

```

I will look into the Azalia module. If I cannot get it working using the alsa kernel drivers then I will try manually installing alsa. That is definately a good start. Thanks that might just be all I need to get this working. Very exciting!!

---

### Post by beeejay77 on 2009-02-12
> **egawrangler said:**
> Those are your analog and digital audio outputs from the southbridge IDT audio, not HDMI.  Otherwise known as the 1/8" analog jacks on the front of the palmrest bezel.  Wish I had a picture, but I'm sure you know what I'm talking about.

Unfortunately I had to fly to NC this morning (I'm in the military and occasionally have to travel on short notice) so I'm away from my laptop until this evening.  As soon as I get back, I'll let you know what I uncover though....

-EGA
I have hp dv5 1110ew - no sound on hdmi. I posted about it on alsa developer forum and guys from there are working on it.
[http://mailman.alsa-project.org/pipermail/alsa-devel/2009-February/014702.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2009-February/014702.html)

This script is upgrading alsa to latest snapshot.
sudo sh ./AlsaUpgrade-1.0.x-rev-1.16.sh -snap

---

### Post by NTolerance on 2009-03-24
Thanks for this thread.  I had just placed an order for a dv5tse with all Intel hardware.  I then learned from this thread that suspend doesn't work.  Based on the bug reports there's no fix in sight even for the latest development version of the Linux kernel.  

I'm on the phone with HP now cancelling my order.  It's a shame that this laptop doesn't have full support as my current dv6000t works very well with Intrepid.  I much prefer HP's build quality over Dell, but I wish HP would offer official Linux support.  

Linux laptop land is still an unhappy place.  :(

---

### Post by deFlNE on 2009-05-14
Guys, I’ve got dv5-1023 with IWL5100:

define@dv5-1023ea:~$ lspci | grep -i intel | grep -i network
02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection

I can’t get it work:
define@dv5-1023ea:~$ sudo modprobe -r iwlagn && sudo modprobe iwlagn

And my syslog shows this. The point is on this string:
iwlagn: Radio disabled by HW RF Kill switch

And I can’t turn my wireless on. It's always swithed off. Guys, how did you solve this problem? I use jaunty 64-bit with 2.6.28-11-generic kernel. Tried interpid, compiled gentoo, tried debian and suse all with 2.6.27 kernels. As I got it’s some kernel problem.

What can you say on the point?

---

### Post by NTolerance on 2009-05-14
> **deFlNE said:**
> Guys, I&#8217;ve got dv5-1023 with IWL5100:

define@dv5-1023ea:~$ lspci | grep -i intel | grep -i network
02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection

I can&#8217;t get it work:
define@dv5-1023ea:~$ sudo modprobe -r iwlagn && sudo modprobe iwlagn

And my syslog shows this. The point is on this string:
iwlagn: Radio disabled by HW RF Kill switch

And I can&#8217;t turn my wireless on. It's always swithed off. Guys, how did you solve this problem? I use jaunty 64-bit with 2.6.28-11-generic kernel. Tried interpid, compiled gentoo, tried debian and suse all with 2.6.27 kernels. As I got it&#8217;s some kernel problem.

What can you say on the point?

I hate to say it, but does your laptop have a physical toggle switch on the back or side that turns off the wifi radio?  My HP DV6000t does.

---

### Post by egawrangler on 2009-05-14
> **NTolerance said:**
> I hate to say it, but does your laptop have a physical toggle switch on the back or side that turns off the wifi radio?  My HP DV6000t does.

...same question from me. On my dv5, I've got a capacitive wifi on/off button on the top right of the laptop, right above the keyboard.  This is the HW RF Kill switch syslog is talking about.  If your machine says this HW kill switch is enabled....it probably is.

When it's off, it's orange.  On = Blue.  

Maybe it's just shorted out and needs to be replaced?

BTW, you can remove that panel and still boot the computer to see if the switch it actually shorted out or its something else.

---

### Post by anjohnso on 2009-05-14
Just another note... Mine won't light up blue, despite having the ability to switch it on and off.  Threw me for a loop a few times.  Try hitting it once and see what happens.

---

### Post by egawrangler on 2009-05-14
> **anjohnso said:**
> Just another note... Mine won't light up blue, despite having the ability to switch it on and off.  Threw me for a loop a few times.  Try hitting it once and see what happens.

Which distro are you using?  Intrepid, Jaunty?

I had problems getting this thing to light up blue under XP, and had to perform some regsitry tweaking.  Maybe the two issues are connected?

---

### Post by anjohnso on 2009-05-16
Running Intrepid.  I really could care less if it lit up or not...though it'd be nice to have everything 100 percent.

---

