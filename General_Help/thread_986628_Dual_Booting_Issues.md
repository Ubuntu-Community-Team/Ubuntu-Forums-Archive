---
title: "Dual Booting Issues"
date: 2008-11-18
forum: General Help
---

### Post by Azren0 on 2008-11-18
Im currently running Ubuntu 8.04 on my laptop, ive decided to dual boot it with Vista cause i require the use of some programs, Ive formatted and resized my partition using gparted so that i have my root directory as 20GB, my home directory as 80GB and my Windows i have left 80GB or so.

Ive tried many ways to get Vista to install on the 80GB but it says it cannot install on the selected file system, even though ive tried both methods of formating it to NTFS with Gparted and Vistas built in partitioning tools. (I used a live CD to format with Gparted as the drive was locked)

When running my ubuntu i have no problems, so i dont think anything went wrong during the resize, its just that Vista doesnt seem to want to install onto an NTFS file system.

Any ideas?

---

### Post by Th3Professor on 2008-11-18
Could you provide the specific steps/commands that you used?

What does fdisk -l show?

---

### Post by ranch hand on 2008-11-18
I am certainly not expert on this but I have heard that it is very difficult, if not impossible, to dual boot if you do not install the Windows OS first.

---

### Post by TeXtonyx on 2008-11-18
Since Vista will wipe out the data on the 80GB ntfs, I think you
should delete that partition first (backup if anything important)
and install Vista to the newly created unallocated space. 

I installed Vista a couple of days ago to a drive that had OpenSuse
on it. I had to delete both of Suse's partitions before it would 
install. Actually, this left the whole drive unpartitioned, so
it's possible Vista wants a clean drive. But it's really easy to
try installing Vista by deleting the 80gb partition; the empty
wine glass is half full. :-)

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)
A Howto with Ubuntu first and some variations of that theme.
Step 3 says to shrink the partition to make free space.
Deleting the existing partition is the same idea in wolf's clothing.

---

### Post by Th3Professor on 2008-11-18
You can install Vista on another primary partition (other than the 1st) if you like. You will need to set up the partitions first.

---

### Post by TeXtonyx on 2008-11-18
I gave the same advice about deleting the Windows partition first
but with XP rather than Vista, and I just got a thank you that it
worked. Remember to point the Vista installer to the free 80GB
space, for one thing you avoid the risk of overwriting Ubuntu.

---

### Post by Th3Professor on 2008-11-18
> **Th3Professor said:**
> You can install Vista on another primary partition (other than the 1st) if you like. You will need to set up the partitions first.

Also... When you set up your partitions be sure to remember which partitions you'd like to reserve for which systems for when you install the systems. You probably don't want to overwrite any systems that you wish to remain unaltered. ;)

---

### Post by Azren0 on 2008-11-19
Thanks for the advice and replys, ill give the suggestions a go and see what happens.

---

### Post by volaer on 2008-11-19
Don't forget to back up first... get all your important files first and burn them in cd so that you won't regret in any possible mistake that you will commit. Any wrong yes or no might delete the partition. When you delete a partition, it is good as deleting everything.... so meaning, always be careful in deleting  a partion... Backup first, then reformat....

---

### Post by Azren0 on 2008-11-19
I have everything backed up which i wish to keep, im still getting this error message even when following the steps in the tutorial (I found a vista one on the same site) its the exact steps i took when trying to install vista before making this post. The error is that 'Windows cannot find a suitable drive which matches the criteria for installation' or something along those lines.

I'm really trying to avoid formatting the entire drive and installing vista first then Ubuntu, but it looks like vista doesn't want to play ball, any other advice would be very helpful.

---

### Post by eder.apt-get on 2008-11-19
I agree with XP beeing installed first. Otherwise, Win will rewrite the MBR, and you gonna have to run GRUB/LILO again, using the Ubuntu CD, in order to fix it.
Check this cool step-by-step: [http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm]("http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm")

---

### Post by volaer on 2008-11-19
If you are really up to formatting, the best thing to do is to install vista first before ubuntu... otherwise, it will be harder to install vista if ubuntu has been installed.

Know that vista is more complicated with XP... especially in hardware requirements... This makes it more complicated if you installed ubuntu first before vista. 

I am using XP, then UBUNTU. but I made my UBUNTU the default BOOT OS. You can do that by right clicking my computer> properties, then look for booting. look for it is various tabs and setting buttons... I will send the exact steps, after a while. You will see a drop down menu for windows (vista/xp), then ubuntu. Just click ubuntu to make it your default Operating System. 

That should solve your dual booting problem.

Wait for the steps... i'll post it in a little while... But this is the process when your vista has been installed ok? But again, i am using xp. But, xp and vista should not have a totally different methods in solving problems and in its system setup.

---

### Post by volaer on 2008-11-19
Ok here it is: right click My COmputer>Properties> Advance Tab> Setting in Start Up Recovery> Then on the drop down menu of Dafault Operating System, click Ubuntu.

Hope this will help you. That is if you just want to still make your ubuntu your default operating system.

---

### Post by Azren0 on 2008-11-19
Ive installed vista and then ubuntu before, and i know that it works, and making ubuntu the default operating system will help. I was just hoping that it would be able to be done without formating the entire disk, but i guess its near possible, Thanks for all the tips and advice its really helped me a lot.

---

### Post by volaer on 2008-11-19
Ok... hope you will really get what you really want to happen.. God bless. :)

---

### Post by volaer on 2008-11-19
By the way, just an info, you can say thank you by clicking the menu for thank you in every post. This is  a much better way of saying thank you. heheheh... it will add up to the reputation of other users.:) God bless again.

---

### Post by ranch hand on 2008-12-11
It is also nice to go to Forum Tools and mark a thread Solved if it is and add a post telling what solved it for the next person with this problem.

Did you get it working?

---

