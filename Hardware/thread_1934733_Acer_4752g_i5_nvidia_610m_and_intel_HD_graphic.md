---
title: "Acer 4752g i5 nvidia 610m and intel HD graphic"
date: 2012-03-02
forum: Hardware
---

### Post by meer418 on 2012-03-02
have an ACER laptop, model:4752g i5 with a  intel(R) HD and a Nvidia 610M 1GB graphic cards. 



After installing UBUNTU  11.10 and 12.04 the system information shows "GRAPHIC: UNKNOWN" and the  photos are not displayed properly. 



Would like to know whether there are  graphic drivers for these cards? as it appears that this laptop has two  graphic chips (according to the information provided in windows 7  device and driver information)


 -If these cards are new, will Ubuntu team or Linux team will come up with proper drivers for these cards?
 -Is there any compatible drivers in existence which I could take advantage of to make the system work properly?


 Best Rgds

---

### Post by avejidah on 2012-03-30
I have nearly the same laptop: Acer AS7739G-6676.  It has the 610m video card, which has been very problematic.

[LIST=1]
[*]Using the 11.10 Desktop edition, the install hangs.
[*]The alternate install CD completed fine.  Afterwards, I cannot boot into the system - I get a flashing cursor then a black screen.  Disabling quite and splash shows Running init-bottom... then a black screen with no backlight.
[*]I can boot up by adding nomodeset in the grub configuration.
[*]After booting, the resolution is set to 1024x768, and wont let me increase using Display.  Jockey shows no proprietary drivers in use, and none available.  I tried installing nvidia-current, and running nvidia-xconfig, then restarting lightdm, but after that lightdm will not start.  I also tried downloading the nvidia 610m driver from nvidia's web page.  After installing this driver and running nvidia-xconfig, I get the same problem.  The system hangs at "Starting the deferred execution scheduler."
[/LIST]

I'm not sure what to try from here. Any help is appreciated.  Thanks!

---

