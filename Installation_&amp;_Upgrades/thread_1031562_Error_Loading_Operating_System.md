---
title: "Error Loading Operating System"
date: 2009-01-05
forum: Installation &amp; Upgrades
---

### Post by bronzehedwick on 2009-01-05
Hey,

I have a very old Dell Latitude C400 latptop that I tried to install Xubuntu on, with disastrous results. I was hoping to get some help figuring out what, if anything, can be done.

The machine was running windows XP. It has no CD drive, and one USB 1.0 port. I thought partitioning the hard drive and installing Xubuntu to the blank partition would be the best way to work around the lack of CD drive. The partition (seemingly) went fine, but when I restarted the computer, it reads, "Error loading operating system." 

After doing a little research, I figured out that the computer's BIOS is really old, and probably needs to be updated to recognize the partition. But then again, it could be something else. (Note: I can't boot from an external optical drive because the BIOS doesn't recognize it).

So my question is is this thing even worth fixing? and if so, how should I go about fixing the error and loading Xubuntu?

Thanks so much!

---

### Post by maybeway36 on 2009-01-05
If your laptop is old enough, find a DOS floppy somewhere and run the DOS command:
```
fdisk /mbr
```
This will remove GRUB (the Linux bootloader) and hopefully let you boot Windows.

---

### Post by caljohnsmith on 2009-01-05
If you can't boot from the CD drive, then how did you install Xubuntu? It sounds like your computer wouldn't support booting from USB either. If you have some way of booting the Xubuntu Live CD/drive or however you did it, how about posting the output of:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by bronzehedwick on 2009-01-05
> **caljohnsmith said:**
> If you can't boot from the CD drive, then how did you install Xubuntu? It sounds like your computer wouldn't support booting from USB either. If you have some way of booting the Xubuntu Live CD/drive or however you did it, how about posting the output of:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

I didn't successfully install xubuntu yet...i was in the process of portioning when the system crashed. I'm going to trying finding a DOS floppy as suggested by maybeway36 for now. Thanks guys!

---

