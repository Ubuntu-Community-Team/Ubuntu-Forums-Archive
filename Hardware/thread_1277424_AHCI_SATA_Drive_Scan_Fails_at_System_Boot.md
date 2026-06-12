---
title: "AHCI SATA Drive Scan Fails at System Boot"
date: 2009-09-28
forum: Hardware
---

### Post by SkittleLinux18 on 2009-09-28
Yesterday I was on my Windows computer doing homework. Once Football came on, I hit the Standby button on my keyboard and walked out of my room. Came back at halftime to discover that my system never went into Standby. I turned on my monitor and saw a bunch of code repeating. I don't remember it all, but it was something to this effect

> Super Block not compatible with current BIOS
scanning for **insert system file here**.... not found
scanning for floppy drive... not found
scanning for cdrom1... not found

So I hit the restart button on my tower. When it restarted, I was brought back to the same screen. So I unplugged the power cord from my computer and counted to 10. I plugged it back in and this time I got my mobo logo screen and the system appeared to start up fine, until I got to the SATA drive scanning screen. When my computer would scan for my SATA hard drive, it would idle for several minutes, during which a series of periods (".") would show up until eventually I get a message that says

> WARNING! - Something wrong with your hardware!

I have troubleshooted a number of things so far:
1) I took my SATA Hard Drive out of my computer and plugged it into my Linux computer and the system booted fine! I used the same SATA cord, so I know both the drive and the cord ARE WORKING!
2) I tested the power cord from the power supply that runs to my HD and it is working just fine. 
3) I plugged the HD back into my Windows computer (the original one it was in when I started having this problem) and  I ran GParted. When the GUI came on, I could not see any drives and there was a message at the bottom of the window saying that no devices could be found. This was no surprise to me because I watched the verbose mode as GParted booted and it gave error messages when it tried scanning for my hard drive. 
4) I have also tried plugging it into the other SATA ports on my motherboard.
5) I tried flashing the mobo BIOS. The flash worked just fine (or at least it appeared so), but the HD is still not being found on the system boot scan.

Bottom line, I know the hard drive is fine because it worked in my Linux computer. So I am thinking it has to be the motherboard. But before I go out and buy a new Mobo and CPU (and possibly new RAM), I wanted to quickly jump on here and post something in case anybody knows something I'm missing.

So yeah, what does everyone think?

Thanks!

---

