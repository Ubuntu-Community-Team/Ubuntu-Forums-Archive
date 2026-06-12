---
title: "HELP! Problem with Ubuntu 9.04 and tx2500: unable to boot after suspend"
date: 2009-06-07
forum: Hardware
---

### Post by ein4290 on 2009-06-07
hi everybody. i'm new to this forum. i would like to ask some things.
i have hp pavilion tx2500 notebook and recently i just installed the ubuntu 9.04
yesterday i was experimenting with my new OS.. and i accidentally press the suspend option.. i thought it will just go to standby or sleep mode. then i try to boot it up again, but it won't boot up! what do i have to do?? i would appreciate anyone help.. thx!

*sorry for my bad english*

---

### Post by kiridude on 2009-06-07
what happens when you turn off the power (with the power button) and then turn your computer on again with the power button? What do you see on your screen?

---

### Post by ein4290 on 2009-06-07
i see nothing.. just black screen.. not even a mouse pointer

---

### Post by Favux on 2009-06-07
Hi ein4290,

Sorry if I am stating the obvious.  I think your buttons are the same as my TX2000.

You slid the power slider button (on the lower left front) all the way to the right and held it until it made the "click" sound?  And it didn't power off?  You have to use the "slider" power button again, sliding it to the right to turn it back on.

---

### Post by ein4290 on 2009-06-07
> **Favux said:**
> Hi ein4290,

Sorry if I am stating the obvious.  I think your buttons are the same as my TX2000.

You slid the power slider button (on the lower left front) all the way to the right and held it until it made the "click" sound?  And it didn't power off?  You have to use the "slider" power button again, sliding it to the right to turn it back on.

yeah i did that. my notebook has been shutdown completely. but when i tried to turn it on again, i only see a black-empty screen.. oh and more information about the state.. the lamp indicating hard disk work is not shining.. but the light indicating caps and num lock repeteadly going on and off..
thx for your advice though!

---

### Post by Favux on 2009-06-07
Hi ein4290,

Are you able to get into the bios?

---

### Post by ein4290 on 2009-06-07
no.. i don't even see the HP logo when i turned it on.. or is there any other way to get to the BIOS?

---

### Post by Favux on 2009-06-07
Hi ein4290,

No you'd have to see the intial boot up with a few lines.

All I can tell you is plenty of TX2500 go into suspend in Jaunty without a problem.  We even have a script to reset their Wacom settings and calibration after suspend.

So it may/probably was a coincidence.

I would unplug it and take the battery out and let it sit for a good long while.  See if that "resets" it.

I hope that works but I'm wondering if there is a hardware problem.  Maybe you'll be lucky and something is loose somewhere.  Make sure the hard drive is properly connected after you let it sit.

---

### Post by kiridude on 2009-06-07
In order to "reset" your machine, you should take out the battery, power cable, and the small round battery inside. Unscrew the bottom of your laptop and you'll find it (maybe under a card). After a couple of minutes put it back together and try to turn it on. 

If it does not boot after, you probably have a hardware issue as suggested by Favux. Then you need to go to HP...

---

### Post by ein4290 on 2009-06-07
okay i'll try it right now.. thank you very much.. i will post if there's any progress after doing it..

---

### Post by ein4290 on 2009-06-07
> **kiridude said:**
> In order to "reset" your machine, you should take out the battery, power cable, and the small round battery inside. Unscrew the bottom of your laptop and you'll find it (maybe under a card). After a couple of minutes put it back together and try to turn it on. 

If it does not boot after, you probably have a hardware issue as suggested by Favux. Then you need to go to HP...

i just read this post.. sorry
there is a small round battery? which screw(s) do i have to unscrew?

---

### Post by LiamWilson on 2009-06-07
> **ein4290 said:**
> yeah i did that. my notebook has been shutdown completely. but when i tried to turn it on again, i only see a black-empty screen.. oh and more information about the state.. the lamp indicating hard disk work is not shining.. but the light indicating caps and num lock repeteadly going on and off..
thx for your advice though!

Hmm. Blank screen you say? Flashing Lights? Sounds Like a POSSIBLE Kernel Panic. What I'd do is if the solution that kiridude and Favux suggested doesn't work, Boot up into a Live CD, place all your /media/disk/home contents on a USB or something, and Re-install. It could possibly be the best option, but only as a last resort.

---

### Post by Favux on 2009-06-07
Hi ein4290,

He's talking about the motherboard battery.  It's like a watch battery.  Sometimes motherboards have a reset button.  You'll have to use your manual or if it doesn't show you how to access the motherboard go to the HP site and see if there is a pdf.  While you have things apart you can check connections.  Along with the hard drive make sure the RAM is seated and hasn't come loose.

---

### Post by ein4290 on 2009-06-07
okay, i'll try to unscrew it and see if that works. wish me luck!

---

### Post by ein4290 on 2009-06-07
argh.. i had a hard time unscrewing them.. is there any other way to repair my notebook by myself? or should i just let someone more expert to handle this?

---

### Post by kiridude on 2009-06-07
Taking the little battery out is not really very complex, you just need a small screwdriver - it can't really be done with a normal one. Many laptops have different sections that are removable underneath. In mine its the center piece - and underneath the card right under the panel. In yours, maybe different. If you feel uncomfortable poking around in there. Try just taking out the battery and plug and leaving it over night, and see if that works. If not, take it to a shop and have someone do it for you.

---

### Post by GiveLove on 2009-06-07
This same problem just happened to me this morning. I powered on my computer, which defaults to booting Ubuntu 9.04 in GRUB. Then I went to go wash the dishes. When I came back, the monitor was in suspend mode, yet the computer was still powered on. Shaking the mouse or pressing keys on the keyboard did not bring my computer out of whatever low power mode it was in. It had obviously frozen. Which I had seen before with 9.04 and suspend. 

What I had not seen was it completely causing my computer to not be able to boot into the BIOS post screen. No matter how many hard resets, or disconnects from power. I was not a happy camper! :mad: I thought that I had had a catastrophic hardware failure.

Turns out that what I assume is the suspend feature locked up something in the motherboard BIOS, thus not allowing it to even post. I had to reset the BIOS via the jumper on the motherboard. Then my computer would beep and show the BIOS post screen and allow me to boot an operating system. Then try and remember my previous BIOS settings. Interestingly enough, I had already changed the setting:

**Put computer to sleep when in inactive for:** to "never". As I already had previous problems with suspend just bringing me to a blinking cursor, and having to hard reset. 

This desktop computer is pretty old hardware. About nine years old. I've never had this sort of problem before with Ubuntu since 6.06 or Fedora 5, 6 ,and 7.

AMD Athlon XP 1800+
Abit KR7A-133R (Via KT266a northbridge)
1GB DDR-266 RAM
Nvidia Geforce 7600GS AGP video card
Creative Labs Audigy 2 ZS sound card
D-Link DFE-530TX+ 10/100 network card
USB 2.0 add in PCI card.
160GB Seagate hard drive
450watt Enermax powersupply



I've actually been in the process of evaluating Debian 5.0. And it runs so nicely. Everything seems to work as expected, and it's Debian stable ;). This problem is the final straw to leave Ubuntu's crazy instabilities that have plagued it since 8.04. What ever happened to the good old days of Ubuntu 6.06 to 7.04?

-----------------------------

ein4290,

If you have a paper manual for your laptop. You might check if it has a CMOS/BIOS reset jumper. This would be easier than removing the CMOS/BIOS battery. Just a thought. Hope you are able to get your laptop working again.

Peace,
GiveLove

---

### Post by ein4290 on 2009-06-10
@GiveLove
thank you very much for sharing your experiences. however i ended up brought my notebook to the HP service center in my area (i'm in Jakarta, Indonesia, BTW)
it seems that HP would take care of the problem(s) in my notebook. thank you for everybody. even though i had this horrible experience (my first time to bring my notebook to service center!), i'll try not to give up on ubuntu because in those few minutes before the incident, i was having a very good time.
this is the best forum that i've ever join. my question gets respond so fast. for all the members of this forum, please keep guide me in this new world. thx for everyone and once again, sorry for my bad english :)

@moderator
please close this thread if you want to, thx

---

