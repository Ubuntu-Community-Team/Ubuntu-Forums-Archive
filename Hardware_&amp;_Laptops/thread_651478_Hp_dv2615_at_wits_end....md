---
title: "Hp dv2615 at wits end..."
date: 2007-12-27
forum: Hardware &amp; Laptops
---

### Post by setonb on 2007-12-27
My brother just bought a new laptop -- hp dv2615 to be exact.  And he really wants to switch to linux instead of vista, and I'm trying to help him, however the installation of Ubuntu has been very painful, to say the least.  

For some reason it seems as though gutsy keeps recognizing an nvidia network card(?).  I'm not sure what that's about...  But I am unable to boot from the livecd -- it keeps repeat the same startup scripts and can't get past the broadcom wireless issue.

So I switched to the Alternate cd, and it loads through, but comes again to the networking issue and even though I'm hard lined into a network it doesn't recognize it, it just keeps showing either the broadcom (which doesn't work) or the nvidia network (which to my knowledge is completely wrong...but it lists it as eth0)

I've tried both the 32-bit and the 64-bit and seem to get further with the 64-bit (which makes sense) but before this gets out of hand, I thought I'd come to the forums for help.

To add to my frustration, my technical support is being done through the phone because the laptop is in ohio --I'm in cali.  So it gets very frustration because my brother is not very technically savvy.  

The specs of the computer are:
Hp Dv2615nr
AMD 64 TL-58
Broadcom wireless
Nvidia 7150M 
2 GB Ram
100 GB Ubuntu partition...

Thanks for the help in advance.

---

### Post by Yellow Pasque on 2007-12-27
If you have an nvidia chipset, then you're going to have an nvidia-branded LAN port, so at least that part's okay. Sorry I can't help you more than that.

---

### Post by Yellow Pasque on 2007-12-27
Also, try disabling the wireless chipset in the BIOS.

Here's a post with similar hardware:
[http://ubuntuforums.org/showthread.php?t=575750&highlight=broadcom+nvidia](http://ubuntuforums.org/showthread.php?t=575750&highlight=broadcom+nvidia)

---

### Post by setonb on 2007-12-28
Ok, I read the guide -- everything seems pretty straightforward.  I'll call my brother tomorrow and give it a go -- Definitely let you know how it pans out.  Thanks for the speedy reply.  The only difference I can see between the two laptops is the screen size.  My brother's is 14.1" and that one is 15.4" but it shouldn't really matter, just a different resolution that the nvidia card should pick up.  Thanks again.

---

### Post by setonb on 2008-01-08
So I've tried to follow that guide, but I can't seem to get my brother past the graphics change.  We try changing it to Generic Monitor 1027x768 but the screen goes all cockeyed.  It's has like 4 mouses and is totally unusable.  
---we've tried a bunch of different monitor settings and none have worked --


Not sure what to do now.  I would love to try the rest of the guide, but I can't seem to get it past this graphics issue.  With the monitor at 800x600 the install process can't continue because we can't see the OK or CANCEL buttons.


Any help would be greatly appreciated.

---

### Post by setonb on 2008-01-16
Well, it worked!!!!   I'm so happy -- what we ended up having to do was delete the panel at the bottom and move the top panel to the side so he could just barely see the ok and nest buttons for the install.  once the install went through we adjusted the video correctly and everything was great!  Thanks for the tip on the tutorial -- many, many, many thanks!

Seton

---

### Post by Yellow Pasque on 2008-01-16
Glad to hear it. Enjoy.

---

