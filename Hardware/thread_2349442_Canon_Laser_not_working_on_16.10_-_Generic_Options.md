---
title: "Canon Laser not working on 16.10 - Generic Options?"
date: 2017-01-14
forum: Hardware
---

### Post by B34N on 2017-01-14
I have a Canon LBP6030 connected through WiFi that works fine on my older Ubuntu (pre 16.04) machines but I cannot get working on my main computer that I upgraded to 16.10. It appears that the reason is due to libbeecrypt being a dependency. I tried to add the dependencies but either there is more to it or I messed up because I still get errors that a dependency is not met but it does now allow me to select the printer's driver, but nothing prints. No error messages or anything. It seems to see the printer but nothing prints.

If I wanted to abandon the Canon drivers altogether, how would l set the printer up as a generic? I do see it listed in "Network Printer" when I do to add. It then give me the AppSocket as the only connection method. When I go to find drivers I can choose Generic but I don't know which generic to try. I've attempted a few (Such as Generic PCL Laser) and when I go to print the test page I get an error "Unable to locate printer."  Any thoughts?

Thank you!

---

### Post by pdc on 2017-01-15
so this would need the Canon UFR driver? I wondered which version you used; as Canon released a new version on the 16th Dec? It now has an install script so should install quickly: mentioned in post #6 here [https://forums.linuxmint.com/viewtopic.php?f=51&t=180109](https://forums.linuxmint.com/viewtopic.php?f=51&t=180109)

---

### Post by B34N on 2017-01-15
> **pdc said:**
> so this would need the Canon UFR driver? I wondered which version you used; as Canon released a new version on the 16th Dec? It now has an install script so should install quickly: mentioned in post #6 here [https://forums.linuxmint.com/viewtopic.php?f=51&t=180109](https://forums.linuxmint.com/viewtopic.php?f=51&t=180109)

Thank you for the response.

I was using Linux UFRIILT v1.30 which has a similar nice install script and was also updated on 12/16/2016. Unfortunately that version still has a dependency of libbeecrypt7 and libbeecrypt-dev.

Based on your response, I tried the version for UFRII (No LT) mentioned in the linked forum post and got very excited when it ran without any dependency issues. Unfortunately my LBP6030 is not one of the listed printer drivers available after installing. I tried using one of the other LBP models and no luck.

Edit: Correction...the driver in the linked post seems to be both UFRII and UFRII LT but still my 6030 is not one of the printers listed.

---

### Post by B34N on 2017-01-15
After much time pulling me hair out I was able to get the printer working by installing the v1.3 drivers that the Canon US support site has as the latest driver for my printer (LBP6030). I did need to install the libbeecrypt dependencies but I did so at the command line this time and it worked. I guess it wasn't actually installing when I tried using the GUI Software Install. Thank you for your help and hopefully this will help someone else out too.

---

### Post by pdc on 2017-01-15
well done to get it sorted; I must say I admire you running 16.10; that is very organised of you; I just stick with the LTS versions; so I plan to run 16.04 till 2021 when it runs out of support; you will be upping sticks and moving on this July when 16.10 runs out of support? Canon do a good job of updating their drivers, but they tend to sync more with the LTS versions; so I hope your very good 6030 keeps going for you

---

