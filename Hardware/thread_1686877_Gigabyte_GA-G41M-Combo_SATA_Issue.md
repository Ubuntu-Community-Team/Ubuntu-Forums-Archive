---
title: "Gigabyte GA-G41M-Combo SATA Issue"
date: 2011-02-13
forum: Hardware
---

### Post by WiseHacker on 2011-02-13
Hopefully a Guru here can solve this problem for me.

I am currently running Ubuntu 10.10 with a Gigabyte GA-G41M-Combo mother board.  I currently have a 80GB IDE drive and a 1TB Sata II drive attached. 80 runs the operating system and the 1TB drive was only installed recently.

So far, I have been able to read and write to the drive but I have noticed that the IO performance seems a bit slow.  I ran a check with lspci and dmesg and it seems that my Sata drive is still being treated like an IDE drive.

From what I can gather, Ubuntu is using the Intel SATA IDE Controller on my chipset.  As a result, all drives show as PATA drives and run using UDMA/100.

My question is this, does the board *really* support SATA II?  The closest option I could find in the BIOS for SATA is "Enhanced".  According to the documentation it treats Sata drives as Sata drives but Ubuntu seems to think otherwise.

As I come from a Windows background, any help would be greatly appreciated.  I am at a total loss as to why I cannot get either Ubuntu (or my mother board) to take advantage of SATA II.

In the event this helps, I have also used hdparam on the drive and it does not list any SATA features.

My thanks in advance.

---

