---
title: "kernel 3.7.0-7-generic : no dvd read"
date: 2013-01-06
forum: Hardware
---

### Post by didli on 2013-01-06
Hi to u all !
I can't read any DVD since I switch to kernel 3.7.0-7-generic. I'm not talking about DVD video, it seems I can't read any DVD *at all*. No matter blank, data dvd, etc.
Before reverting back to main 3.5 kernel (i'm not even sure i didn't have the problem before 3.7.0-7... + i have an awful list of compil to redo if i revert back), I wish to know if others are experiencing same problems or if you heard about a possible fix.
Here's the DVD writer I'm using :
sudo lshw -short -numeric :
```
/0/4/0.0.0        /dev/cdrom      disk        DVD+-RW GSA-H31L
     *-scsi:1
          identifiant matériel: 4
          nom logique: scsi1
          fonctionnalités: emulated
        *-cdrom
             description: DVD writer
             produit: DVD+-RW GSA-H31L
             fabriquant: HL-DT-ST
             identifiant matériel: 0.0.0
             information bus: scsi@1:0.0.0
             nom logique: /dev/sr0
             version: 1.05
             numéro de série: [
             fonctionnalités: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=nodisc
```
Strange thing is that i can read cd & cdroms just fine, which doesn't make any sense for me. Did i miss a package or something ??
Thank you for your help !

---

### Post by Pjotr123 on 2013-01-06
> **didli said:**
> Hi to u all !
I can't read any DVD since I switch to kernel 3.7.0-7-generic. 

Expect frequent breakage and many unsolvable bugs, when using a kernel that's not part of a stable Ubuntu release. Why on earth are you using this kernel? :shock:

---

### Post by didli on 2013-01-06
Because of xorg-edgers ppa, which comes with such kernel plus I was trying to revive some old DVB-T usb, which was known to work better with it (and it was a little true, but not that great).
So in your opinion, i need to revert back ... true ?

---

### Post by Pjotr123 on 2013-01-06
Yes.... I advise to wait for 13.04 Raring Ringtail, which will be released in April.

In a sense, the kernel *is* the operating system. The rest is "just" a layer around it. This layer needs to be finely tuned and adjusted to the kernel, otherwise all kinds of things will go horribly wrong. C'est la vie...

If you have a lot of "panache" and fear no bugs, you might go for the alpha 2 release of Raring, which will be released in a month:
[https://wiki.ubuntu.com/RaringRingtail/ReleaseSchedule](https://wiki.ubuntu.com/RaringRingtail/ReleaseSchedule)

But if you prefer to act as your signature says, you'll wait until April.

En tout cas: bonne chance! :)

---

### Post by didli on 2013-01-06
Eh bien puisque c'est comme ça ... c'est parti !
Downgrading in progress, let's get back to the real thing. I'm not as audacious as I may think, so I will wait and try Raring when it's gonna be available. 
Merci pour ces précieux conseils !
Thanks for your help and your nice (french) words !

---

### Post by didli on 2013-01-06
Damned !
I'm screwed ...
Revert back to kernel 3.5 changes nothing, problem still arises plus I have searched for a firmware (hoping it could help) with no avail.

---

