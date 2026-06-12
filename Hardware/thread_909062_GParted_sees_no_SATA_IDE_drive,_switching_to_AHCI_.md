---
title: "GParted sees no SATA IDE drive, switching to AHCI not an option"
date: 2008-09-03
forum: Hardware
---

### Post by cyberco on 2008-09-03
I have a new Windows XP X64 machine that I want to turn into a dual boot. In the bios my SATA disk is set to ENHANCED IDE mode (since AHCI doesn't bring me much and the XP installation doesn't  support it out of the box). Now, when I want to install Ubuntu 8.04 from the live CD no partition shows up when GParted is launched. I've read that switching to AHCI should solve this, but that is not an option since it will break my existing XP installation while it offers nothing extra.

What are my options?

Thanks!
2B

---

### Post by falcon61102 on 2008-09-03
When you boot from the liveCD, press F6 and a menu with additional boot options will pop up.  Try one or a combo of those and you should be able to get it working.  From everything I've read, its really hardware specific so it's not a guarentee that one or a combo of any of them will actually work but many people have success with this.  Also, if you do get everything working with one of those commands, you will probably need to add that to your menu.lst when you eventually install so you don't run into that problem then.

---

