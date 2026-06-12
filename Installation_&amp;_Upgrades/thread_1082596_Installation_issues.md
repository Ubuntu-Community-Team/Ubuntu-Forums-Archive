---
title: "Installation issues"
date: 2009-02-27
forum: Installation &amp; Upgrades
---

### Post by BAshworth13 on 2009-02-27
First off, let me apologize if this question has already come up.  I did a search through the forums here, as well as via Google, and didn't come up with anything that was directly similar to what I was experiencing.

I have a computer with two sata hard drives.  Sata 0 is my Windows XP installation (wife hates linux, so I have to play nice), and I'm trying to install Ubuntu onto the second hard drive (sata 1).

First time I went through the installation, it completed with no issues.  However, on the first reboot, the computer went straight into Windows XP.  It never brought up Grub.

I re-did the installation, this time checking where it was installing Grub, and saw that it was putting it on hd0.  I changed it to be sbc (might have been sdc) which is the disc that Windows is installed on.

Again, no errors during the installation, but when the computer rebooted, it brought up a blank screen with just the word 'GRUB' on it, and a blinking cursor.

I can get back into windows now (hence my ability to post here).

So... what do I need to do in order to get GRUB to load, and let me get into my Ubuntu installation?  Any direction, assistance, etc. would be greatly appreciated.

Again, if this situation has been posted and answered before, can someone provide a link to that thread?  Since my own searching has proven fruitless so far.

---

### Post by sukhhari on 2009-02-28
First you need to do one thing Boot System with Windows Bootable CD and select into recovery mode and try to delete the partition of raw of Ubuntu Installation.

Then try to boot windows first and try installation on HDD 2 Ubuntu.

---

### Post by caljohnsmith on 2009-02-28
Can you change your BIOS to boot the Ubuntu drive on start up instead of the Windows drive? If so, you could install Grub to the MBR of your Ubuntu drive and that will probably fix your problem. But in order to get a clearer picture of your setup, how about booting your Ubuntu Live CD (the Ubuntu install CD), download the **Boot Info Script** to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

