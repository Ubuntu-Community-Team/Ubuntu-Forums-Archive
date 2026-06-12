---
title: "Grub loading stage 1.5 Grub loading, please wait..... error 21"
date: 2008-09-21
forum: General Help
---

### Post by The New Guy on 2008-09-21
Before I present my case I need to tell you my story.
My PC is a Compaq Presario SR1750NX 

My Default system is windows XP Media Center Edition which is an a 200GB SATA hard drive, ok.
Two years ago I install Ubuntu and Vista in a 40GB IDE hard drive which give me no problems because I set it as an slave hard drive and it work great for me,because sometimes I would plug it and unplug it when ever I wanted to. I would choose from Ubuntu's grub Ubuntu(obviously), XP or Vista. 
[IMG]http://thegabfather.files.wordpress.com/2008/09/grub4kt.jpg?w=500&h=277[/IMG]
[I]Note:This is not my grub I just got it from the internet. My would say 
Windows XP Media Center Edition and
Vista (Loader)[/I]
So there was not a problem there.

Well that was that, know I decided to replace it for an 80GB SATA hard drive because I wanted more space for both system (but I did not how to set the 80GB SATA hard drive as slave so I just took the pin off of it and installed it with out a pin)
Three weeks ago I installed Vista and Ubuntu 8.04 in the 80GB SATA hard drive, everything when fine in the installations so no problem there, well this time when I turned on my PC in Ubuntu's Grub would show me 
[IMG]http://apcmag.com/system/files/images/vista_ubuntu_13.article-width.jpg[/IMG]
[I]Note: Once again this is not my grub.
Between "Other Operative systems" and "Vista Longohorn (Loader)"
my grub will show "Windows NT/2000/XP" but when I click there it does not send me to the system but instead it sends me to the recovery console.[/I] 
Now I have to go to Windows Vista(Vista longhorn (Loader)) and from there choose Windows XP which is shown to me as "Earlier Windows Versions" and then Windows Media Center appears. 

Well today I unplug the 80GB SATA hard drive especting to boot my default Windows Media Center, but instead of that I got this

"Grub loading stage 1.5
Grub loading, please wait.....
Error 21"

Does some one knows how to fix this, my concern is that if in the future I decide to get an even bigger hard drive or sell my computer and keep that 80GB hard drive or just use Windows XP. it will not work because of the error above. Please if some one is so kind to help me out I would really appreciated. Thanks in advance.:(

---

### Post by Wisp558 on 2008-09-21
Why don't you just pull out your slave drive and see what happens? Or have you already done that? It just seems like something that should be tried...

---

### Post by caljohnsmith on 2008-09-21
What you describe typically happens when you install Ubuntu to some external HDD, and then Grub is installed by default to the master boot record (MBR) of the internal HDD since that is the default HDD to boot on start up. So in your case, you most likely unknowingly installed Grub to the MBR of your Windows 200 GB drive, so that when you disconnect your Ubuntu drive, you get a Grub error because Grub can no longer access its stage files or menu.lst. 

Can you set your BIOS to boot directly from your Ubuntu drive? Because if you can do that, then you can install Grub to the MBR of your Ubuntu drive by following these steps from the Live CD:
```
sudo grub
grub> find /boot/grub/stage1
```
That should return your Ubuntu partition in the form of (hdX,Y), use that:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
At some point I would assume you'll want to restore the Windows MBR to the Windows drive, which you can do with the command "fixmbr" from your Windows Install CD. Anyway, let me know how it goes or if you need more details/info.

---

### Post by The New Guy on 2008-09-21
> [PHP]Why don't you just pull out your slave drive and see what happens? Or have you already done that? It just seems like something that should be tried...[/PHP]

That is when the problem start when I tried to pull the hard drive out. Actually its not set as an slave hard drive the computer recognize it as a primary hard drive because SATA drives can not been slaves.


PLEASE IGNORE THIS REPLAY JUST READ THE ONE AT THE BOTTOM

---

### Post by The New Guy on 2008-09-21
> Why don't you just pull out your slave drive and see what happens? Or have you already done that? It just seems like something that should be tried...

That is when the problem start when I tried to pull the hard drive out. Actually its not set as an slave hard drive the computer recognize it as a primary hard drive because SATA drives can not been slaves.

To caljohnsmith

Well Im not sure if I can do that right know because I have to leave for school, but next weekend I'll try to that. Thanks
One question what is MBR?

---

### Post by Moon 111 on 2008-09-22
> **caljohnsmith said:**
> What you describe typically happens when you install Ubuntu to some external HDD, and then Grub is installed by default to the master boot record (MBR) of the internal HDD since that is the default HDD to boot on start up. So in your case, you most likely unknowingly installed Grub to the MBR of your Windows 200 GB drive, so that when you disconnect your Ubuntu drive, you get a Grub error because Grub can no longer access its stage files or menu.lst. 

Can you set your BIOS to boot directly from your Ubuntu drive? Because if you can do that, then you can install Grub to the MBR of your Ubuntu drive by following these steps from the Live CD:
```
sudo grub
grub> find /boot/grub/stage1
```
That should return your Ubuntu partition in the form of (hdX,Y), use that:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
At some point I would assume you'll want to restore the Windows MBR to the Windows drive, which you can do with the command "fixmbr" from your Windows Install CD. Anyway, let me know how it goes or if you need more details/info.

I have the same problem, but what you suggested doesn't work for me.

Using the live CD I opened the terminal and entered "sudo grub" and then "find /boot/grub/stage1" and I got an error: "Error 15: File not found".

Can you help me out?

Thanks

---

### Post by caljohnsmith on 2008-09-22
> **Moon 111 said:**
> I have the same problem, but what you suggested doesn't work for me.

Using the live CD I opened the terminal and entered "sudo grub" and then "find /boot/grub/stage1" and I got an error: "Error 15: File not found".

Can you help me out?

Thanks
Sure, but you'll need to give more info on what your situation is. In other words, how many HDDs you have, what OSes are installed on each HDD, and also please post the output of:
```
sudo fdisk -lu

```

---

