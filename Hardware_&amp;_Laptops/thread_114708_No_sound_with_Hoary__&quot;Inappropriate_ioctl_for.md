---
title: "No sound with Hoary / &quot;Inappropriate ioctl for device&quot;"
date: 2006-01-09
forum: Hardware &amp; Laptops
---

### Post by miahfost on 2006-01-09
Hello there,

I am having some sound issues in Hoary and have not found anything in these forums or in Google which might reveal a solution. 

I have a new Labtec speaker system which fails to produce sound. However my headphones are usable. This leads me to conclude that I do have a functioning soundcard but am not sure it is being seen, here is the output of lspci:

0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
0000:00:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8233A ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
0000:00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
0000:00:14.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
0000:00:14.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
0000:00:14.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV15 [GeForce2 GTS/Pro] (rev a4)

Here are the error messages I get from XMMS when trying to stream some radio;

** WARNING **: SNDCTL_DSP_SETFMT ioctl failed: Inappropriate ioctl for device
** WARNING **: SNDCTL_DSP_SPEED ioctl failed: Inappropriate ioctl for device

I have chmoded /dev/dsp and /dev/mixer just to make sure it was not a permissions issue. 

I would like to know how do I determine the make and model of my sound card?
Do I need to insert a module into the kernel?
Should I just upgrade Ubuntu to Version 5.10 which I have here on disk instead?

Thanks for any guidance!

Jeremiah

---

