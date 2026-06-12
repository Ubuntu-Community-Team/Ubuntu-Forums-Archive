---
title: "Profile: ASUS Z71V"
date: 2005-04-10
forum: Hardware &amp; Laptops
---

### Post by TheRealEdwin on 2005-04-10
Last week a new laptop was released upon the computing world which I happen to like due to the stats it has. [System Specs](http://www.smilepak.com/Z71V_Project.doc)

Anyways after installing XP I put on Hoary on this to dual boot and have noticed a few things. Please realize this is new hardware and stuff should be expected to not work, so this thread is a made to grab the attention of the community to alert them of various issues.
[list][*]Sound: Doesn't work. See resources.
[*]Networking turns off after some time even in the middle of use. This applies to both wired and wireless.[/list]
[Main ASUS site for this model](http://www.asus.com.tw/support/download/item.aspx?ModelName=Z71V&Type=Latest)
[Manual](http://www.asus.com.tw/support/download/selectftp.aspx?l1_id=3&l2_id=43&l3_id=0&m_id=2&f_name=e1825c_z71_hw.pdf~zaqwedc)
[User support thread](http://notebookforums.com/showthread.php?t=72349)
[System specs thread](http://notebookforums.com/showthread.php?t=64256&highlight=z71v+specs)

---

### Post by MooseMuffin on 2005-05-05
Hey Edwin, have you made any progress getting ubuntu to work with this laptop?  I have it as well and would really like to dual boot, but Id rather not waste my time if people haven't gotten it to work.

---

### Post by Knightjar on 2005-06-03
I have hoary running on a new one of these too. I haven't noticed any problems with networking turning off (connecting via DCHP to a LAN). However, add to the list:

Can't find its modem (and the scanModem program as suggested elsewhere doesn't seem to identify it either)

/var/log/messages filled up with 'Asus ACPI: Error reading LCD status' and periodically flashing up 'display changed:lcd off'

None of the function/hot keys working except FnF7 for dimming the backlight

This middle one only turns up under KDE which is what I want to use, The last two seem to be issues on various other Asus models and there's some sort of project at [http://sourceforge.net/projects/acpi4asus/](http://sourceforge.net/projects/acpi4asus/) which has fixed it for them, it just doesn't seem to for the Z71V yet. There's a fix for the sound mentioned elswhere [http://ubuntuforums.org/showthread.php?t=30024&highlight=asus](http://ubuntuforums.org/showthread.php?t=30024&highlight=asus) 

I'm none too experienced, and haven't managed to get any of these sorted yet, any help much appreciated.

---

### Post by secundar on 2005-06-03
I also have this laptop. Love it.

But I learned the hard way that WinXP wants to be on the first partition (NTFS), Ubuntu is on the second ext3 and i made a FAT32 to share files between them.

Suspend to disk works but have not figured out how to suspend to ram.

Don't understand enough to build ALSA so audio does not yet work.

---

