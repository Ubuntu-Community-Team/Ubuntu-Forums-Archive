---
title: "Video Card Question"
date: 2009-12-13
forum: Hardware
---

### Post by deamon_knight on 2009-12-13
I have some spare pieces I'm putting together for secondary desktop I'd like to use for some light gaming. However, my video card is an older ATI 9600. I thought this was supported but it has been deemed legacy by ATI and is no longer supported. Karmic boots and I can enable desktop effects but I don't think I can game without the proprietary drivers. Is there any fix for this? I don't suppose I can just download and install the drivers from ATI's site on Karmic, am I wrong? I thought 9.10 used Xorg 7.4, that appears to be the requirement listed:

[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.24&lang=English]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.24&lang=English")

[I]AMD may periodically provide Windows XP and Windows Vista driver updates (for the products listed above) for critical fixes only.  No new features will be provided in future driver updates.  The Linux ATI Catalyst™ driver will only be supported in Linux distributions prior to February 2009 for the legacy products listed above.
[/I]

But if I wanted to use a version of Ubuntu that supported these drivers, how would I go about Identifying what was needed? Booting to a live CD Jockey shows no proprietary drivers available for this hardware in 9.04 or 9.10. 

Also, I'm trying to Play Civ4, and I think I need a fairly recent version of WINE to make it work, so earlier versions of Ubuntu will have additional difficulty. Am I stuck?

---

### Post by staf0048 on 2009-12-13
I have an ATI Radeon Xpress 200m on my laptop and the driver from the nVidia website didn't work when I had 9.10 installed.  Got a flashing screen that was stuck at the command line prompt login.  

However, it works beautifully on 8.04, so you might want to give that a try.  Sure it's a little old, but still supported for the next 2 years or so.

Also, go to the winehq website to get the latest version of wine installed on 8.04 - or you could even try playonlinux, they might have an installer that will help you configure the game you want installed in wine perfectly.

---

### Post by deamon_knight on 2009-12-13
Well , the problem is not that the drivers don't work its that they are not available in Jockey at all. So I don't know why I can't just install the drivers from ATI's site. I may try to do this anyway and see what happens.

---

### Post by deathbyswiftwind on 2009-12-13
Your best bet would be to install 8.04 and use those drivers. My wifes laptop has a radeon 9600 and its the only way I can get gl enabled to its full capabilities.

---

