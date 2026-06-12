---
title: "strange little hibernate bug"
date: 2007-08-25
forum: Hardware &amp; Laptops
---

### Post by BradNeuman on 2007-08-25
I am running Kubuntu 7.04 on an ACER Aspire laptop and have had relatively few problems. I never tried to hibernate until recently because my swap partition wasn't big enough. Now iv'e got it set up and it works but there is a weird little bug. At first hibernate didnt work (USB error messages and it shut down but started up normally) so I added resume=/dev/hda5 to my menu.lst in grub and now it works.

Funny thng is, when I resume from hibernation the kubuntu loading screen comes up and the bar doesn't move and my power LED goes from greeen to blinking orange, which is what it looks like when the system is shutting down.  after a bit the system loads and everything seems to work fine but the light never goes back to green. I don't really care too much about my little LED but I was wondering if anyone knew the cause or if it could be a sign of something worse.

---

