---
title: "Unable to install Ubuntu 8.04 ---Frustrated!!!"
date: 2008-10-30
forum: General Help
---

### Post by rmcellig on 2008-10-30
The specs for the computer I am using are below. I have 1GB of RAM.

[http://tinyurl.com/6kzrtp](http://tinyurl.com/6kzrtp)

I installed 8.04 from the Live CD with no problems. I installed on the entire 300GB drive. When I restart the computer I get a GRUB error 2 showing up before the computer goes to the startup menu.

When I remove the drive from this computer (1) and put it in my other PC (2), it works fine. Is there any way to get Ubuntu working fine on (1). On (2), the fan is noisy. On (1), it is quiet.

I have another HD with XP Home on it that works fine in (1), so I know that the computer is working properly with an OS.

Could it be a BIOS setting on my Dell? If so, what should I look at?

I am very frustrated!! I spent the entire day yesterday trying to get (1) working. I felt like I was back in the early 90's and not in the 21st century when it comes to working with computers.

I also tried the Ubuntu alternate CD (8.04), with the same results. 

I really need to resolve this soon. Please, I am looking for a solution and am grateful for all the help I can get.

---

### Post by Pettman on 2008-10-30
You probably got a problem with your hard drives getting erroneously ordered by the program that creates the "menu.lst"-file that grub uses to keep track of where to load kernels and such from. Try chosing the ubuntu option in the grub list and then pressing e, then select the config line that looks like hd(0,0) (can be other numbers) and change the first number to other positive integers (start with 0 if it isn't the original value). I'm not entirely sure this will work but I think it's a good start. If it doesn't, google is an excellent way of finding solutions to your ubuntu problems. Also, if you got important irreplaceable data on that harddrive, make a backup of it before attempting anything.

---

### Post by rmcellig on 2008-10-30
I don't even get as far as the grub list. I think I may know what the problem is. Could it be that my Dell needs to have the BIOS changed in order to use large disk access (lda), or that maybe my Dell does not support lda? My HD that I am using is 300GB.

---

### Post by john183 on 2008-10-30
Is the HD that has XP on it a 300GB drive also or is it the 80GB that came with the computer? To install a 300GB drive you will need to make sure that you have the newest update for your bios (A04). Just a warning though your XP install will not recognize the 300GB drive unless you have at least SP2. Hope this helps.

---

### Post by rmcellig on 2008-10-30
Thanks John,

I think I will install Ubuntu on my 80GB drive. At least I know it works with the Dell. Isn't there a way to install Ubuntu without a CD. I remember coming across a link for this but can't remember what it is.

---

### Post by john183 on 2008-10-30
you can install Ubuntu from a usb drive. You will have to have the ISO that you would use to make the cd, a usb drive (1GB min.) and UNETBOOTIN which can be found here: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) Just follow that instructions that come with UNETBOOTIN and it is very simple.

This works much faster than a cd. just make sure that you have the BIOS set up so that it will boot from the USB drive before the main HD

---

