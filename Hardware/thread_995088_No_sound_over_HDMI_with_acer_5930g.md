---
title: "No sound over HDMI with acer 5930g"
date: 2008-11-27
forum: Hardware
---

### Post by bug11 on 2008-11-27
Hello, I am pretty new with linux, only had it for 1year, and just bought a Acer aspire 5930g notebook. Running ubuntu 8.10 x64 and everything works exept sound over HDMI cable.

my aplay -l shows:
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

and my lspci:

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9600M GT (rev a1)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8071 PCI-E Gigabit Ethernet Controller (rev 16)
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100

I dont know whats wrong. I get Video but no sound. My headphone jack is not working either, sound chip not recognize the jack-input. It is not a big deal, just wondering. 

Hope anyone know something. Thank you for your patient with me

---

### Post by Xyem on 2009-02-05
Hey, I have a Acer Aspire 5930 and have the same issues ( headphone jack doesn't work at all and no sound over HDMI ).

I'm looking to the HDMI sound issue at the moment, I'll post back if I find anything conclusive.

---

### Post by Xyem on 2009-02-05
Upgrading to ALSA 1.0.19 worked for me. It created the appropriate nVidia HDMI audio hardware.

The script was here: [http://ubuntuforums.org/showthread.php?p=6589810#post6589810]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810")

> $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Just a small warning. After upgrading I've noticed there is a audible crackle as you change volume ( through alsamixer  for example ). I've noticed this on another laptop with 1.0.18 too though.

---

### Post by xwang on 2009-02-07
> **Xyem said:**
> Upgrading to ALSA 1.0.19 worked for me. It created the appropriate nVidia HDMI audio hardware.

The script was here: [http://ubuntuforums.org/showthread.php?p=6589810#post6589810]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810")



Just a small warning. After upgrading I've noticed there is a audible crackle as you change volume ( through alsamixer  for example ). I've noticed this on another laptop with 1.0.18 too though.

Do you mean that upgrading alsa you have solved both the audio on HDMI and the headphone issues?
Xwang

---

### Post by Xyem on 2009-02-07
> Do you mean that upgrading alsa you have solved both the audio on HDMI and the headphone issues?
Yes.

In regards to the headphones, I had to set ALSA to 6ch so the laptop speakers got muted correctly. One channel(?), 'Side' was not muted automatically when the headphones were plugged in.
However, 6ch stops my 'Line In' which only works in 2ch.

The crackling also seems to no longer be present, perhaps due to the 6ch setting but I am not sure.

---

### Post by xwang on 2009-02-07
> **Xyem said:**
> Yes.

In regards to the headphones, I had to set ALSA to 6ch so the laptop speakers got muted correctly. One channel(?), 'Side' was not muted automatically when the headphones were plugged in.
However, 6ch stops my 'Line In' which only works in 2ch.

The crackling also seems to no longer be present, perhaps due to the 6ch setting but I am not sure.

So the acer 5930G is perfectly compatible with ubuntu or there are other components that do not work correctly?
Xwang

---

### Post by Xyem on 2009-02-07
My laptop is the Acer Aspire 5930. I don't know the differences between a 5930G and the 5930 but..

I should really test the microphone and the bluetooth but I don't have any need to use them ( I'd be happy to test them if it is something you need to know before a purchase ).

The only thing I have found to not work at all is the card slot. It looks like Ubuntu cannot see it at all ( doesn't seem to be in lspci ).

Everything else works. Wireless, camera, graphics chipset, touchpad, suspend, those touch sensitive things on the right of the keyboard.. all work fine. The button above those touch sensitive things doesn't seem to do anything though.

Overall, I'm very happy with this laptop, everything that matters to me works and it plays games well. I get an hour of gaming on a full battery too. The only other issues I can think of is sometimes it seems the kernel panics coming out of suspend ( maybe once every 50 resumes? ) and there is no scroll lock LED ( Acer seemed to think it wasn't important.. )

I hope this helps you.

---

### Post by xwang on 2009-02-07
> **Xyem said:**
> My laptop is the Acer Aspire 5930. I don't know the differences between a 5930G and the 5930 but..

I should really test the microphone and the bluetooth but I don't have any need to use them ( I'd be happy to test them if it is something you need to know before a purchase ).

The only thing I have found to not work at all is the card slot. It looks like Ubuntu cannot see it at all ( doesn't seem to be in lspci ).

Everything else works. Wireless, camera, graphics chipset, touchpad, suspend, those touch sensitive things on the right of the keyboard.. all work fine. The button above those touch sensitive things doesn't seem to do anything though.

Overall, I'm very happy with this laptop, everything that matters to me works and it plays games well. I get an hour of gaming on a full battery too. The only other issues I can think of is sometimes it seems the kernel panics coming out of suspend ( maybe once every 50 resumes? ) and there is no scroll lock LED ( Acer seemed to think it wasn't important.. )

I hope this helps you.

Could you test the microphone and bluetooth, please?
Xwang

---

### Post by Xyem on 2009-03-02
Something going on with these forums, I don't get e-mail notifications anymore.

I'll test these tonight when I get home from work.

---

