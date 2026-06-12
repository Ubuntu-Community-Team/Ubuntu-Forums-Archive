---
title: "PM1554U2  - &lt;0&gt;Kernel panic - not syncing: Fatal exception in"
date: 2005-10-21
forum: Hardware &amp; Laptops
---

### Post by Belfast on 2005-10-21
Hi all,

Im new to ubuntu and have had 5.4 installed for a couple of months now. i did an apt-get distupgrade & on reboot i got this error.

<0>Kernel panic - not syncing: Fatal exception in interrupt 
i rebooted & selected the 2.6.10 kernel & it booted fine

i downloaded the iso for ubuntu 5.10 and found that i got the same error during the installation proccess.
i guessed my problem might be hardware realted so i swapped ram etc until i found that my scsi controller a  PM1554U2 (Adaptec Intelligent Ultra2 SCSI Controller ) was the culprit

my motherboard is an asus P2b-DS

its quite old and im a bit wondering if the support for this card has been dropped.

---

### Post by Kyral on 2005-10-21
Could be. Keep in mind there is nothing wrong with using an old kernel.

What you COULD do is compile your own kernel, while keeping the config of the old one.

[https://wiki.ubuntu.com/KernelCompileHowto](https://wiki.ubuntu.com/KernelCompileHowto)

---

### Post by r4v on 2006-01-31
im trying to do a fresh install of kubuntu and im gettin the same error message and it goes no further :S

---

