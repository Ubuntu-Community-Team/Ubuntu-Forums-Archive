---
title: "how install driver VGA"
date: 2013-03-01
forum: Hardware
---

### Post by hilinux on 2013-03-01
hi 
i use Kubuntu kernel : 3.2.6 
[CENTER][COLOR=#3E3E3E][FONT=Tahoma]lspci | grep VGA: 
[/FONT][/COLOR][/CENTER]
```
[COLOR=#3E3E3E]00:02.0 VGA compatible controller: Intel Corporation Device 0166 (rev 09)[/COLOR]
[COLOR=#3E3E3E]01:00.0 VGA compatible controller: ATI Technologies Inc Device 6840[/COLOR]
```[CENTER][COLOR=#3E3E3E][FONT=Tahoma]

how install driver step by step [/FONT][/COLOR][/CENTER]
:P
[CENTER][COLOR=#3E3E3E][FONT=Tahoma]thank you 

[/FONT][/COLOR][/CENTER]

---

### Post by carl4926 on 2013-03-01
This suggest you have hybrid graphics... do you think that is correct?

---

### Post by hilinux on 2013-03-02
yes 
show this (lspci) :
```
00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)00:01.0 PCI bridge: Intel Corporation Ivy Bridge PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Device 0166 (rev 09)
00:14.0 USB Controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4)
00:1d.0 USB Controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc Device 6840
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
08:00.0 Network controller: Intel Corporation Device 0887 (rev c4)



```

thank you

---

### Post by QIII on 2013-03-02
Unfortunately, you are in a difficult situation.

Intel/ATI hybrid graphics setups are a difficult problem in Linux.

I suggest you read through [this thread](http://ubuntuforums.org/showthread.php?t=1930450) first.

There is no making this easy or simple.

Good luck!  Best wishes!

---

### Post by hilinux on 2013-03-02
thank you mr.Qlll

---

