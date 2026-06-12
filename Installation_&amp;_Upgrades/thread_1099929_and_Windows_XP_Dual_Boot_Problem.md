---
title: "and Windows XP Dual Boot Problem?"
date: 2009-03-18
forum: Installation &amp; Upgrades
---

### Post by djoe on 2009-03-18
I have Windows XP and Xubuntu installed on the same HardDrive

Windows XP 60GB
Xubuntu 16.5GB

Heres the Problem:

When I push the power button for start-up, no menu shows up for WinXP and Xubuntu boot options, but Windows XP starts as usual.

Can I correct this without, starting the whole process all over again?

---

### Post by taurus on 2009-03-18
Did you install Ubuntu first or after you've installed windows?

Maybe the steps from this guide would help you to recover GRUB.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by djoe on 2009-03-18
I installed Xubuntu first and than WindowsXP.

I selected logical during Xubuntu install.  Could that be the problem?

You know when it says Primary and Logical options.

---

### Post by taurus on 2009-03-18
It doesn't really matter where you install Ubuntu.  When you installed windows after you installed Ubuntu, windows basically wiped GRUB from MBR so you need to look at the link from my previous post to reinstall GRUB back to MBR so you can boot both Ubuntu and windows.

---

### Post by djoe on 2009-03-18
Ok, got ya!

---

### Post by djoe on 2009-03-19
In the terminal I inputted Sudo Grub

It worked, but:
find /grub/stage1

It gave me an error.

---

### Post by gentagelse on 2009-03-19
Well, did " find /boot/grub/stage1 " work? The command " find /grub/stage1 ", is second choice if the first one doesn't works. As far as I can tell from the guide.

---

### Post by djoe on 2009-03-19
both gave an error. Do I have to maybe input it a different way?

I'll try and get the error number. I think though it said error 5.

---

### Post by sahabcse on 2009-03-19
Hi

Try to fix the grub, follow below url

[http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html](http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html)
[http://sahabm.blogspot.com/2009/01/grub-fix-windows.html](http://sahabm.blogspot.com/2009/01/grub-fix-windows.html)

---

### Post by meierfra. on 2009-03-20
In order to get a clearer picture of your setup, I suggest to boot from the Xubuntu LiveCD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by djoe on 2009-03-20
How about [www.neosmart.net]("http://www.neosmart.net/")

Someone suggested easyBCD

I found Gag as well
[http://www.softpedia.com/get/System/Boot-Manager-Disk/GAG-d.shtml]("http://www.softpedia.com/get/System/Boot-Manager-Disk/GAG-d.shtml")

Wouldn't it be easier to recover the boot manager from Windows?

---

### Post by meierfra. on 2009-03-20
Gag relies on Grub to do the booting. So that will not help. EasyBCD  uses either Grub or Grub4Dos. Using Grub4Dos directly or via EasyBCD is an option, but I don't think,  Grub4Dos will make solving your problem any easier.

---

