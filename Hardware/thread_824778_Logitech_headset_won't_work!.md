---
title: "Logitech headset won't work!"
date: 2008-06-10
forum: Hardware
---

### Post by TheDeathOfHell on 2008-06-10
[INDENT][/INDENT]I've had this headset a long time and it never failed me. Thought one thing I notice is that, in Ubuntu, I can't hear sound when I watch youtube videos and etcetera. The head set works fine in Windows XP Home Edition. The only way I can get sound in Ubuntu is if I use my actual speakers, which isn't possible because my parents will yell at me because of the noise.

[INDENT][/INDENT]I have a HP Pavilion a630n. I hooked up the the head set to the front of my computer, the headset sound going to the green jack with a pair of headphones etched on the side. Then I hooked up my microphone to the pink jack. If I hook up my headset to the back of the computer it will work, but it has a very bad quality and then I have to unhook my speakers and stuff. I went to the sound button in the top taskbar and went through all the options and I made sure everything was full volume and not muted.

tl;dr: Headset sound won't work on the front green jack in Ubuntu but will in Windows and same with my microphone. 

I would appreciate help.

---

### Post by TheDeathOfHell on 2008-06-10
Um this is kind of urgent, bump.

---

### Post by stchman on 2008-06-10
> **TheDeathOfHell said:**
> [INDENT][/INDENT]I've had this headset a long time and it never failed me. Thought one thing I notice is that, in Ubuntu, I can't hear sound when I watch youtube videos and etcetera. The head set works fine in Windows XP Home Edition. The only way I can get sound in Ubuntu is if I use my actual speakers, which isn't possible because my parents will yell at me because of the noise.

[INDENT][/INDENT]I have a HP Pavilion a630n. I hooked up the the head set to the front of my computer, the headset sound going to the green jack with a pair of headphones etched on the side. Then I hooked up my microphone to the pink jack. If I hook up my headset to the back of the computer it will work, but it has a very bad quality and then I have to unhook my speakers and stuff. I went to the sound button in the top taskbar and went through all the options and I made sure everything was full volume and not muted.

tl;dr: Headset sound won't work on the front green jack in Ubuntu but will in Windows and same with my microphone. 

I would appreciate help.

So the front jacks work in Windows but not Ubuntu?

That is strange as they are just wires that hook up to the sound card.  Give us an lspci output here.  What version of Ubuntu you running?

---

### Post by TheDeathOfHell on 2008-06-10
I have the Ubuntu 8.04 LTS Desktop Edition and I don't know what a lspci output is or how to find it.

---

### Post by stchman on 2008-06-10
> **TheDeathOfHell said:**
> I have the Ubuntu 8.04 LTS Desktop Edition and I don't know what a lspci output is or how to find it.

Go to the terminal window and type lspci.  This will produce an output.  Copy and paste the output in this thread.  This command tells us what kind of hardware you have hooked up the PCI bus.

---

### Post by TheDeathOfHell on 2008-06-10
```
alex@alex-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
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
01:00.0 VGA compatible controller: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series]
01:00.1 Display controller: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series] (Secondary)
03:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
03:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
03:05.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
alex@alex-desktop:~$ 


```

Thanks for helping :)

---

### Post by stchman on 2008-06-10
Do the front jacks work fine in Windows?  If yes, then you need to double click the speaker up in the system tray.  This will bring up Gnome sound manager.  There is a tab and in one of those tabs there should be a headphone box.

You sound is an ICH6 Intel card and works OOB with Ubuntu.

---

### Post by TheDeathOfHell on 2008-06-10
From the start when I installed Ubuntu a few days ago that box was checked. And it never worked.

EDIT: The headphone check box under HDA INTEL (Alsa mixer) and the tab "switches"

---

### Post by stchman on 2008-06-10
> **TheDeathOfHell said:**
> From the start when I installed Ubuntu a few days ago that box was checked. And it never worked.

EDIT: The headphone check box under HDA INTEL (Alsa mixer) and the tab "switches"

Try this.  I have not had much luck with the PulseAudio driver.  Use the ALSA driver.

In the System--->Preferences--->Sound

there are some options for Automatic in output and capture.  Change all those options to ALSA.  Tell me if this works.

---

### Post by stchman on 2008-06-10
Here is an interesting read.

[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

According to the wiki PulseAudio has issus with Flash (YouTube uses flash) audio.  Don't mess with the fix just use ALSA.

---

### Post by TheDeathOfHell on 2008-06-10
Okay, in preferences I made the top for ASLA. But I don't know which to use for device at the way bottom. There are five options. 

[LIST]
[*]HDA Intel (Asla mixer)
[*]Realtek ALC880 (OSS Mixer)
[*]Playback: ALSA PCM on front:0 (ALC880 Analog) via DMA (PulseAudio Mixer)
[/LIST]

Then there are two other options that have "capture:" infront of them. So I don't think those would work.

But I tried those three but I didn't hear anything. If you have to restart to get the changes then could you tell me. Thanks.

---

### Post by stchman on 2008-06-10
> **TheDeathOfHell said:**
> Okay, in preferences I made the top for ASLA. But I don't know which to use for device at the way bottom. There are five options. 

[LIST]
[*]HDA Intel (Asla mixer)
[*]Realtek ALC880 (OSS Mixer)
[*]Playback: ALSA PCM on front:0 (ALC880 Analog) via DMA (PulseAudio Mixer)
[/LIST]

Then there are two other options that have "capture:" infront of them. So I don't think those would work.

But I tried those three but I didn't hear anything. If you have to restart to get the changes then could you tell me. Thanks.

HDA Intel ALSA.

---

### Post by TheDeathOfHell on 2008-06-10
It did not work unfortunately. :(

---

### Post by TheDeathOfHell on 2008-06-10
Here are some pictures that might help:

[IMG]http://img113.imageshack.us/img113/8426/screenshotsoundpreferenue6.png[/IMG]

[IMG]http://img185.imageshack.us/img185/7079/screenshotvolumecontrolac7.png[/IMG]

[IMG]http://img113.imageshack.us/img113/6082/screenshotvolumecontrolqa6.png[/IMG]

[IMG]http://img299.imageshack.us/img299/834/screenshotvolumecontrolmh9.png[/IMG]

[IMG]http://img113.imageshack.us/img113/2213/screenshotvolumecontrolyo7.png[/IMG]

The last four were taken from the settings of HDA Intel (Alsa mixer)

---

### Post by stchman on 2008-06-10
That all looks good.  I have the ICH8 in my laptop but it does not heave near those options.  The headphone worked OOB and cut off the laptop speakers when inserted.

I will see if I can think of anything else.

In the future to take a screenshot there is a much easier method.

Use Alt-PrintScreen at the same time to take a screenshot of the active window.

PrintScreen takes a shot of the entire desktop.

---

### Post by TheDeathOfHell on 2008-06-10
[IMG]http://img55.imageshack.us/img55/6167/p6100063if6.jpg[/IMG]
[IMG]http://img380.imageshack.us/img380/2320/p6100065xn4.jpg[/IMG]

Here's some pictures for reference.

(Front of computer).

Yes, it is dusty. That is not affecting it because when I reboot into Windows it works.

---

### Post by stchman on 2008-06-10
Until somebody else chimes in the only other thing I can think of is to recompile ALSA to a newer version.

I have a script to do this.

[http://www.stchman.com/alsa_update.html](http://www.stchman.com/alsa_update.html)

There are some reports of the newer ALSA 1.0.16 breaking audio functionality.  I have never had that difficulty in my experiences and I have used the script many times on older Ubuntu distros.

Follow the page instructions EXACTLY.  Any deviations can be bad.

Save the ALSA script to your home folder as the instructions are tailored for that location.

Go into the script and comment out lines 73 and 74 as they are for older Ubuntu versions.  The lines should look like this when done.

```
# sudo echo -e '\n' >> /etc/modprobe.d/alsa-base
# sudo echo "options snd-hda-intel model=3stack" >> /etc/modprobe.d/alsa-base
```

Follow the instructions to change permission and run the script.  If you notice a '#' in front of the line is a comment.  Remember to save once you edit.

I hope this helps as I am out of ideas.

---

### Post by TheDeathOfHell on 2008-06-10
Well it didn't work. But thanks for your help! :( If I can't get this fixed I just won't be able to use Ubuntu.

---

### Post by TheDeathOfHell on 2008-06-11
Could someone please help?

---

### Post by TheDeathOfHell on 2008-06-11
Please? I really enjoy the OS but I can't use it without sound!

---

### Post by Pinpoint Focus on 2008-06-18
Hello:

I'm having the same sort of problem but I think I'm better off reverting to my original settings, getting away from the Logitech USB Headset.  Now all I want to do is return things the way there were, after installation.  Is this possible with out loosing my data.  If doing a complete re-install is the only fix at this point I'm prepared to do it, but backing up my data on DVD's would be time consuming.  Unless you know of a simple way to do this type of back up. I have two physical drives one with Windows the other with Ubuntu 8.04

Sincerely,

Robert Chambers.
[email]chambersr@gmail.com[/email]

---

### Post by slaming on 2008-06-30
if its a usb change all of the settings to usb

---

### Post by slaming on 2008-06-30
heres a picture

---

