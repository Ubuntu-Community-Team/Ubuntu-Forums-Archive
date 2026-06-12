---
title: "blank screen with mouse after log in"
date: 2008-09-24
forum: General Help
---

### Post by professormonkey on 2008-09-24
Hello

I was upgrading to Hardy from a functioning Gutsy, but when I log in, all that awaits me is a blank screen (light brown actually) with a mouse pointer that can be moved around, but clicking does not do anything.

Can you help me resolve this? (Im a newbie)

Ciao
Professor Monkey

Oh yeah..
My computer is an ancient Dell Latitude CPx

---

### Post by professormonkey on 2008-09-24
ok, the situation has worsened, now the computer won´t even make it through the Bios screen....

---

### Post by professormonkey on 2008-09-24
OK, it sometimes gets through the BIOS boot, but it only makes it half way through a Fluxbuntu boot that was supposed to be working or a windows 2000 that I have on another hard drive.

It does not matter if it is running on both memory modules or either of them seperately, so I guess this is not a memory problem.

The Bios had asked about the date, when I first starting using it today after two months.

---

### Post by snowpine on 2008-09-24
Dr. Monkey, I also have a Dell Latitude Cpx, and I used Fluxbuntu for a while, so I think I can help you out!

I'm confused, is this a new Fluxbuntu install, or was it working for a while and then it stopped?

Please give me a better description of the problem. I do not remember any "brown screens" in Fluxbuntu; it's mostly white and pastel colors. :)

---

### Post by professormonkey on 2008-09-25
Hi, thanks for your answer.

I have two partitions on this hard drive, a Fluxbuntu one that is OK and a one with Ubuntu 8.04 that I had recently updated from 7.10 which resulted in the problem I discribed in the OP.

Now there seems to be hardware problem too, as the computer sometimes wont even make it through the Bios post progress bar, or boot up from partitions that I knew that were working, such as the Fluxbuntu one or a Windows 2000 I had on a another HD. The computer just freezes completely, be it in the Bios setup, Grub, in a windows boot, Fluxbuntu boot, Live CD or Ubuntu.

This morning I was able to fully boot up the Fluxbuntu, so I restarted and tried the Ubuntu partition, I got to the log-in where I tried to log in to a XFCE session to try to update Gnome, but the computer froze. Now it doesent make it into Fluxbuntu either.

The computer seems to function shorter and shorter with each boot, but the fan did not come on, but worked last time I used the computer and should not even be needed in such a short time after being turned off for the night. I have also excluded a memory and a hard drive failure.

---

### Post by snowpine on 2008-09-25
That makes sense, thanks for clarifying :)
I am running Crunchbang on mine, which is based on 8.04.1, so perhaps this will help you out. I never had this problem with 7.10, seems to be a problem with the new version recognizing the swappable cd/floppy drive. The solution is, when you turn on the computer and Grub appears, press 'e' to edit your boot options. Go to the 2nd line, which starts with 'kernel' and add the following to the very end of the line: "all_generic_ide" (without the quotes). If that works, you can 'sudo nano /boot/grub/menu.lst' and add all_generic_ide to the end of the appropriate line.

I think that will solve your Ubuntu 8.04 freezing at bootup problem. Unfortunately, it sounds like you might be developing some kind of hardware problem as well. :( The only suggestion I can give you there is to open up the laptop (not plugged in of course) and give it a good cleaning--it's amazing what sorts of havoc dust can cause!

Good luck.

---

### Post by professormonkey on 2008-09-25
thanks again for your answer.

I have found what is causing the HW problem. If I remove the keyboard and let a big fan blow on the motherboard, the computer wont freeze. So it is  definitely a heat problem. But how to fix it, I dont know...

could something like this happen due to a bad/currupted BIOS?

---

