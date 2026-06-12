---
title: "Mic doesn't work in VoIP apps, but does with Audacity"
date: 2015-07-06
forum: Hardware
---

### Post by Inoki on 2015-07-06
I am running Ubuntu GNOME 15.04 x64, but I tested also with Manjaro k3.16.7 to see if this impacts only *ubuntu variants and I got the same result - microphone is barely working, I could barely hear myself. It is extremely silent even with high amplification. There is a slight indication it's there, but sound quality is extremely bad with only distorted noise. This is system-wide - tested in Hangouts (web) and Skype (app), Telegram, by sending an audio message.

```
Audio:     Card-1 Advanced Micro Devices [AMD] FCH Azalia Controller
           driver: snd_hda_intel
           Card-2 Advanced Micro Devices [AMD/ATI] Kabini HDMI/DP Audio
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k3.19.0-21-generic


```

---

### Post by Vladlenin5000 on 2015-07-06
How does it work with an external microphone?

---

### Post by Inoki on 2015-07-07
I've tried now with a pair of headphones that have a mic, it was the only thing I have (not using it at all) and my laptop has a unified jack for both mic and speakers. Sound was very, very bad, nothing understandable.

The problem is this is definitely only a Linux issue, as on Windows 7 sound was crystal clear from the built-in mic.

---

### Post by Inoki on 2015-07-11
Do you think is it also possible that I'm having this issue because I installed my system with legacy instead of UEFI settings in BIOS?

I'm asking, because Windows wouldn't install in legacy mode, I had to change boot priority to "UEFI first" and everything worked, so is there a chance my hardware might be misbehaving because of legacy settings?

---

### Post by kansasnoob on 2015-07-11
I'd bet on it being a kernel issue unless it's GNOME DE specific. Does it act the same way running a live session with a live DVD/USB? 

You could test the latest kernel by trying a live session of the Ubuntu GNOME Wily daily image which you can grab from the QA Tracker:

[http://iso.qa.ubuntu.com/qatracker/milestones/340/builds](http://iso.qa.ubuntu.com/qatracker/milestones/340/builds)

Or to find out if it's a GNOME specific issue you could try running a live session with an Ubuntu (or other flavor) image:

[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

Let me know if you have trouble with those links. Don't do anything drastic like reinstalling, or installing the dev version (Wily) - we just have some troubleshooting to do so I thought using live images would be easier unless you have limited bandwidth.

BTW I'm Lance from Ubuntu GNOME QA - not a genius, just a lowly tester ;)

---

### Post by Inoki on 2015-07-11
Hey Lance,

I already tried numerous live sessions with all *ubuntu flavours and also distros like Fedora, Manjaro and the mic behaved the same.

Important thing to mention is when BIOS was set to UEFI and I ran Windows everything worked. Windows wouldn't even allow to be installed with legacy settings.

At some point I think I even had UEFI with Ubuntu on this laptop with an older version and if memory serves me (am not sure though) even the microphone worked. I am pretty sure at some point the mic still worked with Ubuntu Unity. That's why I need confirmation if BIOS settings can have impact on the way hardware works, because I've read that legacy BIOS can have bugs/odd behaviour, but am not sure.

I now tested even Debian Jessie live ISO and the result is the same on a different kernel.

---

### Post by kansasnoob on 2015-07-11
You could also test that scenario using the live Ubuntu (or Ubuntu GNOME) sessions. You'd just change the BIOS settings to use UEFI, then make sure the live session starts in UEFI mode (the boot screen looks like a grub screen rather than a typical live session boot screen). Then if the mic works OK in a UEFI live session you'd know if it's a hardware glitch. I suppose it's possible that some firmware fails to load properly booting in legacy mode but I've not personally seen that.

**Just be sure you change back to legacy BIOS mode before trying to boot the installed OS!**

---

### Post by Inoki on 2015-07-12
Have tested with having everything set to UEFI except OS defaults, those I kept for "other OS", not Windows 8, then my computer [wouldn't even boot]("https://answers.microsoft.com/en-us/windows/forum/windows_8-system/windows-8-boot-problem/954a5e64-2474-47d5-96c5-406b083b880e"), probably also because I have no EFI partition (since legacy boot doesn't require it, at least it doesn't give any prompt as opposed to when I used old BIOS, with which my computer came, and had it set to UEFI). It gave the error described in the link saying no boot device could be found, so I just reverted back to setting everything to legacy and now everything boots.

So this might not be a BIOS issue after all. How to explain, that previously the mic worked, even if briefly, and now it doesn't...

But the question still remains what can be done about that mic not working?

---

### Post by kansasnoob on 2015-07-12
I'm a bit new to UEFI myself but I know that the Ubuntu amd64 live images should boot in UEFI mode even if no EFI/boot partition exists because I've done so with new blank hard drives and totally reformatted drives, then using Gparted from the live session to create a new GPT partition table before installing any OS. But, of the two sets of UEFI hardware in house, one requires that I press F10 during boot to select DVD/USB, and the other requires pressing F11.

Is this a dual-boot? Or is Ubuntu GNOME your only OS on that machine? I'm still just thinking we need to narrow this down to knowing whether it's a Linux problem or a UEFI vs. legacy BIOS problem. Sometimes if I'm really stumped I'll select "load default settings" in BIOS settings/UEFI utility and basically start from scratch - of course backing up all data first.

AFAIK there shouldn't really be any reason to use legacy BIOS mode rather than UEFI mode to set up either a simple dual-boot or an Ubuntu only machine. Multi-booting more than one Linux OS in UEFI mode is complicated though (at least it always is for me).

---

### Post by Inoki on 2015-07-12
I have asked for clarification about UEFI vs. Legacy and got good enough [answer]("https://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why") not to stick with it.

On the other hand, when I change my BIOS settings to full UEFI with defaults for "Other OS" after updating to the latest BIOS version I can't boot anything, so I have to stick to Legacy as in [this thread]("https://answers.microsoft.com/en-us/windows/forum/windows_8-system/windows-8-boot-problem/954a5e64-2474-47d5-96c5-406b083b880e") (error report not mine), because I get the following (numbers may vary):

```
Checking media [Fail]
EFI Network 0 for IPv6 (B8-88-E3-91-96-B20 boot failed
Checking Media [Fail]
EFI Network 0 for IPv4 (B8-88-E3-91-96-B2) boot failed
Lenovo Reovery System boot failed.

Default Boot Device Missing or Boot Failed.
Insert Recovery Media and Hit any key
Then Select Boot Manager to choose a new Boot
Device or to Boot Recovery Media.
```

Just so I don't forget anything, right after I updated my BIOS I got this error. BIOS update was necessary in order to help troubleshoot a [high priority Xorg bug]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1443456").

Once I updated my BIOS I couldn't boot anything with the above error. The only solution was to default my BIOS, but even then it didn't work, because it was in full UEFI, so I had to change a couple of settings and the working ones were even as per the before last comment in the mentioned thread to switch to legacy settings.

I am using only Ubuntu GNOME 15.04 on this machine. Not a fan of proprietary software.

---

### Post by kansasnoob on 2015-07-12
I wonder if the BIOS update broke the firmware for the mic?

---

### Post by Inoki on 2015-07-12
Do you think I should give it one last shot by settings even BIOS Defaults (not only boot priority and boot mode respectively) to Windows 8 (UEFI), then boot to a live session and try Ubuntu GNOME from there?

Even though now it made me think, that the setting for BIOS Defaults (either Other OS or **Windows 8 UEFI**) is just a shortcut that automatically sets everything to UEFI and when I did that manually and it did not boot any more it would not make any difference.

---

### Post by kansasnoob on 2015-07-12
Well, I'm stumped. It certainly seems more and more like an actual hardware borkage issue.

---

### Post by Inoki on 2015-07-13
Ok, you won't believe this, but when I tested over Audacity to record my  own voice it worked. Through Audacity I could hear my voice. Through  Skype or Hangouts, or Telegram I cannot.

I checked both my  current BIOS settings (full legacy) and tried setting OS defaults to Win 8 and  boot priority UEFI first, but with legacy support ON, and I got the same result via both settings.

I tried to launch LibreOffice and it crashes my session on either configuration, so something else is at play.

I have updated the thread title to match the problematic and added Telegram to the list of tried apps. I think this generally applies to any app that transmits data over the internet, but not local apps. How else can it be explained that I can hear myself over Audacity but not via Skype.

---

### Post by kansasnoob on 2015-07-13
Well that's good news :)

I can't help with Skype, Hangouts, or Telegram because I don't use them. I'd first consider the source of those packages and if they're in the standard Ubuntu repos I'd file a launchpad bug against each package. OTOH if they're not in the repos I'd report directly to the source responsible for the package, eg; if from a PPA there is always a "For questions and bugs with software in this PPA please contact" link.

The session crash while launching LibreOffice is likely unrelated, is it the standard version from the repos? I seldom use LibreOffice in favor of the [GNOME Office Suite]("https://wiki.gnome.org/action/show/Projects/GnomeOffice?action=show&redirect=GnomeOffice"), but I know LibreOffice is much more popular.

I'm still a bit curious about any effect the kernel version may have on any of these issues????? Have you tried Wily? It's in quite early development so major breakage may occur at any time but it's up to the 4.0.0.4.6 version kernel which purportedly brings a lot of changes (although none have been obvious to me). Maybe if you have enough disc space you could try dual-booting Vivid and Wily??????

---

### Post by Inoki on 2015-07-13
I don't think filing a separate bug against every app I encounter is a good idea, especially those not in the repos, more like filing a bug against what they all have in common - a library/driver, which is most likely causing the hiccups.

So far I was only able to record my voice via Audacity, but that's a good enough sign, that my mic is not broken and in fact operational, but something is hindering it.

As far as kernel goes, I didn't have issues up to k3.16.*, but after k3.19.* it started, that inlcludes k4*.

---

### Post by kansasnoob on 2015-07-13
I'll ask someone with a real brain to give this a look when he has time.

In the meanwhile - just thinking out loud here - I think the hardware section of the forums gets less traffic than the "general" section:

[http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

I'm not sure about that though ....................... but if you wanted to get the opinion of the forum mods you could click on the "Report Post" button at the bottom left of your OP and ask their opinion. They're all nice folks and won't mind you asking.

---

### Post by Inoki on 2015-07-20
I am currently on Debian 8 k3.16.0-4 and since I've opened this thread I've tested about all the major distros with kernels from 3.16 up, to no avail. Sound is extremely low w/ distortion.

Tried workarounds such as installing gnome-media to open up gstreamer-properties and change device properties, to no avail. Skype e.g. uses pulseaudio and I can't change that.

I already filed a bug against pulseaudio assuming it's the culprit since Audacity which presumably uses ALSA detects my voice clearly.

Waiting and hoping that someone might come up with something.

---

### Post by info-baehr-koenigsbrunn on 2016-01-16
I had to struggle with the same problem with SFLphone (v. 1.4.1) under linux Mint 17.3 and a Fritz!Box 7390 as VoIP provider. I finally got it working by disabling the g722 codec just after I installed pulseaudio 7.99 from git repository which didn't do any better than the stock 4.0. A quick check with my laptop with linux mint 17.2 (pulseaudio 4.0) approved its the g722 codec.

---

