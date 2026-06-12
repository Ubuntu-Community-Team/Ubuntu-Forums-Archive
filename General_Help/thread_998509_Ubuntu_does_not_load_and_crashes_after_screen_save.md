---
title: "Ubuntu does not load and crashes after screen saver"
date: 2008-11-30
forum: General Help
---

### Post by bereta on 2008-11-30
Hello everyone

I have just installed Ubuntu 8.04 and then did the update to 8.10 mainly because 8.10 has support for the Intel graphics controller incorporated in my mother board (Intel GMA X4500). 

I am experiencing 2 problems, I don't know if they are related or not. 
1st, when I boot up the PC and grub starts, after the Ubuntu loading progress bar loads to full, the monitor goes into sleep (or power save mode) and computer stays inactive after that. I have to do a hard reboot to get it out of that state. This doesn't happen every time, but about once every 3 times I boot my computer.

The 2nd problem I have is after the screen saver kicks in and I move the mouse to get out of it, all I get is my desktop background with no panels or any icons. It looks like all or most of the processes shutdown along with the screen saver. The reason I say this is because I had music playing once when the screen saver came in, and when I moved the mouse, music stopped and I got a blank screen.

Does anyone know what may cause this? My computer is made up of a Gigabyte EG43M-S2H main board and an Intel core 2 duo E8400 processor, 2GB of ram, 500GB SATA2 Seagate HDD, and a Sony DVD writer.

Thanks in advance for any help or suggestions

---

### Post by spiderbatdad on 2008-11-30
Unfortunately, a clean install is generally preferred to a dist-upgrade. That particular computer may require some boot options to get all the hardware working properly...like "acpi=off" possibly. Google ubuntu plus your mobo model and see what you come up with.

run the command ```
dmesg > ~/Desktop/dmesg.txt
```then read through that file for clues. You can create an archive of the file by right clicking on it, and you can upload the archive here with the manage attachment tool below. Or paste it to ubuntu pastebin and post a link here. Please dont make a post including all the text from dmesg.

---

### Post by bereta on 2008-12-01
Thanks for the reply spiderbatdad

Here is the link for the dmesg output: [http://pastebin.ubuntu.com/78612/](http://pastebin.ubuntu.com/78612/)
I'm not realy shure what to look for.

so you think it might be easyer to download and install the 8.10 iso. That is not such a big deal for me now because i dont realy have any apps installed or done any costumising yet, but what about when the next version comes out, it may be some what complicated .....

I did't find anything significant on google when I searched my motherboard and ubuntu.

Thanks

---

### Post by spiderbatdad on 2008-12-01
Nothing jumps out as an obvious problem to me. I always do a clean install with a new release. Back up data I want to save. 
It is often desirable to create a separate /home partition. Or to try new releases on a separate partition, and moving files before expanding the space into the old release.

I think you might try noapic nolapic to combat the boot issue. Do you know how to edit menu.lst to apply these changes? Better yet, try a one time boot from the grub menu by pressing 'e' to edit the kernel. Then use the arrow key and move to the line beginning with the word kernel, then press 'e' again. Go to the end of the line. Delete quiet splash. Type noapic nolapic, hit enter, press b.

---

### Post by bereta on 2008-12-02
Thanks, I will try that as soon as I am back at my computer, but what would be the benefits or dissadvantages of "noapic nolapic"?

---

### Post by bereta on 2008-12-08
Hi 

Sorry for the late reply, I have tryed the noapic nolapic and the computer would not boot into the GUI, it wouldet eaven boot to a shell. I gave up and downloaded and installed the 8.10 iso and I don't seem to be haveing those problems. Its been 2 days since I reinstalled, I will let you know if I get any more odd problems.

Thanks for all your help

---

