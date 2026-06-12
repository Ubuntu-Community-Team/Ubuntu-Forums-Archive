---
title: "Best way to upgrade"
date: 2009-07-14
forum: Installation &amp; Upgrades
---

### Post by stjoenewt on 2009-07-14
I installed Feisty Fox a few years back and, as it has done very well, have not been good about installing upgrades.    :(

I now wish to catch up, due to having some new hardware not supported by Feisty. (Web Cam)

I read and attempted to perform the steps called out in both the EOLUpgrade page and bug report 264181, however ran into problems.   :confused:

I then googled for information and after reading threads here last night, I realized where I had gone wrong.  I basically tried to start in the middle of the instructions, where the 7.04 to 7.10 section starts, without realizing there were some steps at the beginning which caused the failure.  I had not changed the sources.list entries to refer to old-releases, so now I think I know how to avoid my errors.

However, in reading posts, I thought I understood that I may have another    option to consider.   :roll:

My  hard drive is partitioned as follows;

/dev/sda1      ntfs           /media/sda1     39.06 Gib
/dev/sda2      ext2           /               48.83 GiB
/dev/sda4      extended                       273.93 GiB     
-   /dev/sda5      linux-swap                 1.95 GiB
-   /dev/sda6      ext2       /home           125.00 GiB
-   /dev/sda7      ext2       /usr            92.83 Gib
-   /dev/sda8      ext2       /var            43.95 GiB
-   /dev/sda9      ext2       /tmp            12.20 GiB
/dev/sda3      ntfs           /media/sda3     8.79 Gib 

The first and last partitions contain Windoze and distributed software that came with the machine.  All the others are used by Linux.

With /home and /var in separate partitions, I believe I could do a fresh install without loosing many user settings.   I have installed a few third-party software packages, and I assume I would have to re-install those if I chose this option.

Is this a correct assessment?   What would be your advise, upgrade 7.04 to 7.10 to 8.04 to 8.10 or fresh install?   How would I identify all the software I have installed that are not in the Ubuntu repo's?   What other settings would I risk loosing with a fresh install?

Thanks in advance for your opinions and assistance.

---

### Post by LepeKaname on 2009-07-14
> What would be your advise, upgrade 7.04 to 7.10 to 8.04 to 8.10 or fresh install?

I could recommend to go with 8.04 or 8.10 (I don't recommend to go with 9.04 yet).

Normally I used to upgrade over the same installation (In general there is no problem). Now, I prefer to do a fresh install everytime.

If you go with a fresh install, do it in another partition. So you will be able to boot back to 7.04 any moment (using grub), so you don't loose anything. Just be sure in which partition you are installing it (its easy to make a mistake and erase other important partition).

Then once everything is working property in the new installation. Mount your 7.04 partition and move your files. Some of the config files in your home may not work properly with the new versions, so you can try one by one. For example, firefox. rename ~/.mozilla to anything else and copy the old ~/.mozilla folder in your home. Run Firefox. If it works properly, you will be able to use your old settings. If not, you may need to export it manually and use the new ~/.mozilla settings.

The extra software you installed, you will need to install it again, as many common libraries changed.

Until you have everything up and running, you can get rid of your 7.04 installation and save some space...

Good luck!

---

### Post by stjoenewt on 2009-07-15
LepeKaname

Thanks for you response.

Why did you change from upgrading to fresh installs? It seems the fresh install is more work. Do the upgrades not properly convert existing settings or applications.

---

### Post by running_rabbit07 on 2009-07-15
I am using 9.04 and it is working great but next time I reinstall which will be soon so I can add Swap and /Home partitions, I am gonna go with 8.04 LTS.

I think you would be good with 8.04 too that way you are supported longer without upgrading until 2011.

---

### Post by lensman3 on 2009-07-15
I just upgraded and formatted my /, /boot, /usr, /tmp, /opt, swap, and /var.  I didn't format my /home, /u1 (another user partition).  I shouldn't have formatted /opt, it has a lot of packages I have installed, because I had to a restore.  I formatted everything ext4 except /boot, which wasn't allowed.

umount all drives that have windows, etc. on them so that the install won't screw them up.  I had to re-setup my users in /home.  I unfortunately years ago had OS-X machine on the network and user 500 was already in use by it.  I had to take another number, so I have to modify the install setup non-root user to user 502.  

I would suggest that you reformat all partitions except your data partitions.  Unplug drives from the motherboard or USB during the install.

Hope this helps a little.

---

### Post by stjoenewt on 2009-07-16
Running_rabbit07 & Lensman3,

Thanks for the replies.

I sounds like consensus is to do a fresh install.  I will want to think about this for a bit, as I had not really considered this option before.

I like the idea assuming I can keep the programs I have installed and especially the user settings.   

Am I understanding that if I do not reformat /home, and redefine the same user ID's after the clean install, then the contents of /home will be used by the OS for the newly defined user ID's?

---

### Post by stjoenewt on 2009-07-16
lensman3

Sorry for the second post, but after re-reading your post, I had another question.

I don't completely understand how Linux utilizes the directories.   Which partitions would be my data partitions?   /usr & /var?

Thanks for your assistance.

---

### Post by LepeKaname on 2009-07-17
> Why did you change from upgrading to fresh installs?

The main reason is because after an upgrade, some things may stop working as they were working. If you do a fresh install as I wrote before, you can mount your old installation in for example: /home/user/feisty. Then you don't need to setup everything in one time. You can start adding packages as you need them and if you want to "recover" something of your old installation it is very easy. Also this is the safest way as you never loose your previous install. And as I said, once you are fine, you can get rid of that old installation (actually right now I have 2 previous installation).

In general, Ubuntu will use your main partition in / (root dir) then the rest will be located inside /media, for example: /media/sda2 

Run this command: "**df**" it will show all your usage and drives information, which includes your "physical" location, like:
```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb1             30945600   5563060  23810584  19% /
/dev/sdc4             60096676  45217840  11826088  80% /media/disk1
```
Which means that /media/disk1 is really /dev/sdc4. So, if for example you want to install ubuntu in that specific partition, write down "sdc4" and its size: 60096676 (60GB in this case) and during the installation choose that one. Be sure that drive is empty and doesn't have any important information. That drive will become "/" and then you can mount your /dev/sdb1 (in this example) in /home/user/feisty (as I explained before).

I hope I explained myself...

---

### Post by raymondh on 2009-07-17
Doing a netwrok upgrade from feisty to jaunty (including ensuring that each version is updated prior to moving to the next) does take time.  With a /home that you have, I would just do a fresh install.

Did you check the livecD (of whatever version you prefer to end up with) and see how it handled with your system ..... ie. wifi, keyboard, graphics, etc, etc.?

You may also consider this for those apps/repos that you want to import.

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

Good luck.

---

### Post by stjoenewt on 2009-07-17
LepeKaname & Raymondhenson,

Thanks for your advise.   It's immensely helpful to get advise from those with more experience using Linux.

I did burn Live CD's of both 8.04 and 9.04 and will try them out to see which  would work better for me.   I'm very tempted to go with 9.04 as my PC is simply a desktop workstation, not a server.   But regardless, I need to get on a supported release again.

Thanks again.

---

### Post by pd71sat on 2009-07-17
> **stjoenewt said:**
> LepeKaname & Raymondhenson,

Thanks for your advise.   It's immensely helpful to get advise from those with more experience using Linux.

I did burn Live CD's of both 8.04 and 9.04 and will try them out to see which  would work better for me.   I'm very tempted to go with 9.04 as my PC is simply a desktop workstation, not a server.   But regardless, I need to get on a supported release again.

Thanks again.

**stjoenewt**, let me give the benefit on my experience today.

On a Fujitsu Laptop with integrated ATI graphics, Atheros wifi, 
and AMD X64 dual processor I had Ubuntu Hardy 8.04.1 LTS 
installed. In the past I had gone the update, then dist upgrade
route to advance to newer release of the product. I started 
at 6.06 LTS dapper drake. Each time it was hell after the 
upgrade was completed. I had to battle with proprietary ATI 
graphics re-installs to get direct graphics rendering active. If 
I did not do that the mesa drivers that were setup with the 
system were slow and the laptop underperformed. From 6.06 to 
7.04 I battled with wifi using WPA key protection. Then Network 
Manager applet was stabilized and from 7.04 to 8.04 I was ok and 
never had a problem again with that. There were also keyring 
issues that meant you had to enter password every time to log 
into your Network i.e. if your laptop was password protected, etc.

Then I used "**wine**" to run some Windows programs like Lotus
Smartsuite, etc. Each upgrade trashed "**wine**" and it had
to be re-installed as it seems to be distribution sensitive.

I wrote all that to tell you this; if you want the best upgrade,
and least effort experience going forward then you may not have 
a choice but to go with 9.04 **Ubuntu jaunty**. Today I got a 
mad streak and did not care if I lost everything and decided to 
upgrade the laptop to 9.04. Noticed that I had skipped 8.10! 
Well I got the best Linux user upgrade experience of my life. 

**Ubuntu jaunty** is the distribution I was looking for as a 
newbie trying to get away from Windows in 2006. 

Here is the jist of what happened:
1) I did not take a backup! (Remember I did not care, but you should.)
2) I downloaded the 9.04 and burnt the ".iso" to CD. Booted, did 
not want to try anything, I just hit install!
3) When came to partitioning it still was not fully intuitive but
it was better than in the past. You just had to change the 
default selected option in the drop down box beside each 
identified drive (other than the swap) to say that you want to 
modify (edit? do not quite remember) and then you will have the 
ability to determine which mount point you want to use it for.
4) I have three(3) partitions on the drive, the first is 
allocated to mount point "/", the second to "/home", and the 
third to "swap". I choose not the format the partitions, except 
the swap (I do not think it permitted otherwise here).
5) Once that was done it went on its merry way and told me that 
it was deleting all "**system files**" found on all the 
drives that could pose an inconsistency to the new installation.

Well this was the first part where I started to breathe a little
easier. For the first time I realized that Ubuntu has got it
right; An install should be able recognize what it has, delete 
what it does not want, and then add back what it has as 
new and leave me with a consistent system, period. This is 
exactly what happened for the next message, after it had done 
its deletions, was to inform me that it was [U]determining what 
files it already had[/U], and which it did not need to copy from off 
the install disk! Fantastic! 

It gets better; After reboot I checked out my system and low and
behold there were no proprietary ATI drivers as I expected, it
usually invalidates them anyway, but I had direct rendering 
turned on and my "glxgears" frame rates were as good, or better 
than with the proprietary drivers. That in itself was a day of  
research and frustration saved. Xorg seems to be at 7.4? Compiz
fusion is automatically installed, and desktop effects can be 
configured. It has been done. Sweet!

I did another reboot and this time update manager told me it had 
about 175 updates to apply. These must be all the updates made 
since the download ".iso" was created. Those updates took a long 
while but there were no issues. My HP "Photosmart C7280" printer 
configuration setup files were now preloaded and was recognized 
in the printer config dialogs. No need to go and get a  >72MB HP 
printer driver package file and spend more hours working on 
getting the printer setup.

"Wine" was knocked out but I could get it back from the 
"**jaunty**" repository. Once installed I was back to normal 
in that arena. No issues with Network Manager and wifi. Fine as 
it has been since 7.10 gusty. So all-in-all the [B]Ubuntu 
jaunty[/B] upgrade took less than a half a day without any 
specialist research to make things work afterwards.

Here is the disclaimer for you though **stjoenewt**, I was 
starting from a much later release than you. I may have been 
lucky, but I think not. My advice to you would be to back up 
your system and try 9.04 **Ubuntu jaunty**. It is also good 
advice given by a previous poster to unmount your Windows drives 
before installing.

Good luck.

---

### Post by stjoenewt on 2009-07-18
pd71sat

Your reply was VERY informative.   Experiences like yours are most enlightening and helpful.   It's knowledge only gained by pain.

What you describe with the upgrades is exactly why I wasn't considering a fresh install.   When I installed 7.04, it was my first time with Linux, and even though I have an IT background (although not in UNIX  :( ), it still took a lot of effort to get everything the way I wanted.   I wasn't looking forward to doing that again.

I agree with you that your description if the installer detecting the current OS and removing it in preparation of then new release is what I would expect of either a upgrade or fresh install.   

I already took a backup, albeit a few weeks ago, in anticipation of this task.   Now I just need to find a window where I can get my family off long enough to do the install.

Thanks again for your advise.

---

### Post by running_rabbit07 on 2009-07-18
I just downloaded and changed from 9.04 to 8.04 LTS 2 days ago and created the /home partition during the install. I only had about 15-20 updates. They have made a new ISO recently for this version, I guess because it is the LTS and most businesses and group installers use it because it is supported until 2011 and longer for businesses.

I truely recommend adding the /home partition because I ruined my OS yesterday trying to install FF3.5 the wrong way and had to reinstall, all of my settings and files in the /home partition stayed safe and when I finished the reinstall all I had to do was a few minimal program installs because they aren't saved to /home. Just be sure when reinstalling or upgrading later down the road that you do not click to format the /home when you set up the mount point or you will lose it all.

I have learned a lot from trial and error over the past couple of weeks because as my wife says I can't leave well enough alone. She's right, but my future goal is to design networks after I finish my CCNA, so i need to practice with everything I can.

---

### Post by stjoenewt on 2009-07-19
running_rabbit07

Thanks for the clarification.

I agree with your partitioning assessment.   When I orginally installed, I did quit a bit of reading on how to best partition the hard drive.   I knew I was going to do that, as I wanted to dual boot.   It looks like that turned out being time well spent.

---

### Post by stjoenewt on 2009-07-21
WOOO  HOOOO  !!!!!   \\:D/

I followed the advise from this thread and things went very well.   I  dismounted my NTFS partitions, and installed from the 9.04 ISO.   There were a few things I ran into and they follow.

When I created my user ID, I didn't see an option to create additional ones.   So, after downloading updates, I went into user maintenance and added my wife and sons.  I got complaints when I attempted to assign the old /HOME directories so simply created new ones.   I then went back after a boot, and switched to the old /HOME directories.  Somehow in doing these steps, the OWNER and GROUP for three of the /HOME directories got switched around (ie Scott owned Brent's /HOME directory), and so I couldn't log on as those users.  I fixed it by using CHOWN -R and CHGRP -R, but never did figure out how that happened.

I also had to reinstall VirtualBox, SKYPE, and GKTPOD which I expected.  Unfortunately I had to rely on my memory for what apps I had added.  Wish I has compiled a better list of what I had installed.

I had to reinstall the printer and add statements to /ETC/FSTAB to mount the NTFS partitions, again not unexpected.  Not sure if I could have avoided having to add the mount entries by specifying that I wanted to use the NTFS partitions or not.

Lastly, I had to redo some security stuff I had done, like setting up a firewall, setting /TMP to noexec, and limiting child processes.   

End to end,it took about 4 hours, which I considered very acceptable.   The new versions of apps like VirtualBox recognized and converted my older snapshots, mail settings were retained, etc.

Great job by the developers.

---

### Post by slakkie on 2009-07-21
> **stjoenewt said:**
> 
I read and attempted to perform the steps called out in both the EOLUpgrade page and bug report 264181, however ran into problems.

I've updated the information on the EOLupgrades as it was a bit out of sync. Too bad it was too late for you though..

---

### Post by raymondh on 2009-07-21
Congratulations and happy ubuntu-ing.

---

