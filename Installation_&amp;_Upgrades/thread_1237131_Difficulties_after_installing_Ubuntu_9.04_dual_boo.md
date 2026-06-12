---
title: "Difficulties after installing Ubuntu 9.04 dual boot with Windows XP Sp3"
date: 2009-08-11
forum: Installation &amp; Upgrades
---

### Post by jolt9157 on 2009-08-11
[FONT=&quot]Motherboard:  Asus M3A[/FONT]
  [FONT=&quot]CPU:  AMD Phenom 9600 Quad core 2.3 gHz[/FONT]
  [FONT=&quot]Hard drive:  Seagate 500 GB SATA/300 (ST3500641AS – RK) drive[/FONT]
  [FONT=&quot]Video card:  old AGP4x radeon card (nothing fancy) purchased off of woot.com[/FONT]
  [FONT=&quot]DVD/CD drive:  LG Super Multi Model GSA-H54N[/FONT]
  [FONT=&quot]Memory:  crucial ballistix 1 gb DDR2 x2 [/FONT]

  [FONT=&quot]Saturday night, I installed Ubuntu 9.04 (i386) on my hard drive.  It was a dual boot installation with Windows XP Pro SP3 (windows had been installed prior).  The hd had 3 primary partitions and an extended partition.  Ubuntu was installed on a logical drive on the extended partition (4GB of partition were devoted to swap as well).  Installation went without a hitch.  [/FONT]

  [FONT=&quot]I reboot and the GRUB bootloader works fine.  Ubuntu boots up and everything works great.  I connected to my network on Ubuntu but could not load any websites.  Confused, I rebooted into Windows XP.  On XP, I was unable to connect to my network.  [/FONT]

  [FONT=&quot]I did a cold reboot, thinking that would solve it.  All of a sudden, I have no post and 5 beeps (Asus website/manual says CPU issues).  I try again and again, same thing.  2 hours later, the BIOS posts and goes to GRUB bootloader.  However, I receive the following error:  grub loading stage1.5Read error (after numerous reboots, I still receive this error).  Was able to run memtest86 off of livecd….normal.    [/FONT]
  [FONT=&quot]When I try to load linux from the livecd or try to get to the installation menu, I see the code cranking away and then the following code repeating:[/FONT]
  [FONT=&quot][ 110.234343] ata4.00:  status:  { DRDY }[/FONT]
  [FONT=&quot] [numbers following same format]Ata4:  softreset failed (device not ready)[/FONT]
  [FONT=&quot][numbers following same format]Ata4.00:  exception emask 0x10 SAct 0X1 SErr 0x90299 action 0xe frozen[/FONT]
  [FONT=&quot][numbers following same format]Ata4.00:  irq_stat 0x00400000x PHY RDY changed[/FONT]
  [FONT=&quot][numbers following same format] Ata4.00:  cmd 60/08:00:00:00:00/00:00:00:00:00/40 tag 0 ncq 4096 in[/FONT]
  [FONT=&quot][numbers following same format]res 40/00:00:00:00:00/00:00:00:00:00/40 Emask 0x10 (ata bus error)          [/FONT]
  
  [FONT=&quot]I have similar results when using the gparted livecd.  [/FONT]
  
  [FONT=&quot]I tried to run cute partition manager to delete the linux partition:  I receive the following error message:[/FONT]
  [FONT=&quot]Initialization failed:  no disk drive.  [/FONT]
  
  [FONT=&quot]So Grub bootloader isn’t working, linux isn’t working, and I cant seem to get into Windows xp to delete the partition to save my life.  After rebooting so many times, my computer is unable to post and I hear the five beeps.  FML?   Any and all help would be appreciated (also, I am newer to this, so I may need layperson speak).  
[/FONT]
Thanks!

---

### Post by tommcd on 2009-08-11
> **jolt9157 said:**
> [FONT=&quot]
So Grub bootloader isn’t working, linux isn’t working, and I cant seem to get into Windows xp to delete the partition to save my life.  After rebooting so many times, my computer is unable to post and I hear the five beeps.  FML?   Any and all help would be appreciated (also, I am newer to this, so I may need layperson speak).  

Are you able to get into the motherboards BIOS? If your motherboard can not even POST, then this is not a problem with Ubuntu or Windows. It is a hardware problem of some kind. If the Asus website says 5 beeps indicates a problem with the CPU, then that is a good place to start.

---

### Post by jolt9157 on 2009-08-11
I am able to post the majority of the time.  The rest of the time it doesn't post and I hear the five beeps.  

However, when it does post, neither the grub bootloader works nor am I able to load linux (see above codes).

---

### Post by caribconsult on 2009-08-11
If you are getting POST errors, or even worse, it just stops, this is indicative of hardware, not software. 

You have an intermittent problem, the most difficult to find, since it comes and goes.  Do you find the unit starts better when it is completely cold?  If so, you have a thermal intermittent; something heats up to operating temperature and then goes off the rails.  Could be your motherboard, cpu, or RAM.  I'd suggest you get a different M/B, CPU and RAM and then try it.

---

### Post by jolt9157 on 2009-08-11
I know it makes sense to attribute both problems (1 being the difficulty to get to post and 2 being the fact that grub and linux aren't loading correctly) to a single problem (i.e. the mb, cpu, RAM).  

However, if I wasn't having the post difficulties, would your advice be the same?  

If I said everything posted perfectly and I received the above error regarding GRUB and linux, would you be saying the same thing?  

The reason I ask is because I would have the occasional post difficulties with windows before I loaded liunx.  Now that I've loaded ubuntu, the difficulty has increased significantly.  However, once I post, I believe that if it was just my CPU acting up, Grub/Linux would run fine if I was able to post.  Is that incorrect?

---

### Post by phillw on 2009-08-11
There does appear to be a problem pointing to your CPU. The above reply is quite correct in saying that getting past POST is completely independent of whatever Operating System you have.

Some things that can cause this sort of error are as mundane, yet serious, as cooling fan(s) not working - a fan can either die, or become gradually gunged up with fluff etc. It's worth a quick check - Better than risking having your CPU fry. Check that your Power Supply fan, also is running as voltage drops from the power supply can wreak havoc with POST and the general stability of your machine.

Other things that could cause a problem - even though it is reporting it as cpu, would be  badly seated RAM, video card, HDD cable... etc.

first things first - let's get you with a system that passes the POST - that is why POST is run by your BIOS - it is completely Operating System independent - In extreme cases I have removed the video card (and any other cards), hard drive, RAM .. Just the CPU left - the POST then should just moan about the RAM, add the RAM .... You should get past POST. Add the Video card (and other cards) .. try again ... lastly add the hard-drive. (I say to add the hard-drive last, as you don't want to be powering off hard drives with the on/off switch - you risk corrupting the hard drive)

Even if there is a problem with the install, the fact your PC is struggling to get past its POST is the 1st and major concern. 

In answer to your other question - If your machine were getting past POST, we would indeed, suggest something else. 

Hope this is of help.

Regards,

Phill.

---

### Post by jolt9157 on 2009-08-11
I cleaned out my tower today with an air duster.  Minor posting issues thus far.  Gparted booted no problem, but it didn't detect any devices.  



I cannot detect any of my hard drive partitions during the ubuntulivecd session.  
Mb recognizing my SATA hd is sporadic.  

Grub still doesn't load and gives the above error.  


Booted windows xp pro cd and windows recovery gives the following message:
Setup did not find any hard disk drives installed on your computer.  


Aside from the posting issues, any chance I might have messed up my hd?  Any other recommendations from here?

---

### Post by stlsaint on 2009-08-11
thats what i was thinking as i read your original messge...HardDrive!! can you boot into like hirens boot or an acronis cd to do any test on your hdd...if EVERY cd you try and boot to test your hdd and they all say the same thing?!! NO Drive than i would think you have a bad drive!! test it by slaving it off of another computer...will have to get ide or sata conversion cable depending on what you have!

---

