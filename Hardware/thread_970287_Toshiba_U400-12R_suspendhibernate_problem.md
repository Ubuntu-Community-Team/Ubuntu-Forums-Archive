---
title: "Toshiba U400-12R suspend/hibernate problem"
date: 2008-11-04
forum: Hardware
---

### Post by MeanEYE on 2008-11-04
Hi, 

I am absolutly thrilled with 8.10 ubuntu. And have only this slight problem I'd really like to fix.

If I suspend my laptop or put it to hibernation, screen turns black, switches display to empty console screen with only cursor blinking and blocks. Only solution from here is to shut down my laptop and start it all over again.

It's been a while since I poked around apmd so I'd really like some help on this. You can imagine how important for laptop is to be able to go on standby.

Thanx

---

### Post by MeanEYE on 2008-11-11
Any sugestions???

---

### Post by uncrumbed on 2008-12-10
Sorry this is a late reply to an aging post. Probably irrelevant, but just in case it helps... I ran into a very similar prob on a SUSE Linux system on a laptop with pretty unstable ACPI (common thing I have read). In my case it happened when simply closing then opening the lid - the X server display always crashed. 

In my case the solution was making a small change in the settings at /etc/sysconfig. There were a couple of entries relating to power management events on lid open or close. The solution my case was to change to the lid close and lid open events from disply off (or whatever they were set to) to vt_switch instead. Apparently vt_switch told the X-server display to reset itself and cleanly recover on open and close instead of crashing. 

I realize Ubuntu and SUSE are different distros, I am just wondering if the issue is funky power management on systems built for MS Windows without regard to general stabilty... so maybe the fix could be similar? 

Please be aware I am a novice so this is nothing more than a thought!

Dunno if that helps at all, but best of luck!

---

### Post by MeanEYE on 2009-01-15
Thanx for replying... 

I think problem is ACPI related. Since the same thing happens if I try to go on standby manually without closing a lid. Am still waiting for solution tho and hope someone helps out...

After blocking I was able to see empty console screen (just blinking cursor) and everything else died. I couldn't even use my keyboard or anything else... Only hard reset could help!

---

### Post by mkarnicki on 2009-02-13
I've got an offtopic questin for you meanEYE, if I may. I'd like to by Toshiba Satellite U400-12R PSU40E-02203DPL, is your model relatively similar? If so, my question would be:

- how is it with wi-fi on Ubutu hardy on this model? does it work nicely? much effort needed or out of the box?

---

### Post by MeanEYE on 2009-02-13
Hi there... yes I have the same model... 

Well, linux works absolutely great on this machine. So far things I havent been able to make work are modem, bluetooth... and suspend... Everything came out of the box, so my initial tuning was all concentrated on compiz :D and wallpaper :)... 

Everything else is great. Wifi works like charm... All hotkeys are working (which surprised me greatly)... ooh, and my battery lasts at least half an hour longer under linux...

If you need anything else just ask...

---

### Post by mkarnicki on 2009-02-13
> so my initial tuning was all concentrated on compiz  and wallpaper ... 
I'd love to have such extreme tuning experience xD ! (my touchscreen once took a week ;) )

Thanks for being helpful, MeanEYE :KS ! This is some good news for me. We're buying a laptop for my aunts jewellery shop, and we needed something small, good looking, and handling linux nice (wi-fi most important). Then I shall contact you if I need any help ^-^ Thank you! :mrgreen: \\:D/

---

### Post by mkarnicki on 2009-02-25
Hello there!

MeanEYE, how should I properly boot into ubuntu installation? I'm having problems with wrong resolution (random strips, colours, etc)..

---

### Post by MeanEYE on 2009-02-25
> **mkarnicki said:**
> Hello there!

MeanEYE, how should I properly boot into ubuntu installation? I'm having problems with wrong resolution (random strips, colours, etc)..

Hm, never had a problem like that. Have you tried entering in save mode? There is a small help screen before booting and I think there's an option for VGA mode. Try and experiment... If you cant manage on your own, I'll try and see how can I help you...

---

### Post by mkarnicki on 2009-02-25
Instead of U400-12R they packed a better U400-14Z. That's why it didn't so swiftly as with yours :/ I wonder what I will do.. I'm trying with alternate CD now.

---

### Post by MeanEYE on 2009-02-25
> **mkarnicki said:**
> Instead of U400-12R they packed a better U400-14Z. That's why it didn't so swiftly as with yours :/ I wonder what I will do.. I'm trying with alternate CD now.

Can you please provide the laptop specs... Then I might be able to help.

---

### Post by mkarnicki on 2009-02-27
Hello ^ ^ ! Sure!

U400-14z

# Processor: P8400 (2.26)
# Processor type: Intel Core 2 Duo
# RAM: 3072MB
# HDD: 250GB
# Graphics: Intel GMA X4500HD

I'll go through the forums right now, it's obviously the fault of graphics, it's something else than in U400-12r. If I find something, I'll write here.

---

### Post by mkarnicki on 2009-03-03
Yay! Works with Jaunty 9.04 ^________^

---

### Post by smate on 2009-05-11
> **MeanEYE said:**
> Hi, 

I am absolutly thrilled with 8.10 ubuntu. And have only this slight problem I'd really like to fix.

If I suspend my laptop or put it to hibernation, screen turns black, switches display to empty console screen with only cursor blinking and blocks. Only solution from here is to shut down my laptop and start it all over again.

It's been a while since I poked around apmd so I'd really like some help on this. You can imagine how important for laptop is to be able to go on standby.

Thanx

I am having same problem with 9.04 on toshiba satellite U400D 107
any solution or advice? thx

---

### Post by MeanEYE on 2009-05-12
> **smate said:**
> I am having same problem with 9.04 on toshiba satellite U400D 107
any solution or advice? thx

Unfortunatly am in the same box with you... Still didnt find anything on this subject. Am kind of hoping they'll manage to fix it soon...

---

### Post by MeanEYE on 2010-01-04
*BUMP*

At one point (somewhere in the mid-summer) my suspend problem was properly solved, then a week later, new kernel update came and problem was back with it.

I was wondering did anyone manage to solve suspend problems on Toshiba?

---

