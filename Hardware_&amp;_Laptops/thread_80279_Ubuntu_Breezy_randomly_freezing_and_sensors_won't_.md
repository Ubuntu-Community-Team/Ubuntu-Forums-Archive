---
title: "Ubuntu Breezy randomly freezing and sensors won't work with Via C3 800"
date: 2005-10-21
forum: Hardware &amp; Laptops
---

### Post by killab on 2005-10-21
I have had Hoary running smoothly with no major problems for 6 months, and when I upgraded to Breezy the machine has suddenly started to crash at random times. I basically run slimserver, and backuppc and also use it as a samba server. Nothing really all that intensive. 

The syslog has no information that seems to be helpful.
I'm thinking that it's possible that it's hardware related, but I don't understand why the hardware would cause a crash, when it was working fine with Hoary. Could there be a new driver in Breezy that could have regressed?

So to see if it really is a hardware problem, I tried to install as many sensor related packages I can find, but none of them seem to work with the Via C3 800 cpu that I have running.

hdtemp is working fine for me, and as I keep an eye on it, I haven't seen any of the 3 drives go above 40°C (39°C tops)

I've basically built the machine around a barebones kit from asus with a VIA chip on the motherboard. It seemed like a good deal, but now I'm not so sure.
Details about the barebones kit can be found here:
[http://usa.asus.com/products4.aspx?l1=1&l2=2&l3=0&model=402&modelmenu=1]("http://usa.asus.com/products4.aspx?l1=1&l2=2&l3=0&model=402&modelmenu=1")

So now that I am trying to determine if it's hardware related, I can't get sensors to work.
sensors-detect relveal these drivers:

#----cut here----
# I2C adapter drivers
i2c-viapro
i2c-isa
# I2C chip drivers
eeprom
w83627hf
#----cut here----


But they won't load up at all.

So now, I am at a loss. Am I barking up the wrong tree? Is there another direction I should take this bug hunting? Should I dump the Asus C3 Terminator for a different HW platform? I wake each morning to see that the machine is frozen, and I have to perform a hard reset. When I reboot, the BIOS doesn't warn me of any failures, so I'm really confused. 

Can someone point me in the right direction? Is there some other log I should be looking at?


Many thanks in advaned

---

### Post by killab on 2005-10-23
Bump.

It's still happening. 

Now I'm looking at the EMVS log and I'm seeing some other interesting stuff.

(none) _3_ MDRaid1RegMgr md_analyze_active_region: Kernel said disk[0] was removed.
(none) _3_ MDRaid1RegMgr md_analyze_active_region: Region md/md0, member sda:  Updating superblock to the info obtained from Kernel driver.
(none) _3_ MDRaid1RegMgr md_analyze_active_region: Region md/md0: Updating superblock to the info obtained from Kernel driver.
(none) _3_ MDRaid1RegMgr sb0_set_sb_info: Superblock disk counts have been changed, nr_disks(001) raid_disks(002) active_disks(001) working_disks(001) failed_disks(000) spare_disks(000).
(none) _0_ Engine plugin_user_message: Message is: MDRaid1RegMgr: Region md/md0 is currently in degraded mode.  To bring it back to normal state, add 0 new spare device to replace the faulty or missing device.
  
  Oct 22 23:13:50 (none) _0_ Engine: plugin_user_message: Message is: MDRaid1RegMgr: Region md/md0 : MD superblocks found in object(s) [sda ] are not valid.  [sda ] will not be activated and should be removed from the region.
  
  Oct 22 23:13:50 (none) _5_ Engine: initial_discovery: Discovery time: 00:00:00.230675
  Oct 22 23:13:50 (none) _5_ Engine: is_object_change_pending: Change pending: Object hda1 needs to be activated.
  Oct 22 23:13:50 (none) _5_ Engine: is_object_change_pending: Change pending: Object hda5 needs to be activated.
  Oct 22 23:13:50 (none) _5_ Engine: is_volume_change_pending: Change pending: Volume /dev/evms/hda1 needs to be activated.
  Oct 22 23:13:50 (none) _5_ Engine: is_volume_change_pending: Change pending: Volume /dev/evms/hda5 needs to be activated.


I'll see if there is a diagnostic tool for my drives

---

