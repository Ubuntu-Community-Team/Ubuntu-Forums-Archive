---
title: "Ubuntu Migration-Monitor Problems"
date: 2006-01-16
forum: Installation &amp; Upgrades
---

### Post by johngrim03 on 2006-01-16
Hello, 

   A while back, I purchased a new monitor (NEC MultiSync LCD1935NXM), as it was capable of a resolution of 1280x 1024, I set that value via Suse's YAST2 Tool. The result was Suse booting but the screen remaining blank. I tried to configure the resultion manually via Sax2, but had no luck. 
 
  As Suse was not able to recognize my graphics card (ATI Radeon Xpress 200), four separate wireless internet adapters, and my sound card, I decided to scrap it in favour of Ubuntu. 

  After installing Ubuntu, the monitor issue presists. The computer boots, but I cannot get an image on my screen (and thus cannot complete the last phase of the installation).  

  I search around these forums and tried two suggestions that I found to be prevalent when this type of issue arises. 

   First, I tried to edit the monitor values via

"nano /etc/X11/xorg.conf"

That did not work

I then ran

"sudo dpkg-reconfigure xserver-xorg"

This seemed hopeful. However, when I tried to manually to change the values  set for the monitor, I was unable to delete first letter of the pre-set value 

For instance, if the HSync was set to 28.0-75.00, and I deleted that to enter the values for my monitor, I would get

2-----------------------

My rudimentary knowledge of computing suggests that leaving the "2" could cause a major problem.  

Is there any other to way to get the computer recognize my monitor? 

Thanks for your assistance. 

-johngrim03

---

### Post by johngrim03 on 2006-01-19
Ok, I ran sudo dkpg-recongifure xserver-xorg and just entered the values, ignoring the fact that I could not delete the first charachter of the present entries. And..It worked. No replies are needed.

---

