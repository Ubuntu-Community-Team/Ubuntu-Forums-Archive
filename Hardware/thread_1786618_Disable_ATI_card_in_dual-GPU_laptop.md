---
title: "Disable ATI card in dual-GPU laptop?"
date: 2011-06-19
forum: Hardware
---

### Post by smashweights on 2011-06-19
Hey all, I've been searching around the forums for a way to disable the ATI mobility 5650 on my HP Envy 14 with very little success.  I really have very little use for it outside of gaming in Windows and it heats the laptop up considerably and certainly burning a lot of battery power.  I'm not using the proprietary ATI driver and just looking for something to turn the ATI card off and only use the integrated Intel chip when using Ubuntu 11.04 64-bit (have dual boot setup with Win7-64).  I'm completely new to Ubuntu/Linux and really love it for everyday computing thus far but it seems if the ATI card is going to eat battery when not in use, it's not a viable mobile setup for me right now.  Any tips or help?

---

### Post by smashweights on 2011-06-20
solved own problem.  managed to install Catalyst 11.6 from ATI website using:

[http://ubuntuforums.org/showthread.php?'p=10805756](http://ubuntuforums.org/showthread.php?'p=10805756)

using hsoulen's terminal code.  now have access to switchable ATI graphics, requires restart to change but seems to only be running one GPU when Intel chip is selected so no more overheating!

---

### Post by jayfost on 2011-09-15
Could you elaborate a little more on this, the link you posted is blank, I have a HP Envy 17" 3D and i have the heat problem plus whenever i restart the machine is displays an error saying that the machine was shutdown due to over heating even though I shut down the machine manually

---

### Post by Dr_Deadmeat on 2011-10-14
> **smashweights said:**
> solved own problem.  managed to install Catalyst 11.6 from ATI website using:

[http://ubuntuforums.org/showthread.php?'p=10805756](http://ubuntuforums.org/showthread.php?'p=10805756)

using hsoulen's terminal code.  now have access to switchable ATI graphics, requires restart to change but seems to only be running one GPU when Intel chip is selected so no more overheating!

> **jayfost said:**
> Could you elaborate a little more on this, the link you posted is blank, I have a HP Envy 17" 3D and i have the heat problem plus whenever i restart the machine is displays an error saying that the machine was shutdown due to over heating even though I shut down the machine manually

If you're still interrested in this problem try this link: [http://ubuntuforums.org/showthread.php?p=10805756](http://ubuntuforums.org/showthread.php?p=10805756) (there was an extra ' in the link from smashweights

EDIT: Grammar errors

---

