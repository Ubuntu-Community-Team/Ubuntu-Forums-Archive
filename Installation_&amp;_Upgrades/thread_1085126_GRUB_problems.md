---
title: "GRUB problems"
date: 2009-03-02
forum: Installation &amp; Upgrades
---

### Post by Django1200 on 2009-03-02
This is my first linux install since about 2000 and I'm having a wierd problem. I'm trying to install on a SCSI drive and am having this same problem over and over. After the install the computer tries to boot from the drive and I get a No OS present error. I know it's a problem with GRUB because lilo works fine. I believe that GRUB is installed in the wrong place; as in the case of lilo, I can choose to place it in the MBR. My questions are 1) Why is GRUB doing this? and 2) How do I fix it?. I'd appreciate any help with this as it is driving me nuts. Thanks

---

### Post by renebs on 2009-03-02
I have had similar problem, from what I understood happens in your case, before. Basically, when I had this problem Grub was being written to a drive/partition instead of MBR.
If this is the problem, this post might help [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

sorry not much of a help

---

### Post by caljohnsmith on 2009-03-02
In order to get a clearer picture of your setup, how about booting your Ubuntu Live CD (the Ubuntu install CD), download the **Boot Info Script** to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

