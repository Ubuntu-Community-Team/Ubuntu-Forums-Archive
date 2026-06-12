---
title: "ATI and Nvidia videocard powersaving features"
date: 2013-06-16
forum: Hardware
---

### Post by user_of_gnomes on 2013-06-16
So I've always been an AMD/ATI buff but it seems that ATI isn't actually the best choice for Linux. the open source drivers are decent but they lack power saving features that I find more important than actual performance. Switching profiles is O.K for me personally but not for some of the other computers I maintain.

I tried loading the propietary drivers for my HD5770 but they seemed extremely unstable, causing crashes the open source drivers did not do. I'm hesitant to use these drivers on the other machines.

Is it still the general concensus that Nvidia is more suitable for Linux than ATI? And if so, will the open source Nvidia drivers allow me to fully utilize all the power saving features on a videocard automatically or will I be forced to use the propietary drivers as well?

---

### Post by Yellow Pasque on 2013-06-16
> And if so, will the open source Nvidia drivers allow me to fully utilize all the power saving features on a videocard automatically or will I be forced to use the proprietary drivers as well? 
The open-source nvidia driver (nouveau) is stuck on the low/idle clock speed for modern nvidia GPU's:
[http://www.phoronix.com/scan.php?page=article&item=nouveau_april_2013&num=1](http://www.phoronix.com/scan.php?page=article&item=nouveau_april_2013&num=1)

---

### Post by user_of_gnomes on 2013-06-16
> **Temüjin said:**
> The open-source nvidia driver (nouveau) is stuck on the low/idle clock speed for modern nvidia GPU's:
[http://www.phoronix.com/scan.php?page=article&item=nouveau_april_2013&num=1](http://www.phoronix.com/scan.php?page=article&item=nouveau_april_2013&num=1)

Thanks, that was very helpful.

> For those serious about open-source graphics driver and needing to use it in a production setting rather than playing Russian Roulette with Nouveau upgrades, the Radeon driver is still generally better off. This is especially the case while the open-source Radeon driver holds the leads with power management, re-clocking, and most recently is the UVD hardware video playback support.

> Lastly, when bumping up Xonotic's visual quality to high, the performance of the AMD open-source Linux graphics driver was about 76~80% that of the Catalyst driver.

Overall, these results are quite promising for these GL2 era games that are now appearing much more competitive on the open-source Linux graphics driver against Catalyst than has appeared in the past. Sadly though the OpenGL support level is still a ways behind with this open-source driver (OpenGL ~3.2 support instead of OpenGL 4.2) plus other missing features like incomplete power management, more advanced AA modes, and other functionality.

That's actually quite decent. The only thing that bothers me is the lack of power management. From what I understood, this is because AMD/ATI is worried that the competition will get a hold of vital data. 

After having read the above I think I'll stick with ATI and the open source drivers as they seem to grow by leaps and bounds. I'll just have to deal with the heat and energy usage issues arising from the lack of power management with profiles.

---

