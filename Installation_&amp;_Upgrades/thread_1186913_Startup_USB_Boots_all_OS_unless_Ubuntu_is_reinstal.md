---
title: "Startup USB Boots all OS unless Ubuntu is reinstalled"
date: 2009-06-14
forum: Installation &amp; Upgrades
---

### Post by Dtfa on 2009-06-14
System: Athalon X2 
**[SIZE=2]Problem's background:[/SIZE]**
-
Originally, I had planned to make a grub boot floppy. However, this failed too many times to count. The Ubuntu community doc that I followed appears below.
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

I was able to successfully create a startup (Rescue USB) by combing the previous Ubuntu documentation with this link: [Super grub disk boot usb]("http://www.supergrubdisk.org/wiki/SGD_Howto_make?phpMyAdmin=4d5aa646470e3977a158303759c2efde#How_to_make_a_Super_Grub_Disk_USB.") Now, onto the problem
>
**[SIZE=2]The problem:[/SIZE]**
-
If I create a"Grub boot USB Flashdrive" under the condition_ *that Ubuntu was installed last **(Last meaning Ubuntu is installed after the installation of Vista & the other two Linux distros***_) the created &quot;startup USB&quot; will boot every operating system on the SATA disk.
>
However, if for whatever reason, I am forced to reinstall Ubuntu. Then the subsequently created "Grub boot USB Flashdrive" will only boot Ubuntu.
>
Could someone please tell me what I am doing wrong? Google & 10 pages of this forums post did not help me.
I even tried the village witchdoctor's solution & it also failed to yield success.
Thanks
signed, baffled

---

### Post by Dtfa on 2009-06-18
Bump
Perhaps no one saw this. However, if someone sees this post, help would be greatly appreciated.
Grazi

---

### Post by Dtfa on 2009-06-21
Bump
>
It's been a week, yet no one has offered to help.
Any help would be appreciated! :)
Thanks in advance

---

### Post by Dtfa on 2009-07-04
**I corrected some gross typing errors in my original post. **
>
**[COLOR=Lime]Perhaps, someone can help me now? [/COLOR]**
>
Basically, I just want to create a "grub boot USB flashdrive" that will boot all installed operating systems." If I install Ubuntu last, creating "grub boot USB flashdrive" that will boot multiple Linux distros is easy; However, if Ubuntu is installed first, then it is impossible to use Ubuntu to create a "grub boot USB flashdrive" that will boot other Linux Distros. Super Grub USB does not work.
>
Thanks

---

### Post by earthpigg on 2009-07-04
are you aware of the *super grub disk* and *ultimate boot cd* projects?

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

super grub has a download specifically intended to be used with a usb thumb drive, and it also has a very nice wiki.

---

### Post by Dtfa on 2009-07-05
> **earthpigg said:**
> are you aware of the *super grub disk* and *ultimate boot cd* projects?

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

super grub has a download specifically intended to be used with a usb thumb drive, and it also has a very nice wiki.

[SIZE=4]**[COLOR=Red]Not solved but found work-around[/COLOR]**[/SIZE]

Thanks for responding! :) finally, someone responded although my typing errors probably did not help.
Anyway, yes I am familiar with them.
*Supergrub disk CD* worked fine on the older machine, and it worked almost as well on my newer machine. However,  scratches, destroy CDs while USB seems scratch and even washing machines resistant, so I just want the security of USB. "Supergrubdisk USB" does not work for me, period; it just hangs at the initial splash-screen.
>
As for the "Ultimate Boot Cd," I tested it & found the CD to be immensely complicated.
I just got stuck in a loop always returning unwittingly to the starting point. 
>
I now have a working Linux distribution (Slax) installed on a flashdrive. Installing it was far simpler than using the "Ultimate Boot CD" Now that I have Slax, should I ever need to: "dd" my MBR back to the computer, run "Testdisk," gparted, a clam virus scan, a "windows password cracker" (I run Vista too)  or log onto the internet (while running a firewall) for more information, I am covered. Too bad Ubuntu does not make something like this, for it's a great tool.
>
Hope this helps someone, and thanks for your response despite the fact that it was 3 weeks late. Just kidding :D

---

