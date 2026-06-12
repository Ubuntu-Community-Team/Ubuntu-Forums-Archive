---
title: "hooking laptop to tv problems"
date: 2012-05-09
forum: Hardware
---

### Post by bigern26 on 2012-05-09
Hello all, 
I am new here and a total newbie to Ubunu. I installed the newest version to my laptop after have problems for the last 4 years with vista. So far I am totally happy with it. I have gotten everything to work perfectly 
except for hooking the laptop to my HDTV. Laptop is a dell inspiron E1505. Tv is a new LG, 
I got a vga to hdmi cable hooked it up along with an audio cable. When I got to screen settings it does not show or recognize any other screen and my tv just says no signal. I have searched ad tried a few different thing but nothing works. 
Is there a trick to this? 
My video card is an intel. 
my tv does have a VGA port do I need to hook up that way instead of the VGA to HDMI?

This is really stressing me out LOL 

Thanks in advance for any help.

---

### Post by sammiev on 2012-05-09
Mine worked right out of the box. Have you checked your bios settings to confirm you have the out put to a second monitor or so on turned on?

Also, Welcome to Ubuntu bigern26. :)

---

### Post by SeijiSensei on 2012-05-09
You can switch between the laptop display and the TV using Fn-F8 on most Dell laptops.  I'd try using the VGA ports first if you have a VGA cable available and see how that works.

---

### Post by bigern26 on 2012-05-09
> **sammiev said:**
> Mine worked right out of the box. Have you checked your bios settings to confirm you have the out put to a second monitor or so on turned on?

Also, Welcome to Ubuntu bigern26. :)
Not sure how to do that.

> **SeijiSensei said:**
> You can switch between the laptop display and the TV using Fn-F8 on most Dell laptops.  I'd try using the VGA ports first if you have a VGA cable available and see how that works.
I did hit Fn-F8 but it did nothing.

---

### Post by papibe on 2012-05-09
Hi bigern26. Welcome to the forums.

Have you tried setting the TV using the application 'Monitors'? If not, look for it on the dashboard (the application search bar).

Regards.

---

### Post by bigern26 on 2012-05-09
> **papibe said:**
> Hi bigern26. Welcome to the forums.

Have you tried setting the TV using the application 'Monitors'? If not, look for it on the dashboard (the application search bar).

Regards.

Tv has no choice, just port choices, The only thing I can find on the computer is System Settings>Displays, and it cannot recognize anything other than the laptop screen.

---

### Post by smuthavarapu on 2012-05-10
Check this post

[http://ubuntuforums.org/showthread.php?t=1969572](http://ubuntuforums.org/showthread.php?t=1969572)

Check your graphics cards, i think there are two graphics. In BIOS, force to use ATI graphics card.

---

### Post by bigern26 on 2012-05-10
i dont think i have 2 video cards, i cannot find monitor settings in bios

---

### Post by ahallubuntu on 2012-05-10
I have an old E1505 that I could probably revive temporarily and plug it into my TV and see how it works for you.  I have a Ubuntu 12.04 live USB stick I could boot on it.  Mine also has the integrated Intel video and not a separate video card.  I don't recall any special video options in the BIOS.  Dell BIOSes are usually pretty minimal.

There is a Fn key on the keyboard to toggle display modes though as I recall - between the external and internal displays.  I'll have to play with it later and report back to you.

---

### Post by bigern26 on 2012-05-10
That would be awesome. This thing is really stressing me out. 
The Fn key and F8 is doing nothing for me at this point.

---

### Post by smuthavarapu on 2012-05-11
[http://support.dell.com/support/edocs/systems/ins6400/en/om/specs.htm#wp1074455](http://support.dell.com/support/edocs/systems/ins6400/en/om/specs.htm#wp1074455)

[http://ubuntuforums.org/showthread.php?p=11298458#post11298458](http://ubuntuforums.org/showthread.php?p=11298458#post11298458)

Is your laptop different that those, both links suggest me that 1505 has two graphics card.

If you have same laptop, check if you can upgrade bios to do the Graphics card settings

If I am wrong, ignore me, i hope you solve your issue soon :-)

---

### Post by ahallubuntu on 2012-05-11
The E1505 has only one video card, but as an option it had EITHER the Intel integrated video card...OR...the ATI discrete video card.  Not both.

---

### Post by ahallubuntu on 2012-05-11
OK, I hooked my E1505 up to my TV.  I don't have an HDMI adapter.  My TV like yours has a VGA port so I hooked it up with a VGA cable.  It automatically worked - I get a clone of my laptop screen on the big screen or I can extend my desktop to include the TV as the second display (I can choose that from display settings in Ubuntu).  On the downside: it can only display at 1024x768 on my TV (without the TV attached, I can get 1280x800 native).  When I tried to switch the TV to 1280x800, it said it wasn't possible and offered that I might re-login in "2D mode" but I didn't try to do that from the live CD.

I don't have a 32 bit version of 12.04 LTS handy - and my E1505 has only a 32 bit CPU, so I couldn't boot up 12.04.  I booted a 11.10 live CD instead.  Not sure if 12.04 would be any different for you.  I doubt it.

Fn+F8 definitely toggled between the options (Laptop LCD only, TV only, or both).  My TV would in fact switch modes (loud "click" on my plasma TV) each time I hit the key combo.  If yours does nothing, I suspect it simply does not detect any display attached via your HDMI adapter.  So: I'd get a VGA cable and connect up sound separately from the headphone jack with another cable to the TV's audio inputs.

There is no display option in the BIOS to adjust anything except "expansion" - that is, the ability to display higher resolutions on the LCD than native resolution.

If you can display only at 1024x768 that's not good: that's more square than a 16:9 TV and a little stretched, so pretty useless for watching TV.

If possible, though, I highly recommend rigging up a dedicated desktop tower as a media center and just get an HDMI card or get a motherboard with built-in HDMI.  I have a couple of boxes like this that I built with Ubuntu for my TVs and they work well.  Passively-cooled HDMI PCI-E video cards (bad for gaming but fine for video playback - and quiet) can be had cheaply on sale for as cheap as $10 after rebate.  I use a wireless mouse to control mine and have everything I want to watch bookmarked so I rarely use a keyboard (I can just do remote desktop from my laptop when needed for that).  Sadly, the E1505 isn't really designed for use with a modern TV, despite the fact that it was sold with MS Media Center.

---

### Post by bigern26 on 2012-05-13
Ok I got this figured out, I cannot use a VGA to HDMI cable. 

I picked up a VGA cable and it works perfect, I can shut the laptop screen off and it comes up on the tv or I can mirror monitors and its up on both. Perfect resolution and everything. 

Thanks all for the help!!

---

