---
title: "Problem with my external hard drive"
date: 2009-12-12
forum: Hardware
---

### Post by Breckan on 2009-12-12
K this is a strange problem. I have had this portable hard drive for over 6 months now and seems to have worked just fine until recently where it appears to have stopped being reconised?!?! I normally plugged it in and it made a little "ding" noise where it would come up as noticed as being plugged in but now although the light on the back of it is on and it makes the same "ding" noise when its plugged in, I don't recieve anything and am not able to find any trace of it. When I click on what I used to click on it on desktop to open it it just comes up as "error cannot be found" and there is not sign of it in my computer. Its as if that extra hard drive never existed. 

Is there anything I can do to check the hard drive? I mean anything to get it open to even look into it to begin with? I cant think why it has suddenly done this and its worrying seeing I have a lot of important coursework on there but i'm suspecting it has become corrupted somehow. Can anyone help me here pls oh and i have tried it on my fathers laptop and it is not reconised there either. Pls someone give me a hand here . [IMG]http://www.suggestafix.com/style_emoticons/default/wacko.gif[/IMG]  [IMG]http://www.suggestafix.com/style_emoticons/default/wacko.gif[/IMG]  [IMG]http://www.suggestafix.com/style_emoticons/default/wacko.gif[/IMG] . Ty.

---

### Post by Breckan on 2009-12-12
Pls someone reply and help me sorry this is just very important.

---

### Post by paulisdead on 2009-12-12
I take it you've tried plugging it into different ports?  What is this a USB drive?

Try this, open up a command line, and type in "dmesg" without the quotes.  Then plug the drive in, and do "dmesg" again.  You can then see if the drive's at least getting detected, and assigned to device in the /dev directory.  If it comes up, you can then try to manually mount the device from the command line.

Have you tried plugging the drive into another computer?  Does the drive actually show signs of being powered on when you've got it hooked up?  Like power lights, you can feel the drive motor spinning, etc.

If it won't show up at all, on this computer, and another, and you're feeling adventurous, you could try to remove the drive from it's enclosure, and plug it right into your motherboard.  It's probably just an ide or sata drive inside there, and might be pretty easy to open up and get at.  It could just be the USB to sata/ide bridge is hosed, or even something to do with the power in the enclosure, and the drive itself might be fine if you removed it.  This might not be easy to do, depending on the drive, and probably voids the warranty.

---

### Post by Breckan on 2009-12-12
> **paulisdead said:**
> I take it you've tried plugging it into different ports?  What is this a USB drive?

Try this, open up a command line, and type in "dmesg" without the quotes.  Then plug the drive in, and do "dmesg" again.  You can then see if the drive's at least getting detected, and assigned to device in the /dev directory.  If it comes up, you can then try to manually mount the device from the command line.

Have you tried plugging the drive into another computer?  Does the drive actually show signs of being powered on when you've got it hooked up?  Like power lights, you can feel the drive motor spinning, etc.

If it won't show up at all, on this computer, and another, and you're feeling adventurous, you could try to remove the drive from it's enclosure, and plug it right into your motherboard.  It's probably just an ide or sata drive inside there, and might be pretty easy to open up and get at.  It could just be the USB to sata/ide bridge is hosed, or even something to do with the power in the enclosure, and the drive itself might be fine if you removed it.  This might not be easy to do, depending on the drive, and probably voids the warranty.

Yeh I not sure how to do the dmesg command line thing lol how do you do that??! sorry. 

Yes I tried using the device (its usb) in my dads laptop but there was no response at all that it was there which is worrying. The drive does seem to show signs of being powered on as the light at the back of it comes on and does not flicker at all and I can hear it whirring. 

If it is corrupted somehow, which I suspect, could I use some type of software to somehow access it to salvage the stuff on it? is there anything you reccomend? thx.

---

### Post by Breckan on 2009-12-12
anyone? sorry to keep on with this but it important to me.

Is it possible i've lost it all if there is some damage on the hard disk?

---

