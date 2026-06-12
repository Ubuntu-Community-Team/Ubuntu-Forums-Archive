---
title: "[SOLVED] Intrepid and ATI HD3450 repost"
date: 2008-11-03
forum: General Help
---

### Post by 73ckn797 on 2008-11-03
Well, I am back to trying to figure out how to get the ATI HD3450 video card to have full acceleration after a fresh install of Intrepid. These were issues with Hardy but I found a fix: [http://ubuntuforums.org/showthread.php?t=902913](http://ubuntuforums.org/showthread.php?t=902913). That procedure does not work with Intrepid. I earlier had reinstalled Hardy again and my earlier procedure did not work. Any suggestions? I might just revert back to Hardy on this computer or until I can afford another Nvidia card.

Until ATI provides better support I will not be able to get the full benefit of using the ATI card. I realize this is not a Ubuntu issue but a support issue via ATI.

The system does load, by default, a driver that does allow high resolution with 75Mhz refresh rate. When trying to set appearances to extra, allowing restricted driver to install, then logging out or rebooting, the system comes back with an unsupported mode or out of range. That could be the monitor being used. I can hear the login music but have no display. Recovery mode thru grub resets back to the default driver.  Seem to be going in circles.

I have connected the computer using 2 different monitors. One is actually a Samsung 46" DLP TV with the PC connection. Best resolution is 1024x768. Any attempt to change that results in a black screen.

I get better resolution using a ViewSonic VA902b LCD running at 1280x1024 and there are still higher resolutions available.

Downloaded Envy but it was no where to be found afterwards.

I have the latest ATI 8.10 "run" file but that would not load following the wiki instructions.

Hopefully this post will get some response.

---

### Post by 73ckn797 on 2008-11-06
No solutions offered so I will abandon trying to use Ubuntu on the system with the ATI graphics card. It isn't my computer anyway.

I am sure there is a solution but I do not desire to spend anymore time on it.

Love using Ubuntu but despise ATI support.

---

### Post by Blue Beard on 2008-12-23
I dropped my ram from 4GB to 2GB to get the card partially working.

It appears iommu needs a window in the first 4GB.  Some motherboards can handle this.

I have other issues now and was not happy ATI will not officially support linux.

---

