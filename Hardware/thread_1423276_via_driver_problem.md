---
title: "via driver problem"
date: 2010-03-06
forum: Hardware
---

### Post by azerty123 on 2010-03-06
hello everybody

i'am newbie and i have installed ubuntu 9.10 since 1 month, and i have no idea about the way we install drivers on it. i'm facing a serious problem with my graphic card, i googled alot with no happy ending..

lspci output:

```

00:00.0 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. CN896/VN896/P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:03.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. Device 5372
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237S PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (rev 01)
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)

```

i want to enable desktop effects, please help :icon_frown::cry:

---

### Post by Venom05 on 2010-03-06
i have the same problem 2... 

some help ?

---

### Post by azerty123 on 2010-03-06
up

---

### Post by IcarusR on 2010-03-06
From my googling results it would seem that this card is not well supported under linux.

Google for "via CN896/VN896/P4M900 ubuntu" & read the results.

There are various drivers around, all with varying degree of success. 
General consensus seems to be that card is not good for games or eye candy.

---

### Post by Uli_of on 2010-03-06
From my googling results it would seem that this card is not well supported under linux.

Google for "via CN896/VN896/P4M900 ubuntu" & read the results.

There are various drivers around, all with varying degree of success. 
General consensus seems to be that card is not good for games or eye candy.[/QUOTE]



There is a thread about Samsung &#925;C20 chipset VX800 with a lot of information
Look also for openchrome.org . The is an VIA driver available.

---

### Post by azerty123 on 2010-03-08
where is that thread?

---

### Post by Uli_of on 2010-03-08
> **azerty123 said:**
> where is that thread?

[http://ubuntuforums.org/showthread.php?t=1079314](http://ubuntuforums.org/showthread.php?t=1079314)

---

### Post by azerty123 on 2010-03-08
thx a lot [Uli_of]("http://ubuntuforums.org/member.php?u=913962")
i'll take a look

---

