---
title: "Ubuntu and than Windows"
date: 2006-01-28
forum: Installation &amp; Upgrades
---

### Post by christooss on 2006-01-28
Hello

Imagine  that I installed Windows on my computer. I already had Ubuntu on so Windows installation eate "my" GRUB with install Windows boot loader. 

So is there NO floppy and NO LiveCD solution that I can start Ubuntu with Windows mbr.

And thing like [dd]("http://www.research.att.com/~gsf/man/man1/dd.html") for Windows?

Why I want to do this?

I just want to know if there is a posibility

BTW I found a lot of pages with Floppy and LiveCD solution
[http://www.highlandsun.com/hyc/linuxboot.html](http://www.highlandsun.com/hyc/linuxboot.html)

Bye

---

### Post by lha on 2006-01-28
[QUOTE=christooss]Hello

Imagine  that I installed Windows on my computer. I already had Ubuntu on so Windows installation eate "my" GRUB with install Windows boot loader. 

So is there NO floppy and NO LiveCD solution that I can start Ubuntu with Windows mbr.

And thing like [dd]("http://www.research.att.com/~gsf/man/man1/dd.html") for Windows?

Why I want to do this?

I just want to know if there is a posibility

BTW I found a lot of pages with Floppy and LiveCD solution
[http://www.highlandsun.com/hyc/linuxboot.html](http://www.highlandsun.com/hyc/linuxboot.html)

Bye[/QUOTE]

First you have to reinstall grub. If you don't want to overwrite mbr, install it to your Ubuntu root partitions boot sector. Then

a) Set Ubuntu's root partition as active. This will load Grub as default and you can use it to chainload Windows. This is my preferred method. (I have to admit I use Windows 98 so the option b isn't possible for me.)

**or**

b) Copy Ubuntu root partition's boot sector into a file in Windows and use NTLDR to load it when you want to use Ubuntu. See [BootPart]("http://www.winimage.com/bootpart.htm")

---

