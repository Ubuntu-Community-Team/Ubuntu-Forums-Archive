---
title: "error when booting feisty"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by Taleman on 2007-10-24
the following occurs with any ubuntu derivative including: xubuntu, kubuntu, linux mint.

Ever since I upgraded to gutsy I get this error whenever i try to boot feisty from the live CD

modprobe: WARNING: Not loading module ipv6

 then i get a repeating error that is:

mmcblk0: error 1 sending read/write command.

The reason i was tying to run feisty is because ever since i upgraded to Gutsy ubuntu could not detect my nic card. is there any way this can be fixed?

---

### Post by Taleman on 2007-10-25
> **Taleman said:**
> the following occurs with any ubuntu derivative including: xubuntu, kubuntu, linux mint.

Ever since I upgraded to gutsy I get this error whenever i try to boot feisty from the live CD

modprobe: WARNING: Not loading module ipv6

 then i get a repeating error that is:

mmcblk0: error 1 sending read/write command.

The reason i was tying to run feisty is because ever since i upgraded to Gutsy ubuntu could not detect my nic card. is there any way this can be fixed?

Ok well i no longer get the read/write error, that was being caused by SD card i accidently left in the reader. However taking int out did't solve the problem. Now i get input output errors that look like

[17179740.008000] Buffer I/O error on device Sr0, logical block 207823

---

