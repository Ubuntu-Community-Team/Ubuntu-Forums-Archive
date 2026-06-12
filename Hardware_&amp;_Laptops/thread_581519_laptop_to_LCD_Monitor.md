---
title: "laptop to LCD Monitor"
date: 2007-10-19
forum: Hardware &amp; Laptops
---

### Post by sophtpaw on 2007-10-19
Hello 

I hope someone can help me with this. I want to be able to plug svga cable from laptop and hook it up to my Samsun LCD television (26") for obvious reasons. Either so i have both screens going simultaneously (ideally) or tranfer it to television if hooked up fullstop.


I have a Lenovo R60e with Intel Pro gma(s)? 945 Integrated graphics card

Gusty works great on it except for the middle scroll but that is a different story. I put the vga cable to the Samsung set it to pc but the television goes blank.

I wondered if anyone could tell me/help me set this right if possible. Interestingly my Desktop work on the Samsung lcd television out of the box. All i do is take vga cable off pc monitor and put it on the back of the television, set it to pc and its there... and that has some kind of integrated graphics on an asus (barebone) motherboard too. Agues, laptops are slightly trickier.... Most of the time its fine but for watching movies its nice to know i can hook it up to a television and get it on the 'big' screen

Many Thanks in advance,

--
sophtpaw

---

### Post by sophtpaw on 2007-10-19
bump

---

### Post by sophtpaw on 2007-10-20
can no one help me with this question?

---

### Post by monoufo on 2007-10-20
you have to configure your laptop to be able to do this.  You can try using the buttons on it, or try doing it in software like the new gui they added to do this.  The laptop needs to know that you plugged something in and want to use it, it's not automatic.  You really never tried this before?

---

### Post by sophtpaw on 2007-10-21
> **monoufo said:**
> you have to configure your laptop to be able to do this.  You can try using the buttons on it, or try doing it in software like the new gui they added to do this.  The laptop needs to know that you plugged something in and want to use it, it's not automatic.  You really never tried this before?

I did try this before but on or rather with my Desktop and all i had to do was take the vga? cable out of the monitor and hook it up to the television use the television remote to go to pc and it was just there. So, you could say it worked out of the box and didn't need telling that i plugged something in.

But with the laptop i get a blank. Also this was with Feisty Fawn. It seems no as straightforward even with the Desktop on Gutsy Gibbon. I wonder if this feature is somewhat broken in Gutsy compared to how it worked in 7.04

Anyhow,i digress; you say i have to configure the laptop to recognize i've plugged something in.... how do i configure the laptop to recognize LCD television?

what buttons? I saw no gui that jumped out at me saying use me to configure your laptop to read external monitors. I have done this with xp on this laptop but saw no such gui in Ubuntu Gutsy. I went #ubuntu but i was advised to go to the forums, but it seems hard to get support on this and all other threads i've found don't relate specifically to my hardware.

---

### Post by aardwolfsgp on 2007-10-21
Try manually setting the external monitor frequency to 60Hz, if possible.

---

### Post by monoufo on 2007-10-21
the reason it works with desktops is the graphics card is constantly sending the signal through your VGA cable.  The desktop doesn't care what monitor you hook it up to.  with laptops, the VGA port needs to be turned on.  I'm surprised you never tried doing this before with any type of TV out, projectors, etc.  But everyone has a first time for everything.

I believe most laptops have buttons for this, whether they work or not is a different issue.  on my laptop I'd have to press Fn and F7.  check out all the little pictures on your Functions keys.

the GUI i was referrinf to in Gutsy is in Administrations --> Screens and Graphics.  Mess around in there and you should be able to get it to work.  It will reconfigure your xorg.conf and stuff.  I can't get Tv out to work on mine, the drivers don't cover that feature.  i never tried using VGA out.  my dad's big screen takes HDMI, not VGA.  I could try with my 19" CRT but i don't even have that on a desk right now.

Good luck.

---

