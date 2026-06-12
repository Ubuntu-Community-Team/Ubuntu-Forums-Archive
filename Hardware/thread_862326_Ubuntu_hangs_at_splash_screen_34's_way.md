---
title: "Ubuntu hangs at splash screen 3/4's way"
date: 2008-07-17
forum: Hardware
---

### Post by ethanklein on 2008-07-17
I love ubuntu and it works very well but one thing that has been going on for quite some time is ubuntu will hang 3/4's way. I tried ctrl+alt+f1 but that shows loading... Im really confused as to why it typically takes like 3min to boot up 8.04. On my sister's laptop, my desktop, and my mother's desktop it usually takes a minute max before they get to login screen. Hope you can help. I have a theory that its my grpahics card. I've been readin the ATI Xpress 200m is crap with ubuntu... pretty much.

---

### Post by Yannick Le Saint kyncani on 2008-07-17
I'd start booting without "quiet splash", so in grub, press "e" to edit, then go to the kernel line, press enter, and replace "quiet splash" with "nosplash". Enter to confirm and then "b" to boot.

This will show you the boot process and hopefully you will see where it hangs and get a nice error message.

---

