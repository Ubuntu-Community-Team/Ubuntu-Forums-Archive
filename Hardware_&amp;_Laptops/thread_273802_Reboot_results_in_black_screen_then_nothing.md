---
title: "Reboot results in black screen then nothing"
date: 2006-10-08
forum: Hardware &amp; Laptops
---

### Post by prophet on 2006-10-08
For some reason my laptop will not reboot. Happens right after the install (graphical or text). Installer says everything installed sucessfully then it tries to reboot but it never does. I tried installing with kubuntu desktop cd and kubuntu alternative install cd. Both had same results. It seems to go through reboot process just fine until it gets to "will now reboot" then my screen goes black but it never reboots nor shutdown. Shutdown works for me so that seems wierd. Also I've tried the lapic acpi=off and lapic acpi=force options which didn't solve the problem. I also tried the TerminateServer=true option in /etc/kde3/kdm/kdmrc. Tried combination of the 3 options and still I end up with the black screen (for long time). HAs anyone resolved this or come up with a different workaround? 

Sorry for reposting this but there were so many people posting in the geneal support forum that I didn't think this got much attention. Seems to me that breezy was more stable than dapper too.

---

### Post by Mazen on 2006-10-08
This happened to me and i kept installing and re-installing!...the last time i used the Ubuntu Live CD and booted from it and installed it from "inside" Ubuntu,
try deleting ur partitions and remaking them so that if there's any problem with the xorg.conf file....(which i found so hard to edit) u'll have a new one with , hopefully, no problems.

---

### Post by prophet on 2006-10-08
Forgot to say I have the averatec 3150 with s3 prosavageddr video card. Motherboard is a VIA VT8235 KN266.

---

### Post by prophet on 2006-10-08
Are yu saying that you had this problem but it is now fixed? and all you did was remake the partition? Maybe my problem is different because I already did several installs and everytime I told the installer to format the partitions. However, the problem still persists. Thanks though.

---

### Post by Mazen on 2006-10-08
well i have dual-boot with WinXP so i formated the partitions using Partitions Magic and because of that you loose ur grub boot screen so you're then obliged to boot from the cd and remake the partitions because they don't exist anymore so it worked for me.

---

### Post by prophet on 2006-10-08
Yeah, that didn't work for me because I also dual boot with winxp. At beginning, I used acronis disk director to partition harddrive to leave space for Linux. Then, I formatted the entire drive including the partition with winxp. Then, installed xp, then installed linux on the free partition. However, after the successful install by kubuntu dapper, the installer restarted my laptop unsuccessfully --> After waiting a long time, I had to press the power button to turn off then start computer back up again. My kubuntu install has never had a successful reboot since. Turn Off Computer works though which really seems odd to me.

---

### Post by Mazen on 2006-10-08
mmm..pretty confusing because i had almost the same thing i guess, i had alot of "edit xorg to fix your resolution" but didn't work it only messed things up. so i went to formation, what i did, i dunno if u tried it, is have free unallocated space on my harddrive so that the linux installer makes them into a EXT and a SWAP drive because when i formated a EXT partition from winxp it didn't work i think so i just let the installer do it's thing, just give it the free space so you don't loose any win data,
hope im helping not making it more complicated!! lol
good luck

---

### Post by prophet on 2006-10-08
I appreciate you trying to help very much. Also, that is logically exactly the same as what I did. I didn't format the drive for linux, though I did format it beforehand just to clean the partition (I know this was an unnecessary step but I like starting things clean). Anyway, then I told the installer to split the partition I allocated -> 1 for swap and the other for root and told it to format root to ext3. So pretty sure I didn't mess up the xorg config, although I don't know how to modify it to maybe workaround this problem if that is the cause.

---

### Post by Pr1m3 on 2006-10-12
Hm. Guess this is a common problem then. I basically somewhat have the same issue. I've installed Ubuntu on my laptop. I did a mem test, ran off dvd for awhile. Then did a full install and partioned the entire drive for Ubuntu and got rid of Windars. Anytime I restar or boot down and try to come back up, I get a black screen. Eventually after messin with it, I figured out, if I unpluged the laptop from power and plugged back in, it'd boot right up. While it's running, it works great no problems. Just the issue of the black screen.

---

### Post by prophet on 2006-10-15
actually, mine doesn't have the problem on boot. It also does the shutdown correctly. Only problem I have is the reboot. Which stops at a black screen then nothing happens. After looking at your post though, seems to me that the power management software has a bug. Does anyone know how to prevent it from installing during the install? I ask this because my reboot problem starts to happen right after the complete installation and the installer just can't do a reboot on my system.

---

