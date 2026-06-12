---
title: "System doesn't Boot after Crash"
date: 2009-01-31
forum: Hardware
---

### Post by Grogger on 2009-01-31
I was dual booting XP pro and Ubuntu Intrepid on my desktop. I picked up some virus or root kit in windows but was still able to boot into windows and do stuff. It was just a bit slow once the virus fired up.

I tried using an ubuntu intrepid livecd to salvage my files without picking up the virus. However twice the computer locked up and I couldn't do anything, so I did a hard shutdown. It seemed like the USB drivers might have been crashing when I was trying to plugin a USB hard drive or flash drive. Anyway after the second crash and hard shutdown my computer won't reboot. It seems like it gets power and the fans come on and hard drives spin, but no graphics show on my screen. It's almost like the computer comes back on to the stuck state from when the livecd crashed but without graphics.

I tried unplugging the computer from the socket for a while. That didn't help. I also reset the CMOS on the Intel motherboard. That didn't help either.

Any ideas on what to do next? It's just weird that such a basic thing like the BIOS posting isn't working. Unless the BIOS posts and I just don't get graphics on it because those are messed up.

*Hardware: Motherboard Intel D915GEVL, Intel P4 3.0Ghz 530J Processor, Seagate SATA 160GB HardDrive, Plextor DVD Burner, Corsair RAM 1GB, Antec Sonata I Case, Antec Earthwatts 380W Powersupply.  Corsair Flash Voyager 1GB Flash Drive, Seagate FreeAgent Desktop External HD.  Dualbooting Windows XP Pro and Ubuntu Intrepid 8.10 *

---

### Post by Piro24 on 2009-01-31
Hmm, though rare, this "virus" could have been one of the particularly malacious ones that messes up your RAM.

Try plugging in other RAM sticks, and make sure everything is properly plugged in. That is indeed one odd problem you've got there.

---

### Post by Grogger on 2009-02-07
I guess I did have a problem with my graphics card acting up. After I unplugged it the bios posted when I used my onboard intel graphics.

Now I just have to figure out how to get NTSF reliable writing to work on the 7.04 Feisty I have installed on it, so I can salvage my windows xp files by writing to my ntfs external hard drive. Probably the updates will at least help.

Thanks.

---

