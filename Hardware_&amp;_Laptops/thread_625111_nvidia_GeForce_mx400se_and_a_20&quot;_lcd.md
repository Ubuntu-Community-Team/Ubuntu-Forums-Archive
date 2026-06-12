---
title: "nvidia GeForce mx400se and a 20&quot; lcd"
date: 2007-11-27
forum: Hardware &amp; Laptops
---

### Post by cronk on 2007-11-27
JUst wondering if anyone has done this under ubuntu or linux for that matter. I'm currently running the old GeForce mx440 just fine but with an equally old 17" CRT.
Getting an LG 20" wide screen LCD in a couple of day and need to be able to set the resolution to 1680 x 1050 . I've checked the specs out on a fwe sites and it looks like I may be able to do it.  Obviously perrformance will siffer a bit but its only temporary until I get the rest of my nerw PC.
If anyone has any experiences with the mx440 I'd love to hear about it.

Thanks.

---

### Post by njparton on 2007-11-27
I run this card at work with that resolution but under Win XP Pro.

It's fine for office 2D stuff like spreadsheets and word processing but I imagine video etc would be an issue.

Stick with nVidia for best linux support for your upgrade :wink:

---

### Post by cronk on 2007-11-27
Thanks man, 
Yeah I didn't figure I'd be able to do much with it in the way of gmes, vieo , etc. Just need to put up with htis old system for a few more weeks and then I'll have a new one. 
Glad to hear I can run it with that resolution, I'm sure it will work under Linux as well.

Thanks again.

---

### Post by cronk on 2007-11-28
Wondering if anyone could tell me how set a custom resolution with Ubuntu 7.10 and the latest nvidia driver?

---

### Post by njparton on 2007-11-30
You'll need to edit your Xorg.conf file and restart X. I think it sits under:

/etc/X11/Xorg.conf

or somewhere under the /etc... directory in a place used by X server.

---

### Post by cronk on 2007-11-30
Thanks again!

---

### Post by cronk on 2007-11-30
OK, I am having a look at my xorg.conf file and not sure what or where to add a custom resolution.

I can see the settings for my card in there but I don't know what to add to it to get 1680 x 1050? 

Any help is appreciated, in the meantime I'll keep searching for a resolution.

Thanks.

---

### Post by njparton on 2007-12-01
Make a copy of the block that includes your current resolution, paste it in below and change the settings to what you require.

Reboot or restart x and your new settings should be available to select.

---

### Post by cronk on 2007-12-04
Thanks so much for all your help, I was able to change the resolution just by doing gksudu nvidia settings and then selecting the correct resolution.

Thanks again.

---

