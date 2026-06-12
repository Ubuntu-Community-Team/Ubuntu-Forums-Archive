---
title: "Winmodem trouble"
date: 2007-01-28
forum: Hardware &amp; Laptops
---

### Post by JermainWijnhard on 2007-01-28
Problem:
Winmodem causing high blood pressure, lot of cursing and stress.

Attempts:
- used scanModem to make some .txt files. Cant make sense of them, sent the .txt file to [email]discussion@linmodems.com[/email] (or something like that).
- rand unload.gz

I do not know how to make out which driver i need and i'm getting desperate. All and any help is welcome!

---

### Post by contadinoste on 2007-01-28
Post the modemdata.txt here.

---

### Post by JermainWijnhard on 2007-01-29
Thank you! I'm at work now and can't connect my laptop to my desktop here so I'll just type it over because im too impatient to wait till i'm home.

-- System Information --
CPU=i686, Ubuntu 6.10
Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18"45:35
UTC 2006 (Ubuntu 2.6.17-10.33-generic)
 scanModem update of: 2007_Jan_22


USB modem not detected by lsusb

Modem or host audio card candidates have firmware information:
PCI slot         PCI ID             SubsystemID       Name
------------     ------------        ------------           ---------------
00:1e.3         8086:266d        1179:0001          Modem: Intel Corporation 82801FB/FBM/FR/PW/FRW

Modem interrupt assignment and sharing

--- Bootup diognostics for card in PCI slot 00:1e.3 ---
[17179573] APCI: PCI Interrupt 0000:00:1e.3[B] -> GSI 20 (level, low) -> IRQ 177
[17179573] APCI: PCI Interrupt for device 0000:00:1e.3 disabled

The PCI slot 00.1e.3 of the modem card may be disabled early in a bootupproces, but then enabled later. If modem drivers load but the modem is not responsive, read Bootup.txt about possible fixes.
send dmesg.txt along with ModemData.txt to [email]discuss@linmodems.org[/email] if help is needed.


=== Finished modem firmware and bootup diagnostics section ===
=== Next deducing cogent software ===

ALSAversion 1.0.11

---

### Post by contadinoste on 2007-01-29
It's all of the file?  It's not that I understand a lot, I just managed twice make a winmodem work, with help from scanmodem and linmodem. Usually they answer. It looks similar to my system, with smartlink modem working now (slmodemd). If you sent those two files to linmodem.org there's hope. When you run scanmodem again  (renaming the "modem" folder first) at a fresh boot the output is the same?

---

### Post by JermainWijnhard on 2007-01-29
output is the same after a fresh boot :/

---

### Post by JermainWijnhard on 2007-01-31
Okay after several attempts i got another output with more txt files and what they basically came down to was that i needed SLModemD.gcc4.tar.gz i went and got it but didnt know what to do with it (even with the .txt files' help). So went to the Kubuntu IRC and got a link in the ubuntu wiki, where i followed the link and dl'd SL-modem-daemon.deb and installed it according to the description. But it didnt work.
I went to Adept Manager and looked up the Package relationships and at one of the relations it says "conflict: sl-modem-modules". Any advice / help?

---

