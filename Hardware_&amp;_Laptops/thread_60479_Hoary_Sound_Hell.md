---
title: "Hoary Sound Hell"
date: 2005-08-28
forum: Hardware &amp; Laptops
---

### Post by cheepgeek on 2005-08-28
I have tried many posts to get sound for my creative s/b live. When i try to use scrips that are posted, I get the message that alsa is not installed......but when i apt-get alsa it tells me that the latest version is already installed. Alsamixer in terminal says there is no sound device, but my card is recognized by ubuntu. Please........can anyone help with this problem?   ](*,)

---

### Post by joshmachine on 2005-08-28
Have you checked the permissions on your sound device.  See the second half of the following post for what I am talking about.

[http://www.ubuntuforums.org/showthread.php?t=60491](http://www.ubuntuforums.org/showthread.php?t=60491)

---

### Post by cheepgeek on 2005-08-28
Here is the output showing my sound card.....0000:00:00.0 Host bridge: VIA Technologies, Inc. VT82C598 [Apollo MVP3] (rev 04)0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C586/A/B PCI-to-ISA [Apollo VP] (rev 47)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 02)
0000:00:07.3 Host bridge: VIA Technologies, Inc. VT82C586B ACPI (rev 10)
0000:00:11.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
0000:00:13.0 Multimedia audio controller: Creative Labs SB Audigy LS
0000:00:14.0 USB Controller: OPTi Inc. 82C861 (rev 10)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]

It also appears that I have permission to access audio. ANy other suggestions?

                                                                                                 Thanks,Jeff

---

