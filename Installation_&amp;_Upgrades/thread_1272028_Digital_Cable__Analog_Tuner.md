---
title: "Digital Cable / Analog Tuner ?"
date: 2009-09-21
forum: Installation &amp; Upgrades
---

### Post by cat2005 on 2009-09-21
I have a question so simple that I am embarassed (sp?) to ask, but will ask regardless:
 
*Could my analog Hauppauge PVR 150 tv tuner make use of the digital cable signal I receive?*
 
My guess is "no" but I wanted to see what others had to say.  
 
If not, then what type of card would I need?  Any recommendations for good linux support?  
 
I have this card in my ubuntu box now and could not get the following to run cable tv:  vlc, tvtime, metv.  Mythtv crashed my system once, so I am afraid to try it again.
 
/ 128 mb nvidia something graphics card
/ p4, 2.4 ghz
/ 1 gb ram 
/ ubuntu 9.04
 
Thanks.

---

### Post by StuartN on 2009-09-21
> **cat2005 said:**
> If not, then what type of card would I need?  Any recommendations for good linux support?

No, it will not work. Try the MythTV project to check which cards are supported - [http://www.mythtv.org/wiki/Video_capture_card#Cards_tested_with_MythTV](http://www.mythtv.org/wiki/Video_capture_card#Cards_tested_with_MythTV)

---

### Post by cat2005 on 2009-09-21
> **StuartN said:**
> No, it will not work. Try the MythTV project to check which cards are supported - [http://www.mythtv.org/wiki/Video_capture_card#Cards_tested_with_MythTV](http://www.mythtv.org/wiki/Video_capture_card#Cards_tested_with_MythTV)


StuartN, et al:

Thank you, that is what I thought.  

However, I have another question.  To set it up:  When I ran windows XP on this same box, I made very basic use of the card.  By "very basic" I mean I simply connected the cable from the wall into the card, clicked the "winTV" icon (or whatever icon it was) and could watch TV.  I never tried to do anything fancy, like record, skip commercials, etc, but I could watch TV.

I had the same digital cable back then (1 week ago).  Do you have any thoughts as to why it provided basic viewing in Windows but not Linux?  Everything is the same, except the OS.

Sorry if the answer is obvious to you and others, but I am certainly a "fish out of water" on tech topics like this.

Thanks again for your time.

---

### Post by StuartN on 2009-09-22
> **cat2005 said:**
> Do you have any thoughts as to why it provided basic viewing in Windows but not Linux?

At a guess, I would say your cable supplier pipes both analogue and digital TV down the same wire. Try tvtime in Linux, which should work with your card and should autotune to the available channels.

---

### Post by cat2005 on 2009-09-22
> **StuartN said:**
> At a guess, I would say your cable supplier pipes both analogue and digital TV down the same wire. Try tvtime in Linux, which should work with your card and should autotune to the available channels.


Unfortunately, I can not use TV time.  My card is one specific card TV time does not support.  I even tried myself.  I also tried vlc and metv.  Both failed.

---

