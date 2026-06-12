---
title: "A cautionary tale about Ubuntu, a ThinkPad, and Suspend mode"
date: 2009-05-06
forum: Hardware
---

### Post by redfrog07 on 2009-05-06
This post is not so much to report that suspend mode did not work properly for me on a ThinkPad laptop computer as it is to offer hope to those poor souls who, like me, fear they may have "bricked" their trusty companion.

Normally I don't use "suspend" or "hibernate" modes. Maybe it's my many years of using computers that didn't offer those modes. Also, I know that these modes can be problematic, especially under Linux. Just look in these forums for proof. Anyway, I had just installed Jaunty (9.04) Ubuntu on my IBM R51 ThinkPad and it seemed to be working pretty well. So when I called it quits for the evening one night last week, I decided to see how suspend mode worked with this new distribution, invoking it from the shutdown menu. Big mistake!

When I went to use the computer the next morning, I couldn't get it to "wake up". I tried power cycling, tried holding the power button down for more than 10 seconds, tried removing the battery, tried booting from CD, tried booting from a Knoppix USB flashdrive. The results were always the same - on power up the CAPS and NUMLOCK LEDs would flash, the power and battery LEDs would remain on, and the fan ran. However, the screen remained blank and the keyboard was dead. It never got to the stage of displaying the IBM logo.

I searched the web from another computer to see if there was any help there. Although they worried me at first, I was able to dismiss the ignorant "Dude, your mobo's fried" posts. I really didn't believe I had damaged any hardware. The computer was simply stuck in a mode I couldn't get it out of. I read many posts about removing the battery and leaving it out for a long period of time. I tried four hours, then 24 hours, then three days. No joy. I read several posts about various combinations of pressing the on/off button with the battery out - "ten times at one second intervals, then hold for 90 seconds", "hold down for two seconds, release, repeat ten times, then hold down for 12 seconds", "hold down for two minutes", etc. Nothing seemed to work. If someone had said waving a dead chicken over it had worked for them, I probably would have tried it.

Today, five days later, I decided to try disconnecting the small lithium battery that keeps the CMOS RAM alive. It **does** exist by the way, despite several posts to the contrary. It wasn't easy to get to - I had to remove many screws and lift the keyboard bezel. Fortunately, IBM has excellent documentation (still available on the Lenovo site) on the whole process. After disconnecting the battery, I shorted the battery connector terminals on the board together using a small screwdriver, just for good measure. I reassembled the computer, reinstalled the main battery and crossed my fingers. When I saw the IBM logo, I knew my computer was back from the dead. I don't think I'll be trying suspend or hibernate again soon!

I offer this information in the hope that it will save someone else from the mental anguish I went through.

---

### Post by DavidCrow on 2009-05-06
9:15 PM
Dude,
You may have just saved me hours of work & hassle. My Dell E510 just did the same thing when I selected *suspend*. I'll be back with results shortly. Thanks for posting.

~ David

11:22PM addendum.

Yep - worked like a charm. Took the battery out for 5 minutes and put it back in. When I turned the power on - VIOLA - computer booted automatically into BIOS. So what if I had to spend 5 minutes re-setting all my BIOS settings.

I had spent an hour researching the problem at the Dell Forums web site from my wife's computer. By pure coincidence, I discovered to my horror that some owners of this desktop model (E510 or 5150) has a nasty history of displaying the same symptoms (blinking amber power button w seemingly dead computer) when hardware components have gone bad. I must have read 50 posts before deciding to do one more search on Google. I just couldn't believe that it was a coincidence that my hardware had decided to go bad at the exact moment I selected "Suspend Mode" form the Ubuntu 9.04 live CD. So I decided to add *Ubuntu* to one more Google search query and your "cautionary tale" was the very first Google return. And you had only posted it 5 HOURS EARLIER!!!! Amazing - no, really amazing!

Thanks again for saving me from the "mental anguish" you went through.

---

### Post by nbotticelli on 2009-05-06
That sounds horrible! Is there any kind of information as to what would actually cause this?

Also, I trust suspend more than I trust hibernate though I for the most part use neither, also since hibernate seems to be quite a bit more problematic on a lot of hardware, regardless of what OS you are running. 

Is there a relatively simple way of just completely disabling/removing hibernate as a feature? That way someone else who may use the computer doesn't put the laptop into hibernate when it may fubar a machine?

---

### Post by redfrog07 on 2009-05-11
> **DavidCrow said:**
> 9:15 PM
Dude,
You may have just saved me hours of work & hassle. My Dell E510 just did the same thing when I selected *suspend*. I'll be back with results shortly. Thanks for posting.

~ David

11:22PM addendum.

Yep - worked like a charm. Took the battery out for 5 minutes and put it back in. When I turned the power on - VIOLA - computer booted automatically into BIOS. So what if I had to spend 5 minutes re-setting all my BIOS settings.

I had spent an hour researching the problem at the Dell Forums web site from my wife's computer. By pure coincidence, I discovered to my horror that some owners of this desktop model (E510 or 5150) has a nasty history of displaying the same symptoms (blinking amber power button w seemingly dead computer) when hardware components have gone bad. I must have read 50 posts before deciding to do one more search on Google. I just couldn't believe that it was a coincidence that my hardware had decided to go bad at the exact moment I selected "Suspend Mode" form the Ubuntu 9.04 live CD. So I decided to add *Ubuntu* to one more Google search query and your "cautionary tale" was the very first Google return. And you had only posted it 5 HOURS EARLIER!!!! Amazing - no, really amazing!

Thanks again for saving me from the "mental anguish" you went through.
I'm glad I was able to spare you some anguish! Good thing I didn't wait any longer to post my message or you would have missed it. Hopefully others will be spared as well.

---

### Post by redfrog07 on 2009-05-11
> **nbotticelli said:**
> That sounds horrible! Is there any kind of information as to what would actually cause this?

Also, I trust suspend more than I trust hibernate though I for the most part use neither, also since hibernate seems to be quite a bit more problematic on a lot of hardware, regardless of what OS you are running. 

Is there a relatively simple way of just completely disabling/removing hibernate as a feature? That way someone else who may use the computer doesn't put the laptop into hibernate when it may fubar a machine?

I don't really know what caused the problem. Since these modes aren't really important to me, I'm not motivated to really dig into the problem. Perhaps someone else can shed some light on the problem.

As for disabling these modes, I found some good information here: [http://preview.tinyurl.com/o5l8lh]("http://preview.tinyurl.com/o5l8lh")   Although the info. was written for Ubuntu 6.0x, it worked great for me with Ubuntu 9.04. Hope that helps.

---

