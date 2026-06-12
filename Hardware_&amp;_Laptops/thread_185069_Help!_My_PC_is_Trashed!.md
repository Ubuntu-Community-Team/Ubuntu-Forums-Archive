---
title: "Help! My PC is Trashed!"
date: 2006-05-31
forum: Hardware &amp; Laptops
---

### Post by beeldings on 2006-05-31
Running an AMD Athlon 64 3200+ with 2G DDR 400 Kingston ValuRam, and PNY Verto GeForce 6200 256M AGP. What happened is that while on a quest to enable AGP Fast Writes, I decided that I should flash the BIOS with the latest version. I visit the Asus web site, download the latest BIOS, load it on a floppy, and reboot. The Asus update utility states that the ROM ID does not match the system's BIOS ID, so the update is aborted. I decide to flash the BIOS with the original factory BIOS located on the driver CD. Done. I enter the BIOS, load setup defaults, make a few changes to the memory timings and reboot. Black screen. Nothing happens, no POST, no HDD activity, nothing. I start to panic until I realize that I can force recover the BIOS by setting a jumper on the board itself. About an hour later after tinkering with the hardware and cabling, I finally get the PC to boot. I enter the BIOS, load setup defaults and enable AGP Fast Writes and change my boot device priority. I reboot and load Ubuntu. However, when "Checking root filesystem" loads, the PC freezes. I reboot, enter the BIOS and load setup defaults, reboot again, load the kernel recovery mode, and manually start GDM as root. I log in, Gnome loads, and then it immediately freezes. I reboot my system again, load the recovery console, change my video driver to vesa and start GDM. I can log in and while the system doesn't freeze, it reboots after a few seconds. This time I proceed to load memtest, however before it can begin to check my memory, the system reboots. I load the Ubuntu installation CD and try to run memtest from there, but the PC reboots again. After the system reboots, I load the recovery console and install links, and here I am. I honestly don't know what to do. I bought the computer a little over a month ago and invested a lot in upgrades (both time and money) and I would be pretty annoyed if I have to replace it. So, what do you guys think? Did I destroy the memory? Could it be a corrupt BIOS? Where do I go from here? I apologize for how this post is formatted and if I made a double post, but it's pretty difficult to post on the forums from the command line.

---

### Post by beeldings on 2006-05-31
I should have mentioned this earlier, but the board is either an ASUS K8V-MX or K8V-MX/S. The manual is for the K8V-MX, but there's a sticker on the motherboard itself labeled "K8V-MX/S," so I really have no idea what 'board I'm using. Also, I am running Dapper Drake. If I have to replace the motherboard and memory, no biggie, but if I have to replace the whole system, yeah, the s*its gonna hit the fan. Ok guys, it's been a long night, I'm off to bed.

---

### Post by H.E. Pennypacker on 2006-05-31
I was going to say you should have used paragraphs, but your story is already depressing as it is.

It is safe to say that your computer had absolutely no issues prior to your tinkering with the BIOS.  If that is the case,  we can also safely conclude what happened is directly related to the tinker.  If this proves to be true, you won't have to worry about your files and other stuff on the HD.  That should be fine.

The solution should lie in having the BIOS go back to a previous state.  How that is done exactly, I don't know.  I'll do some research and I'll try to find out.  

1. What's the BIOS version?
2. Motherboard name and any specific details?

Add anything else you think we should know.

Note: I simply can't figure out what's causing the reboots, and how a defect in the BIOS could cause such a problem.

EDIT: Additional info was provided before I completed my post.

---

### Post by _simon_ on 2006-05-31
As the bios is all you changed I wouldn't have thought it would have impacted any other components. 

Your board isn't very expensive, just to get your system back up and running I'd be tempted to just get another board then fiddle with getting the old one to work and keep it as spare or sell it on.

The only other thing to really cause random reboots is the PSU... it could be a coincidence.... if you believe in those.

---

### Post by beeldings on 2006-05-31
I did some research on Google and I retrieved what I believe is the latest BIOS for the motherboard. If this BIOS upgrade doesn't solve my problems, then I am going to test each stick of memory to determine if one or both of them is damaged. From there I will try to return the memory for a replacement, however if the problem still occurs with the new memory, then I will now it's a problem with the motherboard itself and that will be replaced (with a much better unit, I might add). If the problem STILL occurs after replacing the motherboard, then it will be a problem with the PSU like _simon_ mentioned earlier.

BTW, I'm posting this from my old PC. It's slow, it's damn-near obsolete, but (knock on wood) it hasn't given me any problems.

---

### Post by beeldings on 2006-05-31
Ok, the BIOS I downloaded this morning did the trick. After reflashing the BIOS, I booted into memtest and let it run for nine-and-a-half hours while I was at work. My memory passed memtest with no errors and after rebooting the PC and loading Ubuntu, the system appears to run very stable. Now I know not to mess with memory timings...hopefully someone can benefit from my mistake.

---

### Post by H.E. Pennypacker on 2006-05-31
It's good to know everything's taken care of!

---

