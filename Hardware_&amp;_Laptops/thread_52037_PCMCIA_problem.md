---
title: "PCMCIA problem"
date: 2005-07-26
forum: Hardware &amp; Laptops
---

### Post by saat on 2005-07-26
I start the Ubuntu installation on my laptop ("no name" laptop) and when it comes to the point where I have to decide whether to enable or not the PCMCIA port, I choose yes but I do not give any additional commands that may be needed. After that the progress bar remains at 98% until ofcourse I reboot or shut down the pc. Is there any specific way to solve the problem? Any type of installation guides or maybe something more specific about PCMCIA? If anybody has any idea please tell me because it is a kind of an emrgency to set up Ubuntu...

Thank you in advance.

Saat

---

### Post by Ambugaton on 2005-08-07
I'm having some pcmcia troubles too... I have a D-Link dwl650 and I already ndiswrapped the driver for it off the installation cd. I've been looking around since yesturday and I think I've come to the conclusion that the only problem I'm having is that the laptop wont supply power to the PCMCIA socket when the laptop boots up ](*,) . Does anyone have any ideas as to what I should do, maybe a few steps or something to get power to the pcmcia socket? Any help would be appreciated.

---

### Post by catchpolemartin on 2005-08-08
What kind of laptop is it?
Ive solved the same prob on my thinkpad 600 by disabling the power management of the pcmcia slots.

---

### Post by Ambugaton on 2005-08-08
Its an Averatec 3200 Series. Do I need to apt-get install any power managements tools in order to fix it?

---

### Post by hypnos on 2005-08-09
Launch the installation using this parameter ```
 hw-detect/start_pcmcia=false
```

---

