---
title: "DVD-RW and DVD-ROM"
date: 2006-09-14
forum: Hardware &amp; Laptops
---

### Post by Marksman Ken on 2006-09-14
I have a DVD-RW and DVD-ROM but when I insert a CD to read it eg music.
All it does is crash the program trying to read the CD. It also seems to turn off my drive so I cant retrive the disc (until restart), and also it pretty much makes Ubuntu crash if I do anything else like try to log out or switch it off.

On start up after this happening my motherboard cant seem to find my second hard drive (This is the one with Linux on it), this causes Ubuntu to fail to boot and give Error 21 which I have researched to mean what I thought, cant detect hard drive.

If I then restart again my motherboard comes up with a message saying "Overclocking Failed!" Even though no settings have been changed. It asks me to either go to default settings or change them myself (I dont bother changing any settings).

After one more restart everything will be back to normal.

I have only had Linux for a day so im very new, but this seems very puzzling and Im thinking its not going to be a straight forward anwser.

I need my DVD-ROM to get my internet :( (Wifi USB drivers)

Info:
Ubuntu: Dapper - I have very little else installed
AMD Dual Core 4800+ / 2048 MB RAM / ATi X1900XT x2 in crossfire / X-Fi Xtreme Music sound card / 2X Maxtor 300 Gb Hard Drives >>> 3DMark'06 = 8500+ (Stock speeds) DVD-R)M and DVD-RW are both Sony
Motherboard Asus MVP deluxe
Niot sure what else you might need.

PS. It has taken me alot of research and work to get Linux install, boot and run at all this far so any help would be amazing because this is starting to get out of my league :(

---

### Post by BLTicklemonster on 2006-09-14
My best guess would be to figure out which program it is that is coming up to play the music, then go to synaptic package manager, look program up, and mark it for complete removal, remove it, reboot, then go back and install it again. Do you know how to get to synaptic?

---

### Post by Marksman Ken on 2006-09-14
I think I know what that is.
I try to run my music CD with rhythmbox but i think other CD's do the same thing, like ones containing general stuff (not like I have alot of CDs to test it with anyway lol).

Thanks for the fast reply :D

---

### Post by BLTicklemonster on 2006-09-14
Um... I hope someone with a better answer will come along soon, but I wonder if there are some codecs you need? The reason your tray won't pop out is because the program is hung up (you have tried right clicking on the cd's icon on your desktop and clicking on "eject", I suppose?). If all else fails, you can use the old straightened out gem clip trick. All cdroms have a teeny hole under the tray, and you can carefully push a straightened out paper (gem) clip in there, and make the tray pop out until you need to reboot.

---

### Post by Marksman Ken on 2006-09-14
Yeah tried that.
I have managed to get most CDs/DVDs to work now but some still crash it. I think its the ones that have Mpeg music videos on them, not sure why this would crash a music player though :D

---

### Post by BLTicklemonster on 2006-09-14
Ah. Do you have the stuff that makes mpeg music videos work installed? Try getting automatix, and I can't suggest that you install the illegal codecs and media player things and all that I was going to suggest you install because they are illegal or something. So I can't. Or have you already?


(search for automatix on google, and go to the home page and download it there, install it and run it)

---

### Post by Marksman Ken on 2006-09-15
No, all I have installed is Ubuntu from the disk I have.
Im not sure what illeagal codecs you are talking about but I dought I have any, havent even managed to get the internet running yet :D
But just for future reference which codecs are illeagal?

I've noticed I need the internet to install everything, so I cant just transfer it from windows can I (After I download it with windows)? 

Thanks for the help, it was very useful. I think I will have to try and sort out my internet first with the looks of things.

BTW everything didnt mess up when I tried to load the CD in rhythmbox, I think it wouldnt mount (no icon on desktop) altogether which is why i found it strange, Im guessing this was down to Ubuntu rather than the music player.

---

### Post by cracker on 2006-09-16
The "Overclocking Failed!" message leads me to believe this isn't just a software problem, but a problem with the motherboard or disk controller, or even a drive or cable. Have you tried booting with only one of the drives connected, or connected on the other IDE channel, to see if this fixes the problem? Also, check the condition of the discs you are using, and make sure it's not something silly like a loose cable inside. I recently had a problem with a pair of optical drives (a DVD-ROM and CD-RW) failing proper detection by the motherboard. For some reason, each drive worked alone, but messed up when both were connected, even when master/slave was set manually. I ended up buying a pair of BenQ DVD+-RW drives.

---

### Post by Marksman Ken on 2006-09-16
I think the overclock failed message must have been a one off, even after all the times its crashed it seems to boot ok after restart now, strange.........

I have been testing some more and it seems that if I dont insert a DVD in one of the drives, plain music CD's will Mount for 2 seconds then unmount and crash my drive. If I insert a DVD first, then a CD (even after removing the DVD) things are fine. Completely puzzled @_@

But if there where a problem with the drives being connected properly, wouldnt it make a difference in windows too. I've never had a single problem with it reading the CD's at all.

---

