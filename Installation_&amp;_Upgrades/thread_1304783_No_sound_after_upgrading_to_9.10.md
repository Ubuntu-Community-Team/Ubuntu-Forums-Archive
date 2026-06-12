---
title: "No sound after upgrading to 9.10"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by MrSnowmiss on 2009-10-29
I've just finished upgrading my machine to 9.10 (was 9.04)
Everything went fine, except I now don't have any sound. No mp3, not on youtube clips. Kmixer has nothing muted. Any suggestions where to go from here?

BTW. On the old setup I could listen to two different sounds at the same time (for example playing mp3's while hearing a youtube movie)

---

### Post by Pablo Pablovski on 2009-10-29
I upgraded last night and had the same problem. I have a single sound device, a Sound Blaster Audigy, that worked ok in Jaunty (I use kubuntu). I was also getting errors in the Notification area about sound devices not working properly.

Anyway, the fix for me was to promote the "Audigy #1" entry in the Multimedia configuration preference of System Settings - it turned out that that device is associated with the front speakers and "Audigy #2" is the rear speakers - and plain ol' "Audigy" (which was the default preferred output) doesn't seem linked to anything. I'm sure it was different in Jaunty. Go figure.... 

If you're using Gnome, it might be a different process, but it's worth investigating the priority of sound devices.

---

### Post by gsparky2004 on 2009-10-29
This might be a bug.  I had the exact, same problem.  I was actually playing music while the upgrade was downloading.  I upgraded to karmic less than an hour ago, and now I have no sound.  When I open the "Sound Preferences" window, there aren't even any sound devices listed.  No idea where to go from here.  I'm just... stuck.  I went to report it and found that there was a bug report for the same thing.  I just listed it as "I'm having the same problem".  I'm also subscribed if / when they create a fix for it.

---

### Post by MrSnowmiss on 2009-10-29
I did a reboot and a message came up saying "It seems some audio hardware is no longer available, do you want KDE to forget this hardware al together"
I clicked NO, in my settings my HDMI output is now grey. I made my HDA Intel the first device before pulseaudio. Tested it and it worked then tested it again and it gave a message that my sound wasn't working correct. I do remember having similar problems with jaunty but had hoped it would have been solved with karmic :(

Don't know if it has anything to do with it, but I am using the 64bit version.

---

### Post by gsparky2004 on 2009-10-29
I just ran a "lspci" command and the audio card was listed.

00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8500 GT] (rev a1)
02:00.0 Mass storage controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8050 PCI-E ASF Gigabit Ethernet Controller (rev 17)
06:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
**06:01.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 05)**
06:01.1 Input device controller: Creative Labs SB Live! Game Port (rev 05)
06:02.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem

So, no idea what the problem is here.  I'm going to keep poking at it because, hey, this is one thing you're allowed to do in Linux.

---

### Post by MrSnowmiss on 2009-10-29
You could also try: > aplay -l to see a list of playback hardware devices

---

### Post by gsparky2004 on 2009-10-29
Ah, the plot thickens.  I ran "aplay -l" and got:
> aplay: device_list:223: no soundcards found...
Hmmm.

---

### Post by dupper on 2009-10-29
same here

---

### Post by lovinglinux on 2009-10-29
I'm not sure this is the correct procedure, because I'm running kde-minimal over command-line ubuntu installation. Anyway, what I did with the sound was installing pulseaudio and promoting it to the top of the Multimedia settings as already explained on another post. The warnings stopped and all sounds work. Actually, it works better than Jaunty with no extra pulseaudio CPU usage.

---

### Post by francsal on 2009-10-29
I had that problem when testing the Beta version, and this tip actually worked. Open terminal, and start alsamixer. Then, first check that no output is muted (MM on the bottom of the bar), and then turn up the volume for each output channel. Even though the mixer showed no muted channels doing that restored audio on my netbook.

I hope that works.

cheers.

Frank.

---

### Post by MrSnowmiss on 2009-10-29
> **lovinglinux said:**
> I'm not sure this is the correct procedure, because I'm running kde-minimal over command-line ubuntu installation. Anyway, what I did with the sound was installing pulseaudio and promoting it to the top of the Multimedia settings as already explained on another post. The warnings stopped and all sounds work. Actually, it works better than Jaunty with no extra pulseaudio CPU usage.

Pulseaudio is already installed and putting it on top of the multimedia settings doesn't seem to help :(

---

### Post by MrSnowmiss on 2009-10-29
> **francsal said:**
> I had that problem when testing the Beta version, and this tip actually worked. Open terminal, and start alsamixer. Then, first check that no output is muted (MM on the bottom of the bar), and then turn up the volume for each output channel. Even though the mixer showed no muted channels doing that restored audio on my netbook.

I hope that works.

cheers.

Frank.

THANX a lot !!!

This did the trick for me! :D:D

---

### Post by lovinglinux on 2009-10-29
> **MrSnowmiss said:**
> Pulseaudio is already installed and putting it on top of the multimedia settings doesn't seem to help :(

Did you put it on top on every Multimedia settings, not just the top ones?

---

### Post by dupper on 2009-10-29
i had to update grub manually because it still used the kernels of 9.04...

---

### Post by gsparky2004 on 2009-10-29
Okay, being a newbie, I'm not familiar with alsamixer.  Do you just type "alsamixer" in the terminal window?  If so, I got the following error:
> alsamixer: function snd_ctl_open failed for default: No such file or directory
And I have Pulseaudio installed (I looked in Synaptic), but I have no idea how to run it / control it.  There are no icons for it anywhere in my "Applications" and if I try to run it from the terminal window, I get:
> E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.
Any suggestions?  I'm about ready to repartition the hard drive and re-install 9.04.  I want my sound / desktop icons / no "unknown processes" / Skype works computer back.

---

### Post by mondo1287 on 2009-10-29
gsparky2004, I have the same issue that you have.  Alsa can't find any sound cards after the 9.10 update.

---

### Post by lovinglinux on 2009-10-29
> **gsparky2004 said:**
> Okay, being a newbie, I'm not familiar with alsamixer.  Do you just type "alsamixer" in the terminal window?  If so, I got the following error:

And I have Pulseaudio installed (I looked in Synaptic), but I have no idea how to run it / control it.  There are no icons for it anywhere in my "Applications" and if I try to run it from the terminal window, I get:

Any suggestions?  I'm about ready to repartition the hard drive and re-install 9.04.  I want my sound / desktop icons / no "unknown processes" / Skype works computer back.

This thread is for Kubuntu. If you are running Kubuntu or KDE on Ubuntu, go to "System Settings >> Computer Administration >> Multimedia".

---

### Post by gsparky2004 on 2009-10-29
> This thread is for Kubuntu.

So much for one, big, happy Linux family.  Come on, mondo1287, we'll go start our own thread.

---

### Post by lovinglinux on 2009-10-29
> **gsparky2004 said:**
> So much for one, big, happy Linux family.  Come on, mondo1287, we'll go start our own thread.

I'm not saying you shouldn't be posting here, just that graphical tools are different, so you might be trying to find stuff not available on your installation. I wasn't sure if you were aware of this. Anyway, is always a good idea to check the thread tag, which in this case is [kubuntu].

---

### Post by roikonen on 2009-10-30
Hi!

No sounds here either. Updated from 9.04 to 9.10 this morning.

$ aplay -l
aplay: device_list:223: no soundcards found...

$ alsamixer
alsamixer: function snd_ctl_open failed for default: No such file or directory

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 81ec
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at ffaf8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

Don't know what to do.

---

### Post by Plumtreed on 2009-10-30
> **dupper said:**
> i had to update grub manually because it still used the kernels of 9.04...

My Grub is showing only 9.04 not 9.10, which suggests that the same thing is happening to me.

Can you tell me how to update Grub?

---

### Post by izmenar on 2009-10-30
> **francsal said:**
> I had that problem when testing the Beta version, and this tip actually worked. Open terminal, and start alsamixer. Then, first check that no output is muted (MM on the bottom of the bar), and then turn up the volume for each output channel. Even though the mixer showed no muted channels doing that restored audio on my netbook.

I hope that works.

cheers.

Frank.

thank you very much , that did it ,

---

### Post by roikonen on 2009-10-30
> **Plumtreed said:**
> My Grub is showing only 9.04 not 9.10, which suggests that the same thing is happening to me.

Can you tell me how to update Grub?

Edit /boot/grub/menu.lst

---

### Post by paolo.pani on 2009-10-30
No sound in KDE on ubuntu even here. Sound works in Gnome and it worked both in gnome and KDE on Ubuntu 9.04

> aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Sound cards are detected... and Pulse is on the top of Multimedia..but still it does not work

---

### Post by emptymind on 2009-10-30
I am having similar troubles ...

$ aplay -l
aplay: device_list:223: no soundcards found...

$ alsamixer
alsamixer: function snd_ctl_open failed for default: No such file or directory

$ sudo lshw -C multimedia
  *-multimedia            
       description: Multimedia audio controller
       product: VT8233/A/8235/8237 AC97 Audio Controller
       vendor: VIA Technologies, Inc.
       physical id: 11.5
       bus info: pci@0000:00:11.5
       version: 60
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: driver=VIA 82xx Audio latency=0
       resources: irq:22 ioport:e800(size=256)

The snd_via82xx module is listed when I run "lsmod", but the soundcard isn't detected. And yes, it worked fine in Jaunty.

I'll try running another kernel and see if that helps.

---

### Post by emptymind on 2009-10-30
Hi, just a quick update. Turns out that after the update, I was still running an older kernel.

I did a sudo apt-get install grub2, accepted that the script update my menu.lst based on what was there before, and it installs a new /boot/menu.lst which contains the new kernel. I rebooted and have sound working perfectly.

---

### Post by MrSnowmiss on 2009-10-31
Although I mentioned having my sound back (on youtube en mp3 players), it seems I can listen to any radiostation from this site: [http://www.nederland.fm/](http://www.nederland.fm/)

Does this require a plugin I had in Jaunty that has disappeared?

---

### Post by cloud69 on 2009-10-31
same probelm here after upgrading from 9.04  to 9.10 sound card was not detected.

---

### Post by cloud69 on 2009-10-31
> **emptymind said:**
> Hi, just a quick update. Turns out that after the update, I was still running an older kernel.

I did a sudo apt-get install grub2, accepted that the script update my menu.lst based on what was there before, and it installs a new /boot/menu.lst which contains the new kernel. I rebooted and have sound working perfectly.

try this it might work for you. as it did for me. thanks!

---

### Post by chessmani on 2009-11-02
> **francsal said:**
> I had that problem when testing the Beta version, and this tip actually worked. Open terminal, and start alsamixer. Then, first check that no output is muted (MM on the bottom of the bar), and then turn up the volume for each output channel. Even though the mixer showed no muted channels doing that restored audio on my netbook.

I hope that works.

cheers.

Frank.

This worked for me too. In my case I had the master channel unmuted, but it turned out that I needed to have 'headphone' unmuted as well. Sound works now. Not with every app though. Skype doesn't work, for example.

Edit: Skype does work, had to upgrade it. I guess now my sound works flawlessly. Intel HDA here btw.

---

### Post by gypsumwolf on 2009-11-02
I have a Dell Mini 10. I had no sound after upgrade (of 9.10). Now the sound is working perfectly. I used this to fix the problem (Its very simple to do). Maybe the solution for your card is somewhat similar.

[http://georgeblog.nyarangi.com/2009/10/no-sound-on-dell-mini-10-running-ubuntu.html]("http://georgeblog.nyarangi.com/2009/10/no-sound-on-dell-mini-10-running-ubuntu.html")

Quoted from the website:"

Follow these steps:
1.First you must find which model of sound card you use, so run this command:


```
cat /proc/asound/card0/codec#* | grep Codec
```


Note: You should obtain this:


```
Codec: Realtek ALC269
Codec: Silicon Image SiI1392 HDMI
```


This means that your soundcard is ALC269. If it is not ALC269, follow the instructions here. Otherwise, continue to step 2.

2.Open /etc/modprobe.d/alsa-base with the following command:

```
sudo nano /etc/modprobe.d/alsa-base.conf
```


3.Paste the following line at the end of the file:

```
options snd-hda-intel model=basic
```


Save the file and close it.

4.Go to System>Preferences>Sound>Hardware.
On the Profile drop down menu, select "Analog Stereo Output".
Make sure the Output Volume is set to 100% and close.

5.Reboot and now you can enjoy Karmic with sound:) "

---

### Post by MrSnowmiss on 2009-11-02
> **chessmani said:**
> This worked for me too. In my case I had the master channel unmuted, but it turned out that I needed to have 'headphone' unmuted as well. Sound works now. Not with every app though. Skype doesn't work, for example.

Edit: Skype does work, had to upgrade it. I guess now my sound works flawlessly. Intel HDA here btw.

I downloaded the latest skype (amd64 deb) and installed it....no sound :(
Even worse also no video (while video was working in 9.04)
It also Intel HDA here. So it seems a bit randomly all this sound/skype thingies.

---

### Post by KIAaze on 2009-11-02
> **francsal said:**
> I had that problem when testing the Beta version, and this tip actually worked. Open terminal, and start alsamixer. Then, first check that no output is muted (MM on the bottom of the bar), and then turn up the volume for each output channel. Even though the mixer showed no muted channels doing that restored audio on my netbook.

I hope that works.

cheers.

Frank.

Worked for me too.
Thanks. :)

---

### Post by OriTheEep on 2009-11-02
> **emptymind said:**
> Hi, just a quick update. Turns out that after the update, I was still running an older kernel.

I did a sudo apt-get install grub2, accepted that the script update my menu.lst based on what was there before, and it installs a new /boot/menu.lst which contains the new kernel. I rebooted and have sound working perfectly.

Thanks!

I followed your advice and now have sound back and XSane sees my scanner once again.

:)

---

### Post by JohnsShadow on 2009-11-29
i fixed it, i was browsing around in my sound prefrences and under applications i saw firefox which was muted un click that and boom done

menu<system<prefrences<sound<application<firefox=UNMUTE

to be fair i did a fresh install not one of those lame upgrades (never worked in windows why would it work in linux)

---

### Post by cespinal on 2009-12-02
> **MrSnowmiss said:**
> THANX a lot !!!

This did the trick for me! :D:D

for me too here :)

---

### Post by z_mikowski on 2010-01-10
Ok, so I spent 3 hours on this yesterday.  My Wife's machine stopped producing sound after a recent upgrade, and it fell on me to fix.

1. Remove everything to do with pulse audio, with the exception of libpulse0, which is a dependency of KDE4.

```
wajig list-installed |grep pulse
> libpulse0
```

2. In vi /etc/modprobe.d/alsa-base.conf, changed the intel lines to read:

```
# options snd-hda-intel power_save=10 power_save_controller=N
options snd-hda-intel model=auto
```

3. Made sure the latest kernel was being used, as this was an upgrade.  I did this by installing grub2.  Also, I installed linux-backports-modules-karmic to ensure drivers were in sync with the kernel (?)

4. Used alsamixer to ensure that all audio channels were unmuted

5. Ensured all multimedia support was installed ( it was; see [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) )

6. Ensured there was an output card, using aplay (from the alsa-utils package):

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

7. Made sure System_Settings->Multimedia has HDA Intel (ALC888 Analog) as the preferred device.

After all that, the speaker would 'pop' when sound was supposed to play, but then nothing.

**RESOLUTION:** I gave up after all this and perhaps 15 reboots and shut down completely.  This morning, after STARTING THE COMPUTER FROM THE FULL SHUTDOWN, sound works perfectly.

**LESSON LEARNED: Rebooting is NOT the same as complete power-down and power-up cycle, at least for my MoBo.**  Apparently, reboot did not fully reinitialize the on-board sound (Intel HDA RealTek ALC888 ), but a full power-down/power-up cycle does.

Hope this helps someone else!

---

