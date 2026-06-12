---
title: "Lenovo G770 not resuming correctly after suspend"
date: 2012-07-11
forum: Hardware
---

### Post by blasmat on 2012-07-11
I am running Ubuntu 12.04 on a Lenovo G770 (core i5, 8gb RAM, RadeonHD 6650 (using proprietary Catalyst drivers) + Intel HD3000), and everything was working fine until I upgraded to kernel version 3.2.0-27 via Update Manager. Now when I attempt to resume after suspend, it comes to a blank black screen (backlight is on) with a responsive cursor, but never loads the wallpaper or brings up the dialog box asking for my password. This occurs regardless of whether I am using the integrated or discrete GPU.
 
I am able to get to a prompt using Ctr-Alt-F1, but Ctr-Alt-F7 just brings me back to the same screen with a responsive (but useless) cursor. Since I hadn't had an issue before upgrading the kernel, I tried rebooting and selecting "Previous Linux Versions" and "Ubuntu with Linux 3.2.0-26" from the GRUB menu, but found that suspend no longer works under the previous kernel version either. 

I don't know if it is in any way related or if it might shed some light on the issue, but since the kernel upgrade I no longer see my desktop wallpaper at the login screen, only a solid purple wallpaper.

Being able to suspend and resume is quite important to me as this is my primary computer and is both used and transported with me *very* frequently, and the idea of having to wipe everything and perform a fresh installation (for the second time) is extremely frustrating, particularly over something that was a complete non-issue up until yesterday. I will be extremely grateful for any assistance anyone can provide!

---

### Post by blasmat on 2012-07-27
*bump*

Anyone have any insight on this issue? I've been using Gnome Shell since it suspends/resumes without issue, but I had grown accustomed to and now prefer Unity...

---

