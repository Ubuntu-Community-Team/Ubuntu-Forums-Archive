---
title: "Reinstall Vista"
date: 2008-05-08
forum: Hardware
---

### Post by darco on 2008-05-08
I dual boot w/Vista and HH on my laptop. I resized my HDD parition and now my Vista gives me an error (cant find winload.exe). I did all I could to fix this issue but Im ok in reinstalling it. HH boots up fine. So my question is, if I re install Vista will that wack my grub? If so will Super Grub fix it? I dont want to reinstall HH.

thanks
daco

---

### Post by Chonnawonga on 2008-07-15
I know this is really old news, but I faced the same issue today, and after some struggling, figured it out, so I wanted to post the solution.

Basically, you need a working Vista install or recovery CD. Without that, you're up $#!+ creek, as far as I can tell. If you do have one, though, you can use this method to fix the winload.exe error in Vista:

[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/")

That will fix Vista, but may break your GRUB booting for Linux, which you can fix with this:

[http://ubuntuforums.org/showthread.php?t=224351&highlight=howto+install+grub]("http://ubuntuforums.org/showthread.php?t=224351&highlight=howto+install+grub")

---

### Post by niyonk on 2008-07-15
Hi, why don't you leave the windows bootloader as is..
I use a program called [EasyBCD]("http://neosmart.net/dl.php?id=1")
I always recommend it to anyone on dual-boot.
All you have to do, is point the program to where Hardy is installed and It'll do the dirty work for you...:)

If you still want to use grub, go ahead...follow the above instructions
Cheers!! :biggrin:

EDIT:: I almost forgot to say...The winload.exe error might be because when you resised your HDD, the partition tables changed and now your windows bootloader is now pointing to a wrong partition.This is why you should never resize the windows partitions from another non-M$ OS. Try the vista DVD and repair....

---

### Post by Chonnawonga on 2008-07-15
Very good points, niyonk. You're absolutely right!

Unfortunately for me, I only figured this out AFTER I had resized a Vista partition with GParted, so the above solution was necessary. I won't make that mistake again!

---

