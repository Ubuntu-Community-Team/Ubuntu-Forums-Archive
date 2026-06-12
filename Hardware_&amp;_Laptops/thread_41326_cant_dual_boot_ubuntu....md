---
title: "cant dual boot ubuntu..."
date: 2005-06-13
forum: Hardware &amp; Laptops
---

### Post by mrweirdo on 2005-06-13
Hey all well I went and installed ubuntu linux on a drive in a removable bay inside my system(secondary drive on secondary ide cable).  I didnt want to even mess with my main windows drive(primary on primary ide cable) so I wound up disconecting the windows drive from my system while I installed ubuntu. Anyways here is my problem now I want to be able to do a dual boot using boot.ini. I searched google and found some instructions on how to do it so I created the ubuntu.bin in ubuntu and copyied it over to my windows drive. Then I added 
C:\ubuntu.bin="Ubuntu"
in boot.ini as a boot option. So then I restart my system this time with both drives hooked up and enabled through bios.  Now If i chose this new option I allways get a blank screen if i try to boot ubuntu. The only way to boot ubuntu still is by disabling my main hard drive in my bios.

Any ideas on how to get this working?

---

### Post by defkewl on 2005-06-13
Why didn't you use Grub?

---

### Post by FLeiXiuS on 2005-06-13
[QUOTE=defkewl]Why didn't you use Grub?[/QUOTE]
Ahem :-P tis perfectly fine to use boot.ini :-).  Just a bit different.

[quote=mrwierdo]
Any ideas on how to get this working?
[/quote]
You can take a look here ([http://www.ubuntulinux.org/wiki/WindowsDualBootHowTo)](http://www.ubuntulinux.org/wiki/WindowsDualBootHowTo)), there's an example of how to get this working; just scroll down to step three.  It's best to keep the primary drive in the computer while being configured and enabled.  Nothing is in harms way other then the the users primary senses.  Always remember to not bother /dev/hda* in any way.

If problems still exists please let post again and I will be more then happy to include further details on the issue at hand.

---

### Post by mrweirdo on 2005-06-14
well on advice of a friend I just went ahead and reinstalled ubuntu with both drives enabled and actualy used the grub bootloader replacing the windows one in the mbr. I shouldnt have though because now that Ive been using ubuntu for awhile I dont think its quite ready for replacing windows on my main system. The main reason being the fact that my creative sb live 5.1 sounds way beter under windows with creatives drivers. The difference in sound quality is amazing and since I'm allways listening to music or editing music on my comp I'm gona keep windows.

Ubuntu is going on anouther box I'm planing on rebuilding though :)

Now I need to figure out a way to put the old boot.ini back into the master boot record.

---

### Post by davidmigl on 2005-06-14
It's rather simple.  Put your Windows CD in the drive, make sure your CMOS is set to boot to the cd first, and reboot.  Boot to the CD, and enter the Recovery Console (i think by pressing "R").  Logon to your installation and type "fixmbr" (without the quotes), and Windows should overwrite the MBR with it's boot loading process.

I'm in the same situation now, so I'll probably be doing a similar process.  There are just too many conflicts with ATI cards, dual monitors, and adjusting AA/AF for OpenGL apps.

---

### Post by chgokt7raid on 2005-06-26
Instead of creating a new thread, I thought I'd add onto this one.

After reading through ubuntuguide and the wiki howto on dual boot, GRUB doesn't actually load.  I only get a glimpse of it (ie. GRUB loader 1.5---or something along those lines, it's all very fleeting) before my system reboots.  After a second try, and after using FIXMBR to start all over again, I figured I'd tap into the collective knowledge of folks such as yourself who know more than I do.

What I'm trying to do is pretty much what the wiki howto suggests doing.  One drive, XP on partition 0, root on part 1, swap on 2, and sharing on 3.  However, I used Ubuntu to partition and let XP install on C: or "0".  Ubuntu installs all the way through until I have to reboot and it just doesn't work for me.  

One of the first few comments on the wiki warns against letting GRUB override the MBR and, instead, suggests using WinXP's boot.ini.  Does this only happen on select machines?  I have an Abit KT7-raid with a 160GB Seagate on one of the ATA100 channels.  Is there any difference using boot.ini over GRUB?  If this a hardware issue, should I bug it?

Any help would be greatly appreciated.  Thanks in advance.

---

