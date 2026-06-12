---
title: "Backlight Failure While Using Gutsy LiveCD to Adjust Resolution"
date: 2007-09-28
forum: Hardware &amp; Laptops
---

### Post by SendDerek on 2007-09-28
So, I don't know if I should report this to launchpad or just make a general statement, but here goes...

With a fresh copy of the new Gutsy Beta LiveCD, I sucessfully made it to the main desktop on the Sony Vaio VGN-N325 laptop.  However, the screen resolution was wrong, so I went to make the change to 1280x800 (with the 85Hz refresh rate selected by default) using the Preferences->Screen Resolution tool.  It made a quick flicker and then nothing.  After a very close inspection, I can actually still see my cursor moving about the screen.  The short of it is, there's no more backlight.  From the moment you press the power button to the moment the OS (Windows or Ubuntu) boots up, there is absolutly no backlight.  In a word, it's 'busted'.

It could be just an issue with the laptop, but this seems awful strange.  The second I hit "apply" the backlight broke.  Was it the wrong refresh rate?  Can selecting the wrong refresh rate cause physical damage to the LCD?  I didn't think so before, but now I'm kinda wondering...  Am I an idiot for not knowing to set the correct refresh rate from 85Hz to 60Hz?

Suggestions?  Thoughts?

---

### Post by peabody on 2007-09-28
It definitely should not have broken your backlight, regardless of what you did.  Modern LCDs are good about being smart with the signal they're sent (they won't bother with it if they know it's something they can't deal with).

The question here is who's to blame:
1) Did your laptop's backlight just spontaneously break?  I find that unlikely.
2) Do sony's products suck by not dealing with improper input correctly (I find this very likely).
3) If Ubuntu did cause this, is it Ubuntu's fault if the manufacturer has sensitive products? (probably not, but if running Ubuntu can physically break your laptop in consistent fasion, the public should probably know about it).

Edit:  I just had a thought.  Did you try unplugging and removing the battery from your laptop for about 10 minutes?  I hear it's best to also hold down the power button during that time.  That should totally clear your laptop of any settings floating around in the hardware and reset them (with the exception of the cmos clock which should have a battery keeping it alive).

---

### Post by SendDerek on 2007-09-29
Thanks for the response.

 I seriously doubt that it was Ubuntu's fault.  I tried to be very careful to explain the situation as closely as possible without putting blame on Gutsy.  It does sound like this particular Sony was having issues.  Thankfully, it wasn't a computer of mine (or anybodies except the retail store) and it will be sent back to the manufacture with no productivity loss.  

I did have it unplugged for a time without the battery, but with no resolve.

It was just a very strange coincidence that it happened the moment I pressed the "Apply" button.  It's too bad that I can't try it again to see if the problem is persistent.  It was just surprising to see.  In all my years of computing and experience, it was crazy to see something like that happen.  But then again, computers surprise me everyday.

---

### Post by xerxian on 2007-10-14
I find the same problem happening whenever i change anything to do with brightness, and a reset doesnt fix it.

However i found that pulling the battery and ac will fix the backlight (until the next time something tries to change the brightness).

---

