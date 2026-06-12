---
title: "screwed up GRUB royally"
date: 2009-03-23
forum: Installation &amp; Upgrades
---

### Post by gseeli on 2009-03-23
So yesterday I decided I was going to completely wipe my hard drive clean and repartition it for windows and ubuntu. First I compressed my (almost entire) current ubuntu filesystem and stored it on another computer. I then wiped the hard drive, repartitioned with partition manager live CD, installed windows on hd0,0, installed ubuntu's main file system on hd0,1, installed the swap partition on hd0,2, and installed a shared FAT32 partition on hd0,3. At this point the dual-boot was working just fine, then I decided I was going to restore my previous linux system, taking my archive and completely overriding the new install with the old one. I didn't think about the fact that GRUB was in the old filesystem but wasn't configured for the new partition scheme. Next time I booted up my computer, I was greeted with a friendly ```
grub>
``` and I realized my error #-o. I then tried who knows how many tricks of fixing/uninstalling/reinstalling/etc. GRUB to try and get it to recognize the new partitions. Most of the time I get fatal errors. I am able to boot to windows using a string of commands in GRUB but that is all the progress I have made. So, now the question is, do you have any ideas about how to fix my errors. The other question I was pondering was, should I have made a /boot partition? 

Thanks for any help,
gseeli

---

### Post by meierfra. on 2009-03-24
In order to get a clearer picture of your setup, I suggest to boot from the Ubuntu LiveCD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

