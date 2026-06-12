---
title: "New Laptop giving more trouble than I could ever have imagined."
date: 2007-07-07
forum: Hardware &amp; Laptops
---

### Post by NickArgyle on 2007-07-07
This morning I bought a new HP Paviion dv9000 with the following:

AMD Turion 24 x2
Nvidia Geforce go 6100 
120 gig hd
2 gig Ram 
M$ Vista
Lightscribe dvd+-RW

When I got the PC home I went to install Ubuntu. I put a 32 bit feisty installation cd in and cliced start/install. It seemed to boot okay off of the cd, messed up when it tried to initialize x. I never got to the login screen, just a very strange looking grey screen (And not the typical grey screen you get when x messes up, but a very ugly one.) I assumed this problem was because I was trying to boot the 32 bit version on a 64 bit processor, so I downloaded the 64 bit iso and burned it, but when I ran he cd I got the same result. I checked the cd for defects and got nothing. I ran it in the safe graphics mode and also got the same result. In this screen the commands to enter the console would not work, all I could do was reboot the system.

At this point I assumed this must have been caused by the nvidia drivers not being installed, and since I couldn't enter the command line, maybe I should try using the text based installer to get the program working. So I downloaded and burned the iso for the 64 bit text based installer. I installed completely text based, and then when I tried to boot, the loading bar would freeze half-way and lock up completely. So I ran it in safe graphics mode so I could see what was happenng, once booted I would get errors with loading the hardware profile, or something about fonts depending on which of the many times I tried restarting it. 

At this point I decided I would reinstall ubuntu again except this time completely command line based as maybe if gdm and stuff werent installed it would work and I could narrow it down later while manually downloading the programs. I did this but the comand line system also pauses at loading hardware profile.

Now I have no idea what to do, I have tried all posible cd installations. Is my hardware incompatible? What should I do?????

---

### Post by strabes on 2007-07-07
Remove the "splash" option from the kernel boot line in grub so you can see what it locks up on. Most likely it's when it's configuring some hardware.

---

### Post by hardyn on 2007-07-07
my bet is its going to the be the 6100, you might have install using a vesa video mode, until you can get the restricted package driver in there.

---

### Post by NickArgyle on 2007-07-07
Well, apparently several people have had trouble with this notebook model and ubuntu, at least I reas so on the sabayan forum. I decided to try sabayan just too see if it would work, and it did, so I know the hardware is not corrupted. I am using sabayan right now but am not quite liking the switch enough to keep the OS. Gentoo and sabayan are simply too far removed from the ubuntu that I am used too. I am going to test debian and see if the main problem might be the unsopported graphics card.

---

### Post by l-fever on 2007-07-07
Did you read through this thread? Don't give up!

[http://ubuntuforums.org/showthread.php?t=431815&highlight=dv9000]("http://ubuntuforums.org/showthread.php?t=431815&highlight=dv9000")

---

### Post by NickArgyle on 2007-07-22
Finally got ubuntu working (well linux mint to be precise but it is still ubuntu.) Last week I had given up on ubuntu and my laptop and decided, after about five other distros, that I would stick with mepis as it works. Other distros that worked included sabayon, and pclos. However I was not completely comforatable with mepis. It is a great Os and I could have used it but it just wasnt the same (mainly KDE :mad:,) the same goes with Sabayon and pclos just didnt get along with me. I decided to try mint, however it did the same as ubuntu, but I was able to hack around and get Mint running. This will also work with ubuntu, however you will need to install with the text based cd if you were having the problem I was.

How I got it working:
I ran the mint live cd with the noapic boot option. (this allowed X to run off the cd.)
I installed mint, however when I tried to add the boot code in grub my computer would restart.
So all I had to do was boot the live cd again and access the HD that I just installed mint on to. I had to edit the menu.lst file and add noapic to the correct line (the end of the kernal line) and then edit the xorg.conf and change the driver from nv to vesa.

If you have these problems and want ubuntu instead of mint, then in my experience you must install ubuntu from the text based cd, then use a live cd from a different OS (mint, sabayon pclos etc.) to manually edit the ubuntu menu.lst and xorg.conf files on your harddrive.

I missed ubuntu :)

---

### Post by Skidpad on 2007-07-22
A great work-around Nick, and a great story.  I enjoy reading these "new laptop" threads, as I've been drooling for quite some time over the latest hardware; these types of threads will be beneficial when I decide to purchase.

Thanks for sharing.  :)

---

