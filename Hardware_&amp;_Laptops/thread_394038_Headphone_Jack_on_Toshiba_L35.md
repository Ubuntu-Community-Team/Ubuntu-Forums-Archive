---
title: "Headphone Jack on Toshiba L35"
date: 2007-03-26
forum: Hardware &amp; Laptops
---

### Post by airencracken on 2007-03-26
Despite searching the forums and replying to several threads I have yet to find a solution to the particular issue I'm having (and a lot of other Toshiba Satellite L35-S2171 owners as well). Basically pretty much everything works on the laptop out of the box (even the dreaded ATI M200, though I have yet to get XGL/Beryl working on it, mostly out of laziness). Probably the only thing that doesn't work is my front headphone/microphone jacks. Although they aren't necessary, it'd be really nice to have them working so I could use headphones while I did my work on my laptop in public places. Granted I could normally use my iPod or something like that, but that also means I'm not getting any audio notifications from the computer and I can't use VOIP. Again, not a huge deal I suppose, but since it's pretty much the only one I have (on my laptop, desktop is another story, but of course I'm attempting much more complicated stuff there...) it bothers me. Any suggestions?

Running Edgy with all updates installed as of March 26, 2007.
Toshiba Satellite L35-S2171

---

### Post by s0cket on 2007-03-26
Does it work in Windows?  Generally speaking I thought that was completely hardware controlled.  When you plug in headphones the soundcard should see that and turn off the speakers and shuttle the sound out the "phone plug".

---

### Post by airencracken on 2007-03-26
Yeah it works fine in Windows, everytime. Other people seem to be having the same problem as well, which leads me to believe that it is an ALSA/Driver issue.

---

### Post by Blaster95 on 2007-03-30
I'm having the same problem with the same kind of laptop.

---

### Post by airencracken on 2007-03-30
Yeah it seems like a lot of people are having the same problem. I have yet to see anything that resembles a solution though.

---

### Post by naxmul on 2007-04-05
same problem here, with the same model, but with dapper.

oh btw, XGL/Beryl works perfectly, you should really get around to installing it =P

---

### Post by Corwin7 on 2007-04-08
I have a Toshiba Satellite L35-S2171 and am having the same headphone jack issues. I used module-assistant to compile ALSA but it failed!?! WTF!?! I'll probably install a real copy of Debian on this laptop, the installation on kubuntu is really slick but I don't think it's worth having a half *** broke version of Debian where module-assistant doesn't even work. The Atheros Wifi doesn't work on the laptop either. Madwifi drivers work great on my Debian desktop. I'm really surprised how bad kubuntu is on this laptop. I could easily see the headphone issue being a BIOS/hardware problem, but a broke m-a and non working Atheros drivers is not going to cut it.

---

### Post by Awalton on 2007-04-13
Same problem, same laptop, doesn't work with Dapper, Edgy or Feisty (and Feisty's ATi/Intel HD Audio driver in the most current kernel (all >2.6.20-9 for me) is borked and doesn't output any sound at _all_).

I've alerted the Ubuntu kernel team, but I haven't moved upstream to ALSA yet (and I'm still poking through to see what the heck is up).

---

### Post by naxmul on 2007-04-13
> **Awalton said:**
> Same problem, same laptop, doesn't work with Dapper, Edgy or Feisty (and Feisty's ATi/Intel HD Audio driver in the most current kernel (all >2.6.20-9 for me) is borked and doesn't output any sound at _all_).

oh man. i thought somehow, the newest release would make it work. =\

---

### Post by manny0 on 2007-04-21
having no sound at all ROCKS!!! im going to exchange this laptop at work for a new dual core machine next week im so tired of it. not working with linux.

---

### Post by airencracken on 2007-10-12
I'm really hoping that this issue is finally fixed in Gutsy. I must say this and the lack of support for the video on this particular laptop (for compiz) are both very dissapointing.

---

### Post by airencracken on 2007-10-19
> **airencracken said:**
> I'm really hoping that this issue is finally fixed in Gutsy. I must say this and the lack of support for the video on this particular laptop (for compiz) are both very disappointing.

Nope. Still doesn't work. It does however mute the speakers which is a nice change.

---

### Post by airencracken on 2008-07-09
Still doesn't work for Hardy.

---

