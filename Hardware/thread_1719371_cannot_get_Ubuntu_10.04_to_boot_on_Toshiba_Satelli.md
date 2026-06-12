---
title: "cannot get Ubuntu 10.04 to boot on Toshiba Satellite 1130"
date: 2011-04-01
forum: Hardware
---

### Post by johnyd on 2011-04-01
Hi all,

I have a Toshiba Satellite 1130 that I'm trying to load Ubuntu 10.04 on. I have the dvd-rom set as the first boot device and have tested the burn of 10.04 in my own system and it is working fine. Does anyone have any knowledge of loading Ubuntu onto this laptop?

The detailed spec sheet on the notebook is [here]("http://dl.dropbox.com/u/899652/satellite_1130.pdf"). 

It currently has Windows XP loaded on it. It's in a broken state, is missing some system files and refuses to boot. It also is refusing to boot the Ubuntu dvd media as well.

Any help with this is much appreciated.

Thank you

---

### Post by Lateralis on 2011-04-01
I think we might need some more information before we can give you some specific advice.  

You say the laptop will not boot to CD but the BIOS is set to boot from CD before the hard disk?  

At what point does the LiveCD boot sequence fail?  Do you see nothing but a black screen?  

Do you get the Ubuntu LiveCD menu asking if you want to try a live session or installing directly?  

Does the laptop instead try and boot into Windows?  



If the laptop tries booting into Windows that would probably suggest the CD/DVD drive isn't the first boot device or the CD/DVD drive does not work properly.  If you get the Ubuntu menu but it fails to load a live session then there is probably an incomparability with your hardware, most likely your graphics.

---

### Post by johnyd on 2011-04-01
> You say the laptop will not boot to CD but the BIOS is set to boot from CD before the hard disk?  Yes, bios is set to boot from dvd prior to hdd.

> At what point does the LiveCD boot sequence fail?  Do you see nothing but a black screen?  As far as I can tell the live boot cd does not even begin. I just get a black screen after a veerrryyy slow bios post. After a long wait (30 seconds or so), after that it informs me that there are missing Windows system files... so it looks as though it is not booting from live cd.

> Do you get the Ubuntu LiveCD menu asking if you want to try a live session or installing directly?  No, black screen and then Windows error message.

> Does the laptop instead try and boot into Windows?It seems so, yes.

---

