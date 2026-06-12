---
title: "3TB install"
date: 2013-05-09
forum: Hardware
---

### Post by pdlethbridge on 2013-05-09
I put in my 3TB in the computer and its off and runing how  I got it to run I don't know, I think it was creat partition table which is now gpt. I have about 9 partitipions on it but no extended partitionsfile:///home/paul/Pictures/Screenshot%20from%202013-05-09%2018:54:04.png

---

### Post by hansdown on 2013-05-09
Hi  pdlethbridge.

All your file systems appear to be ext4.

Sorry if I'm misunderstanding the question.

---

### Post by pdlethbridge on 2013-05-09
I really don't know how I got it going so soon As you saw every thing is extention 4 but thats changable

---

### Post by hansdown on 2013-05-10
If it's working, that's the best part.

Nice job.

---

### Post by oldfred on 2013-05-10
One of the advantages of gpt over the 30 year old MBR(msdos) is that you do not have primary, extended and logical partitions. You just have partitions. But at the rate you are going you may run into the new limit of 128 partitions. :)
I think some utilities may run out of numbers first. 

If you are installing Ubuntu in BIOS mode you have  to have a tiny 1MB unformatted bios_grub partition any where on drive. And if booting with UEFI the first partition is supposed to be the efi partition for boot files.

 GPT Advantages (older but still valid)  srs5694 post #2:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)

---

