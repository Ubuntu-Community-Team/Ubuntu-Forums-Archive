---
title: "Jaunty with raid0?"
date: 2009-04-16
forum: Installation &amp; Upgrades
---

### Post by Skeorx13 on 2009-04-16
I just got a new hard drive for one of my systems (1.5TB). I wanted to try out ext4 and Jaunty. However, the system is currently running XP in a soft raid0 (2x500GB seagate sata). I know trying to install on the raid would either fail or screw the partition. However, would installing on this secondary drive mess up the raid on the other two drives? Perhaps while attempting to mount the raid in ubuntu? I have a considerable amount of info on the raid I don't want to lose (I have backups but it would take me literally a month to restore all the data). If it won't crash the raid would it be accessible in ubuntu (like normal ntfs mounting) or would it not be able to access the data at all?

Also, I had a problem getting ubuntu to recognize a drive of identical specs in another system I have running XP & Intrepid. I had to format it in ntfs before ubuntu would even recognize the drive. I suppose it was because of the drive size (over 1TB). I just left it in ntfs format to prevent the hassle. However on this newer system it would be vital for me to install Jaunty on this drive. If necessary I could try two separate partitions, one Jaunty, one NTFS. 

It's a pretty beefy system and I really want to see what she can do in Ubuntu. I just don't want to trash my XP partition in the process.

system specs:
QX9650
Asus P5E3 premium mobo
2x500GB Seagate sata raid0
8800gts 512
4GB OCZ 1333 DDR3

---

### Post by ronparent on 2009-04-16
You're right; installing on a raid array would be a bit tricky. You ought to be able to set your new drive as boot in bios and install to it normally with the live cd. I doubt that you will want to use the whole drive for one gigantic linux partition so you should choose guided or manual partitioning in that step. The system will not automatically recognize the raid, however, until you install dmraid and run it to map your raid partitions. You can then to add lines for them in /dev/fstab to make them visible to the ubuntu install. If that is what you want I can provide more specific guidance. If done along these lines nothing would be written to the raid0 including the MBR. Also the system would be dual bootable with XP.

---

### Post by Skeorx13 on 2009-04-16
If I don't do the whole partition in linux should I format a partition in ntfs and then linux or vice versa? Will installing on this secondary drive prevent my XP from booting? (Since grub would be on the second drive and not the raid)

From what I gather I'd have to connect the drive, boot up with XP, format a (non-booting) partition in NTFS, reboot with livecd, install linux to another partition on the drive (at which point I should be able to mount the new NTFS partition but not the raid), install dmraid which will give me partition/drive info (for the raid) to add to my fstab, then reboot. So then how would I boot my XP raid? Would grub gather the dmraid info, list the XP OS in the boot options, and forward the boot to the MBR for windows to load? Obviously the info on the drive would be accessible, but will XP still be able to boot as normal?

---

### Post by ronparent on 2009-04-16
Almost. You would connect the new drive, select it as first boot in bios, start the live cd to install, at the partitioning step select guided or manual (make sure you select the non raid drive - it will be the largest disk), decide how big you want the ubuntu partition (30 or 40GB would be ample, mount to /, format probably ext3 etc.), complete the install. If everything goes well, you should be able to reboot to the new ubuntu install. You will have to edit menu.lst to boot to windows  ao that windowsXP boot entry looks something like this:

title       Windows XP (hd1)
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

Once boooted into your new ubuntu install from a terminal you would:

sudo apt-get install dmraid

Run dmraid per 'man dmraid' to map your raid0 drive. Grub does not does not gather the dmraid info. Dmraid set up symbolic link for the raid partitions in /dev/mapper/.
Those links by name are the raid references you add to the /etc/fstab.

If done correctly, grub will start the boot process from your 1.5Tb drive mbr. From there you make your boot choice to boot ubuntu or chain to the windows boot record and thus should have a dualboot setup. When booting windows, windows will load the raid driver to work from the raid (as it does now).

As a note, you will have to create whatever directory structure you want to mount your raid partitions to (ie /media/winXP, /media/Data, etc.). That is where you will see your raid partitions including all files and file structures in your file browser (nautilus). Your existing windows mbr on the raid drive will be left intact and will be acrive if you select that drive as boot in bios or remove or disconnect your new 1.5 Tb drive!

I'm sure I probably forgot something. Ask here if you need more clarification.

---

### Post by Skeorx13 on 2009-04-17
> **ronparent said:**
> Your existing windows mbr on the raid drive will be left intact and will be active if you select that drive as boot in bios or remove or disconnect your new 1.5 Tb drive!
Ah cool, so even if it doesn't work the way I want I can just set the raid to boot from mbr rather than grub on the single drive.

I already formatted the ntfs portion. I'll probably try the rest of the install today and report back.

---

### Post by Skeorx13 on 2009-04-23
The partitions formatted and installed ubuntu but grub failed. For some reason it tried to install onto the first drive of my raid. The raid is still intact and can still boot to XP though, thankfully. I just set the 1.5TB drive to boot first and am trying the install again. Perhaps it will try to install on the right drive this time. Also any commands I tried in the grub terminal to install grub onto the right drive couldn't even find the drive even though the livecd did locate it.

Update: 
grr... grub still won't recognize any drives or partitions. I keep getting error 17 for every possible setup. The install says ubuntu is already installed but grub won't install so how do I even boot to linux without grub???

update2:
AAAAAAAAAAHHHHHHHHHHHH. This is so frustrating. Nothing is working. It is starting to seem like it may be the drive. I finally got a non-error 17. Something about cylinder heads. I might have to move my entire ntfs partition to the back of the drive so that grub feels important or some stupid **** so it will actually install and recognize the drive. However I have to be at work in a few hours and need to force myself to sleep. I'll try again tomorrow and hope I don't throw the install discs out the window.

---

### Post by cobalt017 on 2009-04-24
When I had to install Intrepid on my raid 0 system, I followed the directions here:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Scroll down to the 8.10 section and follow the long version of method 2. I'm not sure if it'll work for Jaunty though.

---

### Post by Swooper86 on 2009-04-24
When I tried to install Intrepid on my raid0, I [had trouble]("http://ubuntuforums.org/showthread.php?t=991112")...

Incidentally, I'm thinking of trying again from scratch soon. I was told Jaunty was supposed to include added raid support, but I can find no evidence of this fact. Can anyone confirm/deny that rumour?

---

### Post by Skeorx13 on 2009-04-25
I don't want to install ubuntu on the raid, just the new hard drive. However the raid0 is the windows boot and I don't want to have to switch the boot drive priority in the bios every time I want to boot to XP.

---

### Post by ronparent on 2009-04-25
Right now, can you boot anything with the bios set to boot on the new drive?

---

### Post by Skeorx13 on 2009-04-26
Ok I moved my ntfs partition to the back of the drive and the ext4 to the front. I finally was able to install grub but it still wouldn't boot so I wiped that partition and reinstalled. This time grub installed properly and I got to boot up. I installed dmraid and briefly scanned the man page. I don't really have time to mess with it right now but I will probably have time later tonight. I have a feeling I'll need a few tips on using it...

---

### Post by Skeorx13 on 2009-05-05
Ok I'm having trouble finding resources on dmraid that apply to my situation. Am I correct in assuming ```
sudo dmraid -r
``` or ```
sudo dmraid -s
``` will list my two raid drives (sda and sdb) and their relative info? Then what do I do to mount them and edit into fstab? A step by step with commands to enter would help me a lot. Please let me know what other info you will need.

Info:
raid0 (mobo/software based)
2x 500GB seagate sata drives in the raid: sda and sdb with XP home on it.
sdc is my 1.5TB sata drive with Jaunty (ext4), grub, non-boot NTFS, and swap on it.

---

