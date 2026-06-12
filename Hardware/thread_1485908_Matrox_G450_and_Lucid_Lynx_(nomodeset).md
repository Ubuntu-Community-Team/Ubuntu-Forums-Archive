---
title: "Matrox G450 and Lucid Lynx (nomodeset)"
date: 2010-05-17
forum: Hardware
---

### Post by mod-jkl on 2010-05-17
Hi,

I have a matrox G450 graphic card, Lucid Lynx doesn't make it work correctly (desktop is not displayed properly). I tried to add nomodeset in the grub configuration file but it doesn't work (adding nomodeset to the boot command line, at boot time, works, but I can't do that all the time, and they are other persons who uses this pc)..

Any solution to this problem ?

Thanks for any help

---

### Post by mod-jkl on 2010-05-23
Nobody have the same problem with Matrox G450 and Lucid Lynx ?

---

### Post by anglican on 2010-05-24
> **mod-jkl said:**
> Nobody have the same problem with Matrox G450 and Lucid Lynx ?
I have a G550 (which should be fairly similar) and it works fine (apart from compiz - but that's another story). When you say > desktop is not displayed properly what exactly do you mean?

H

---

### Post by mod-jkl on 2010-05-24
Difficult to describe exactly, the panels are not displayed properly and are not usable (I know gnome normal looking). After a fresh install, I had a normal behaviour when adding nomodeset to the boot command at "grub time". But when I added nomodeset in the grub conf file, as it is described in the 10.04 releases notes, that did not work.

You have 10.04 working normally with a G550 without using nomodeset or something else to avoid KMS ?

---

### Post by anglican on 2010-05-25
> **mod-jkl said:**
> Difficult to describe exactly, the panels are not displayed properly and are not usable (I know gnome normal looking). After a fresh install, I had a normal behaviour when adding nomodeset to the boot command at "grub time". But when I added nomodeset in the grub conf file, as it is described in the 10.04 releases notes, that did not work.

You have 10.04 working normally with a G550 without using nomodeset or something else to avoid KMS ?
Yes (10.04 is working normally) and no, I don't use nomodeset or anything like "modeset=0" in /etc/modprobe.d/mga-kms.conf (I'm guessing that's how you'd turn it off there). I do have an xorg.conf that defines modes on the lines of (in the "Screen" section):
 ```
SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
 EndSubSection
```Which may or may not be relevent.

H

---

### Post by mod-jkl on 2010-05-25
Thanks for the information. 
In fact, I tried to deactivate KMS with nomodeset in the grub conf file (there is at the end of the post what is nentionned in the 10.04 releases notes) but I can try in /etc/modprobe.d/mga-kms.conf (when I'll re-install 10.04)

Did you create the xorg.conf by hand ?
Did you upgrade from an older ubuntu release or did a fresh install ? if you did an upgrade, maybe this file was already there..
A last thing, if you already have a 10.04 cd install, if you would boot your pc on this cd, it would be very useful to me to know if the desktop is displayed properly.
I just read on your sig that you use xubuntu, maybe something is a bit different with ubuntu, I'll boot my pc on a xubuntu cd to see if I have the same problem.


From the 10.04 releases notes

Working around bugs in the new kernel video architecture

Ubuntu 10.04 LTS enables the new kernel-mode-setting (KMS) technology by default on most common video chipsets. While this is a major step forward for the graphics architecture in Ubuntu, in some rare cases KMS will prevent your video output from working correctly, or from working at all. If you need to disable KMS, you can do so by booting with the nomodeset option. You can also save this setting so that it's applied at every boot by adding it to your grub config (for GRUB 2: edit /etc/default/grub and add nomodeset to GRUB_CMDLINE_LINUX, then run sudo update-grub; for GRUB 1: edit /boot/grub/menu.lst and add nomodeset to the line beginning with # kopt=, then run sudo update-grub). (533784, 541501)

---

### Post by mod-jkl on 2010-05-25
Also, does plymouth work on your pc ? (which I believe means that KMS is working on your graphic card)

---

### Post by mod-jkl on 2010-05-25
I boot my pc with the xubuntu installation cd and the graphic card works fine.. so there is something different with the ubuntu cd.
Still interrested to know if plymouth works on your pc.

---

### Post by anglican on 2010-05-26
> **mod-jkl said:**
> I boot my pc with the xubuntu installation cd and the graphic card works fine.. so there is something different with the ubuntu cd.
Still interrested to know if plymouth works on your pc.
Yes, I can boot fine with the xubuntu CD. I actually upgraded from an older Hardy installation which is where the xorg.conf came from. In addition to needing mode lines I also had to add in the monitor section:
```
        HorizSync       31.0 - 70.0
        VertRefresh     40.0 - 75.0
```to get anything above 800x600. Plymouth does work with my system... meaning that I see the xubuntu logo during boot up. It's very grainy (compared with what I get on my netbook) but I presume that the fact it's there means plymouth is working (I'm not very knowledgeable on plymouth). I guess that it's grainy because at that stage I'm in 800x600 as xorg.conf hasn't been consulted yet.

H

---

### Post by mod-jkl on 2010-05-26
xubuntu is working on my pc so it may be a solution. But anyway, I will stick with jaunty for the next 6 months and will see then how this pc works with lucid with all the updates..
Thanks again for your help

---

