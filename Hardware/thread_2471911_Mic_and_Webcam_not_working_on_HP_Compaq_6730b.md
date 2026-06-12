---
title: "Mic and Webcam not working on HP Compaq 6730b"
date: 2022-02-12
forum: Hardware
---

### Post by 1xx12 on 2022-02-12
Hello everyone,

I have various problems on my ubuntu 20.04 LTS 64bit installed on a notebook HP Compaq 6730b:

1) internal mic not working
2) external mic not working
3) webcam not working

I have a tried to mess around with alsamixer, but I got absolutely no sound from the microphone not matter what I do.

I need your help, ubuntu forum community, to get those devices working (or at least _the microphone_), please.

P.S.: the computer not have all the original hardware: it have 4gb of ram, an SSD and Intel® Core™2 Duo CPU P8600 CPU.

---

### Post by him610 on 2022-02-12
Please show results within code tags of these commands...
```

lsusb
lspci

```

---

### Post by 1xx12 on 2022-02-12
> **him610 said:**
> Please show results within code tags of these commands...
```

lsusb
lspci

```

Sure him610, here the results of lsusb:
```
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 08ff:2810 AuthenTec, Inc. AES2810
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

And here the results of lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
44:00.0 Ethernet controller: Broadcom Inc. and subsidiaries NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
```

---

### Post by him610 on 2022-02-13
I don't have an HP laptop, but I do have an HP all-in-one which I booted up with Xubuntu 20.04.3 from a USB stick. 
Using both* lsusb* and *lspci*, I could not see any indication of internal camera or microphone. Bigly mystery!
I did get the camera to work using *cheese*. It doesn't come with the initial *buntu setup, but it can be installed. 
Using *pavucontrol*, you can check your input devices, hopefully, your internal microphone will show up there.
Good luck.

---

### Post by 1xx12 on 2022-02-14
> **him610 said:**
> I don't have an HP laptop, but I do have an HP all-in-one which I booted up with Xubuntu 20.04.3 from a USB stick. 
Using both* lsusb* and *lspci*, I could not see any indication of internal camera or microphone. Bigly mystery!
I did get the camera to work using *cheese*. It doesn't come with the initial *buntu setup, but it can be installed. 
Using *pavucontrol*, you can check your input devices, hopefully, your internal microphone will show up there.
Good luck.

I installed "pavucontrol" and try to bring to the maximum the audio levels and also try to change the "fallback" option, no results, the microphone looks like is dead.

I forgot to specify, the microphone shows in the pavucontrol and on the audio section of the ubuntu settings (as "internal microphone-internal audio" then to "front microphone-internal audio")

As for the webcam, I tryed to do an "sudo apt-get remove --purge cheese" and then install it again, but the webcam still not working.

P.S.: "It doesn't come with the initial *buntu setup, but it can be installed." my ubuntu installation always had it included.

---

### Post by 1xx12 on 2022-03-09
Up

---

### Post by QIII on 2022-03-09
Hello!

Feel free to bump your thread 12 hours after receiving your last (or no) response -- but no sooner, please.

If you wait three weeks, your thread will sink down to the bottom of the sea with the whale bones to be buried in the muck where nobody will see it.

---

### Post by 1xx12 on 2022-03-22
Up

---

### Post by Autodave on 2022-03-22
Try booting to your install medium and then choose "Try Ubuntu" and see if they work.

---

### Post by 1xx12 on 2022-03-28
> **Autodave said:**
> Try booting to your install medium and then choose "Try Ubuntu" and see if they work.

Thank you very much for the suggestion Autodave!

I was searching for the option in my bios to enable the boot from the usb disk, when I found that webcam and microphone were disabled.

After turning on the two devices, the ubuntu system recognized the microphone and the webcam correctly.

I'm sorry to have wasted the time of him610 and everyone else, when the answer was next to me.

P.s.: in the bios, to enable the microphone, you need to enable the webcam too. Turning on only the microphone and not the webcam result in the microphone not working.

---

### Post by him610 on 2022-03-28
> I'm sorry to have wasted the time of him610 and everyone else, when the answer was next to me.
Hey! That's okay - definitely not wasted. Probably half the issues posted here can be traced back to 'headspace' problems. 
I follow these forums to learn things from others - like you, and I have learned a lot over the years. 
Occasionally, I am familiar enough with a topic to offer some advice.

---

