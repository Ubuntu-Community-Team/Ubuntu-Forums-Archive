---
title: "Thinkpad screen stuck after lid close"
date: 2007-03-04
forum: Hardware &amp; Laptops
---

### Post by vicarious on 2007-03-04
I have a Thinkpad T41 with a Radeon 7000 mobile (uses open-source radeon driver). When the lid close button is pressed the screen turns black. When I open the lid, the screen will not come back on unless I switch to a TTY and then back to X. Every once and awhile the screen will come back scrambled after this and I have to reboot.

I tried 'xset dpms force off/on' manually and it worked fine.

I disable all power management settings. Screen still got stuck, it had no effect.

I commented out the entire /etc/acpi/lid.sh file. It had no effect.

I **stopped the acpid, acpi-support** and apmd daemons. It had no effect.

I don't know where to go next. **What is blanking my screen if it is not acpi**?! I have never had a problem in the past with other distros on this laptop so I know I can get this to work.

---

### Post by defenestratos on 2007-04-24
Yeah, I have the same problem on my Benq Joybook (camp name I know). I shut the lid and on opening is nearly totally black but if you look really carefully you can see the login window through the gloom.
It would be good to get it going, does anyone have any thoughts?

---

### Post by Sunflower1970 on 2007-04-24
Have a similar problem with a Thinkpad R40 using Feisty. Decided to go back to Edgy since I had no problems with suspend there.

---

### Post by tschneiter on 2007-04-24
Occasionally on my lappy (dell 640m) I get a black screen after re-opening the lid. I find that shutting it and re-opening it fixes things. Possibility?

Also, check your power-manager settings to see if it blanks on shut; though I suppose if acpi is off, that shouldnt make a difference...

---

### Post by strabes on 2007-04-24
Check out this page: [http://www.thinkwiki.org/wiki/ATI_Mobility_FireGL_V5200](http://www.thinkwiki.org/wiki/ATI_Mobility_FireGL_V5200)

---

