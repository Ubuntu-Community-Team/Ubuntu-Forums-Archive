---
title: "How long to install 8.10, any progress indicators?"
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by ShaunMo on 2009-04-10
I have a pretty new (2007) laptop rendered inoperable after Vista tried to auto update itself in 2008. I have my data off of it, so I thought I would try to "start over" by installing Ubuntu.

Downloaded 8.10 and it seems like I successfully made a boot disc (on DVD). Booted off that drive and got an Ubuntu install screen. Encouraged, I selected "Install Ubuntu."

The DVD started whirring, but no changes in about 4 hours. It's on the same screen with the "Install Ubuntu" choice still highlighted, but I can't cursor off of it now to anything else. DVD still spinning.

Surely if this was installing it wouldn't take this long and there would be some indication of progress? Is this install just hung up? Any suggestions?

Thanks in advance for any help.

---

### Post by Partyboi2 on 2009-04-10
Your install seems to be hung up, try adding this boot option to see if you can get past the hang up. At the main menu press F6 and at the end of the line add ```
noacpi
``` and then press enter to boot.
Also if you have not already see if you can check the cd for defects (one of the options at the main menu screen)

---

### Post by ShaunMo on 2009-04-10
Thanks. I gave up on that install (shades of Windows) and now I'm scanning the hard disk. Once I'm done with that, I'll try the CD scan too... although brand new, out of the box, then burned the Ubuntu OS on it, so I have to think that's good. It's actually a DVD+R, but that wouldn't make a difference, would it?

I saw that F6 option, so after the disk checks I'll try that and see if I can figure out how to add that command. Thanks so much for your advice.

---

### Post by adamitj on 2009-04-10
More considerations about your post:

1) If you downloaded an ISO file for CD-ROM (usually between 600 ~ 700 MB), you should burn it into a CD-ROM (CD-R or CD-RW). AFAIK, CD and DVD have different section blocks for booting an image, so you can have problems when trying to boot a CD image from a DVD - please someone correct me if I am wrong;

2) If your problem is with ACPI, you'll be able to start the installation. After the loading of kernel (it will appear a progress bar after <ENTER> on try or install ubuntu options) the OS progress bar (orange) should stops after a few seconds. In this case, I recommend you to use the option```
acpi=noirq
```instead of```
noacpi
```if this option works for you. Disabling ACPI will brings you some problems with power management the same way I had (my laptop is a HP Pavilion) and the OS will hang sometimes when is about to turn off the display - especially when running on battery mode;

3) Once my option described on item 2) worked fine for installation, you'll need to add this option in **/boot/grub/menu.lst** file.

---

### Post by ShaunMo on 2009-04-10
I downloaded 8.10 from the website to a DVD and then did the ISO thing from there to another DVD because that's what I had laying around and tried to boot from that. I think I might try burning again to a CD just to rule that out. Thanks. My laptop is also HP Pavillion.

Oh, and for clarity, the downloading and burning was on another machine because the laptop doesn't do anything at this point.

---

### Post by ShaunMo on 2009-04-11
Switching from a DVD to a CD was all it took.

I went out and bought some CDs today and burned the ISO again. Totally different experience right from the start. Booted up to full operating system right from the disc. First time I had seen anything besides an endless loop of a Windows flash screen/blue screen/reboot since last summer, exciting.

Installed from the CD to the hard drive, now I'm booting off the hard drive, easily installed my wireless driver, and making this post is the first productive thing I've been able to do on this laptop in almost a year. Praise Ubuntu, very clean install.

Thanks so much for the suggestions, I'm sure I'm not alone in appreciating experienced users cruising the install forum to help out new users and experimenters.

---

### Post by adamitj on 2009-04-12
Congratulations! :)

Switching from MS Windows to Ubuntu will bring you a lot of new experiences, but you'll need to change your mind too. Ubuntu is Linux, that means it is based on inter-dependent packages (one depending of some other ones). There is no .EXE or .MSI to install software, it's all done with .DEB or from source compilation.

I hope you enjoy Ubuntu the maximum you can. After 2 years of maintaining a dual boot on my notebook, now I have the pleasure to say I abandoned Windows and I am using Ubuntu in home and office.

Other thing is: Ubuntu is not perfect. As any OS might be. You can find some problems and bugs, but in this forum you can get help for all of these.

Enjoy Ubuntu!

---

