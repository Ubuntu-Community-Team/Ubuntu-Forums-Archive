---
title: "GeForceGo 7300 low resolutions."
date: 2017-09-04
forum: Hardware
---

### Post by vorvalk on 2017-09-04
Greetings,

After a lot of research i can't see an answer for  this. I have a laptop with GeForceGo 7300 and proprietary drivers work  perfectly fine in Linux Mint 18.2. Though I have dual boot and tried the exact  same  drivers in any flavor of 16.04 LTS Ubuntu, after install and reboot I only  have available low resolutions. Have read about xorg.conf in Foruns but I  cant fix or realize why the same kernel and the same driver version  works on Mint but not Ubuntu (Ubuntu, Ubunto GNOME, UBUNTU MATE and  Xubuntu tested). Any optimization that must be done after NVIDIA drivers install that mint may have been doing out-of-the-box?

Thanks in advance

---

### Post by Autodave on 2017-09-04
Where are you getting the driver for the Nvidia card? What driver are you installing?

---

### Post by Autodave on 2017-09-04
According to the website, the 304 driver is the newest one that can be used.  I have found (in the past) that sometimes a newer version can be used, but generally their website is accurate.

---

### Post by vorvalk on 2017-09-04
The driver is the same that is suggested in "Additional drivers" 304.135. The same as if i sudo apt install nvidia-current. I have also tried sudo apt install nvidia-current-updates which didn't solve the problem.

---

### Post by Autodave on 2017-09-04
I am assuming that you have gone into the Nvidia display panel and tried? What resolutions does it show available to you? What is the largest one that you can choose?

---

### Post by vorvalk on 2017-09-04
The highest one is 1024x768. My lcd native is 1280x800 and it works well with the open source drives. In NVIDIA settings panel no resolution is available only in "Displays" section (Xubuntu this case).

---

### Post by Autodave on 2017-09-05
In the Nvidia control panel (Settings -> Nvidia X Server Settings -> X Server Display Configuration) you should be able to choose the proper resolution.

---

### Post by vorvalk on 2017-09-05
No available resolutions at all in NVIDIA settings. I figured out something, though: in a last effort I downgraded kernel back to 4.8 and it worked. So the driver in repository may not be compatible with the newest kernel. This was the kernel shipped with Xubuntu 16.04.2.

---

### Post by Autodave on 2017-09-05
Good job!  Please remember to mark the thread as SOLVED. You can do that from the top right corner under THREAD TOOLS.

---

### Post by vorvalk on 2017-09-05
Somehow I also found there is a patch available for those driver in newest kernel. (Not pasting the link because I don't know if it's against the Forum rules). Anyway, I tried that patch but couldn't get it installed. Know if there is that patch in Ubuntu repositories or any ppa available for it?

---

