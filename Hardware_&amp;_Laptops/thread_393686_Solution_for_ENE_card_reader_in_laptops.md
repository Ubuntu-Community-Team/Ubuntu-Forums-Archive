---
title: "Solution for ENE card reader in laptops"
date: 2007-03-26
forum: Hardware &amp; Laptops
---

### Post by dptxp on 2007-03-26
I have posted this in beginners forum, but have received no reply so far.

The solution to detect SD cards in UBUNTU is to use KERNEL 2.6.20-11
as per this page.

[http://www.linuxquestions.org/questi....php?p=2673740](http://www.linuxquestions.org/questi....php?p=2673740)

Has anyone tried ?

Can anyone tell me how I upgrade the KERNEL ?
Can anyone tell me how I upgrade in 64-bit EDGY EFT ?
WHAT is the KERNEL in FEISTY ?

Solution as per referred page:

There is a fix for ENE controllers in the 2.6.20 series; if you're using Ubuntu kernels, you should upgrade to 2.6.20-11 which has this fix, and then try with sdhci again to see if you can read SD cards

Response of one user:
Ok I updated to the 2.6.20-11 ubuntu kernel and it works perfect.

__________________

---

### Post by s0cket on 2007-03-26
Odd my SD card reader works with Edgy no modifications needed.

---

### Post by jpneron on 2007-03-27
It depends on the type of reader. The ENE cardreader seems to be a problem. 

You can do a 'lspci|grep Card' to see what kind of reader you have.

---

### Post by HarshReality on 2007-08-29
Page not found... if I might ask what version ENE are you using? I noticed fixes for the 712 but mine is a 710 and those fixes dont apply.

---

