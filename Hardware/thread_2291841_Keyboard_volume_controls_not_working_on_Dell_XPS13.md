---
title: "Keyboard volume controls not working on Dell XPS13 with 15.04"
date: 2015-08-23
forum: Hardware
---

### Post by potatan on 2015-08-23
Hi,

I have a [Dell XPS 13]("http://www.dell.com/support/home/uk/en/ukbsdt1/product-support/product/xps-13-9343-laptop/diagnose") running Ubuntu 15.04 with the latest BIOS.  It took a few tweaks to get any sound out at all, but this is now working through the speakers and headphones.  

The only remaining problem is that I can't get the volume controls on FN+F1, F2, F3 to do anything. I have tried switching the BIOS to not require the FN key but that didn't help.  Also, the top panel Ubuntu volume control slider doesn't affect the volume.

Soundcard info:
```
xxxxxx@XPS:~$ sudo lshw -C multimedia
  *-multimedia:0          
       description: Audio device
       product: Broadwell-U Audio Controller
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:00:03.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:50 memory:f741c000-f741ffff
  *-usb:3
       description: Video
       product: Integrated_Webcam_HD
       vendor: CN09GTFM72487524A5RMA00
       physical id: 5
       bus info: usb@1:5
       version: 49.22
       serial: 200901010001
       capabilities: usb-2.01
       configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
  *-multimedia:1
       description: Audio device
       product: Wildcat Point-LP High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=snd_hda_intel latency=32
       resources: irq:49 memory:f7418000-f741bfff

```

Has anyone resolved this?

I've searched quite a lot but the only solutions I find are to the problem with no sound, rather than specifically with the controls not working

Thanks in advance.

---

### Post by TheFu on 2015-08-23
a) I have complete ultrabook envy!!!  Saw one a few days ago with the super detailed display. It was about the same size as my $200 chromebook, but oh so much different.  The guy with it didn't buy it - corporate system - almost 10x more expensive than mine.

b) I haven't run the default Ubuntu desktop since 2011 (Unity).  However, by running openbox, I can control all the keys and remap any to any function needed.  Unity can probably do this too - I just don't know how.  Here are my keybindings in the ~/.config/openbox/rc.xml file. Unity will do it differently, so don't copy this blindly.
```
<!-- Keybinding for Volume management -->
  * 
<keybind key="XF86AudioRaiseVolume">
*  * *<action name="Execute">
*     ** *<command>amixer -q sset Master 3%+</command>
* *   </action>
  * </keybind>

  * <keybind key="XF86AudioLowerVolume">
* * * <action name="Execute">
* ** *    <command>amixer -q sset Master 3%-</command>
* *   </action>
  * </keybind>

  * <keybind key="XF86AudioMute">
* * * <action name="Execute">
* ** *    <command>amixer -q sset Master toggle</command>
* *   </action>
  * </keybind>
```

Make sense? The asterisk characters got added by the forum software for some reason I don't understand. I've never seen that before.

To get audio working might be easier or very difficult.  Post the output from **aplay -l** to start, please.

---

### Post by potatan on 2015-08-23
aplay -l  output:
```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC3263 Analog [ALC3263 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by TheFu on 2015-08-23
So it looks like you have 4 possible audio outputs. If you want speakers to work, use "card 1" - looks like hw:1,0 is the device for that. I like **alsamixer** for this stuff - it is simple and works on desktops AND servers. Inside Alsamixe, pick the correct output device first, then verify *automute* isn't enabled for any of the output controls.  'm' toggles it in alsamixer. You don't want to see "mm" at the bottom of any vertical bar. That area needs to show a number from 0 - 100; 70+ is what I need to hear anything on my netbook.

Hope this is enough to get you going.

If you want one of the video outputs (HDMI 1-3) to have audio, the the other devices will need to be tried to figure out which goes to which through the video cables. Also use alsamixer and check the automute stuff as described above.

---

### Post by potatan on 2015-08-24
Hi, thanks for your advice, but all the speaker/audio outputs work fine as it is.  

The only problem I have is getting the keyboard volume controls to do anything

Edit: photo added

These keys: [http://imgur.com/0EzjO9K]("http://imgur.com/0EzjO9K")

---

### Post by TheFu on 2015-08-24
The keybind stuff above is all I know. Does the "Ubuntu Desktop Guide" cover keymapping? The commands above can be used to raise, lower, mute audio.

---

### Post by potatan on 2015-08-25
Thanks, I'll have a look at keybindings and see if I can use the commands you metioned

---

### Post by potatan on 2016-04-05
This has now been fixed, I downloaded the latest Kernel 4.4 and installed that - two reboots later and the softkeys are functioning perfectly. Posting this in case it helps someone else.

---

