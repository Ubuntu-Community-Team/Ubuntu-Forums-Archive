---
title: "Can't boot into Ubuntu"
date: 2008-09-28
forum: General Help
---

### Post by 357mag on 2008-09-28
Okay I got Ubuntu installed. What I did was when I got to the part of the installation program that asked me where to put the boot loader I told it to install it on the Linux drive. Here is what I entered:

/dev/sdb1

Everything appeared to be okay and the installation process completed.

My plan was to just go into the BIOS and use the BIOS to control which drive my computer boots from. So I went into it and under Hard Drive order it shows:

<ST3320620AS>
<ST3320620AS>

By default the first drive was highlighted, that is where Windows is currently installed. So I highlighted the second drive and hit Enter and saved my changes and exited.

But it just keeps booting into Windows instead of Ubuntu.

---

### Post by fooman on 2008-09-28
try highlighting it and then moving it up to the top spot.  usually done by pressing the +/- keys (or maybe up/down arrows).  then press enter.

---

### Post by anystupidname on 2008-09-28
You told the boot loader to write its code to the first partition instead of the boot sector. You could either boot to supergrubdisk using this (easiest) [http://downloads.sourceforge.net/lubi/unetbootin-supergrubdiskrev120.exe?modtime=1202438037&big_mirror=0](http://downloads.sourceforge.net/lubi/unetbootin-supergrubdiskrev120.exe?modtime=1202438037&big_mirror=0)

or try something like this:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

P.S. grub is really good at finding and booting other OSs so I always let it be my sole boot loader... (almost all my systems are dual or triple boot)

---

### Post by 357mag on 2008-09-28
Please tell me EXACTLY what to type at the part of the installation where it asks you where you want GRUB to be installed. That is what I really want.

I do not want to mingle the two operating systems. And I do not want to put GRUB to the MBR either.

If I know exactly what to type when it asks you where to install GRUB I think it will work.

By the way this is the error I'm getting:

Error 17: Cannot mount selected partition

---

### Post by RedPandaFox on 2008-09-28
> **357mag said:**
> Please tell me EXACTLY what to type at the part of the installation where it asks you where you want GRUB to be installed. That is what I really want.

I do not want to mingle the two operating systems. And I do not want to put GRUB to the MBR either.

If I know exactly what to type when it asks you where to install GRUB I think it will work.

By the way this is the error I'm getting:

Error 17: Cannot mount selected partition

The last frame before you click "install" Go to advanced

---

### Post by caljohnsmith on 2008-09-28
When you do the install again, just tell Grub to install to /dev/sdb instead of /dev/sdb1; that will put Grub in the MBR of the sdb drive.

---

### Post by anystupidname on 2008-09-29
If you want to be able to pick the drive to boot from in your BIOS you with *HAVE* to install grub to the MBR of drive 2. What is your objection to that? The only alternative would be chain loading grub from the Winblows loader...

---

