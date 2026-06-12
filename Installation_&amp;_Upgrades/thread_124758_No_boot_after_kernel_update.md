---
title: "No boot after kernel update"
date: 2006-02-02
forum: Installation &amp; Upgrades
---

### Post by miyet on 2006-02-02
Hi
I'm new to this but getting there \\:D/ or was until I accepted an upgrade. I have searched the forums but all similar scenarios have only given limited help. 

My system is a HP laptop running Win XP and Ubuntu 5.10 under acronis partition/boot manager. Ubuntu is set up with 3 partitions -  /Boot as the first partition on the drive, / , and /swap

On reboot after the automatic upgrade from 2.6.12-9-386 to 2.6.12-10-386 I selected Ubuntu from the acronis boot manager and was given a blank screen with the word GRUB (not the grub shell). I ran the install CD rescue mode and did grub-install. This now gives me the grub shell from which I can can get the boot started but fails and drops back to shell

I am intendng to reinstall Ubuntu but would welcome advice on how to avoid the problem again.

Thanks

---

### Post by linuxden on 2006-02-02
what error message do you get when GRUB loads??

---

### Post by darth_vector on 2006-02-02
in the boot manager you are using are you given the option of running your old kernel?

---

### Post by miyet on 2006-02-02
Apologies for the delay.. In response to the questions in the 2 previous posts.. 

1. From the grub prompt - I have tried with

root (hd0,2)
kernel /vmlinuz-2.6.12-10-386 root = /dev/hda6 ro single
initrd /initrd.img-2.6.12-10-386
boot

This appears successful though the screen is too fast to read. It comes to the "mount file system", attempts to run a script and gives a message that no volumes are found and drops to shell prompt - same when I sub the previous kernel ver - change 10 to 9 ??

2. the acronis partition manager does not give alternate kernel access but does allow to explore partitions - did not seem to be anything untoward in menu.lst - both kernels are listed 

A question - If I am using a partition manager, would it be better to include the /boot with the /  partition instead of separate?

Thanks for responses

---

