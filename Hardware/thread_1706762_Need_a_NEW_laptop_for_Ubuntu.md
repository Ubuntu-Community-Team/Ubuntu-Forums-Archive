---
title: "Need a NEW laptop for Ubuntu"
date: 2011-03-14
forum: Hardware
---

### Post by donalgodon on 2011-03-14
Would this laptop [http://www.dell.com/us/p/xps-l502x/pd?oc=dndodh1&model_id=xps-l502x](http://www.dell.com/us/p/xps-l502x/pd?oc=dndodh1&model_id=xps-l502x) have full video card compatibility with Ubuntu?

I want to buy a new laptop, but I want something that won't have problems with drivers. The compatibility list here is pretty dated, so the current models don't often show up.

Any advice would be appreciated.

---

### Post by ajgreeny on 2011-03-14
Should be OK, I think, with nvidia graphics and intel wireless.

No idea about the webcam, but that may not be quite so important to you.

---

### Post by donalgodon on 2011-03-14
Thanks for the reply. The webcam is something that I care little to nothing about, so looks like this is it for me.

Does Ubuntu have native drivers for this video config, or will I have to install manually the proprietary drivers?

Just asking because I only have ever used Intel HD graphics with Ubuntu.

---

### Post by Slave2Metal on 2011-03-14
Unfortunately, you'll be stuck using the intel chip on that machine.  You can turn off the nvidia card, but will not be able to use it at this time with ubuntu.  You can thank optimus for that.

> **donalgodon said:**
> Thanks for the reply. The webcam is something that I care little to nothing about, so looks like this is it for me.

Does Ubuntu have native drivers for this video config, or will I have to install manually the proprietary drivers?

Just asking because I only have ever used Intel HD graphics with Ubuntu.

---

### Post by donalgodon on 2011-03-14
So, I'm back to the drawing board. 

What newer model laptop would offer the best experience/performance for Ubuntu out of the box?

---

### Post by Slave2Metal on 2011-03-14
If I hadn't bought my xps already, I would look at a lenovo t410 or t510.  The newer models will be out soon(t420/t520 sandy bridge).  I like the x201 for a portable.  Comes with icore chips, but also a hefty price tag.  But, if you want a backlit keyboard, I don't believe it's an option on the thinkpads like it is the xps.
Right now, anything with optimus does not have support in linux.  Some laptops have the option to switch the nvidia card off in bios.  Not sure if the second version xps15 has it or not.  My L501x does not and it doesn't matter, because its useless anyway.  Here's a list of certified hardware, but I don't believe it's that update for the cutting edge stuff. _[http://www.ubuntu.com/certification](http://www.ubuntu.com/certification)_

For wireless, I would try and stick with intel cards.  The base model centrino in my xps is the n1000 and it seems to be reliable so far.
> **donalgodon said:**
> So, I'm back to the drawing board. 


What newer model laptop would offer the best experience/performance for Ubuntu out of the box?

---

### Post by donalgodon on 2011-03-14
Looks like the new Lenovo's all have Optimus aslo.

I'd be happy with the simple improvement over HD graphics, since the built in graphics in the 2nd generation series is plenty fast for non-gamers like me.

Is there one that ONLY uses the sandybridge graphics?

---

### Post by Slave2Metal on 2011-03-14
You'll have to do some research on the new models.  I did read somewhere that the thinkpads have a bios switch, but cannot confirm.  Also, you can get a t410/510 with intel graphics only.  I'm assuming it would be the same for SB.  You would configure from the base model up and stay away from switchable graphics configurations.
> **donalgodon said:**
> Looks like the new Lenovo's all have Optimus aslo.

I'd be happy with the simple improvement over HD graphics, since the built in graphics in the 2nd generation series is plenty fast for non-gamers like me.

Is there one that ONLY uses the sandybridge graphics?

---

### Post by donalgodon on 2011-03-15
Having a heck of a time finding something that doesn't have a discrete video card in the 2nd gen Core i series laptops.

Anyone else have any luck?


Edit:

Configed to spec via Dell plain-vanilla onboard graphics core i 2nd gen, centrino wireless runs up to over $1,200!

No, thanks. The same spec with discrete graphics can be had for around $799. Nonsense.

---

### Post by donalgodon on 2011-03-15
How about the wireless in this one??

[http://shop.lenovo.com/SEUILibrary/controller/e/web/LenovoPortal/en_US/catalog.workflow:category.details?current-catalog-id=12F0696583E04D86B9B79B0FEC01C087&current-category-id=906E364A9BBD7E7BF1B30DF0790656CB&action=init](http://shop.lenovo.com/SEUILibrary/controller/e/web/LenovoPortal/en_US/catalog.workflow:category.details?current-catalog-id=12F0696583E04D86B9B79B0FEC01C087&current-category-id=906E364A9BBD7E7BF1B30DF0790656CB&action=init)

Looks like it's realtek? or no,maybe Broadcom?

If that's the case, the new Natty kernel should support it, right?

Doesn't it have newer support for Broadcom, etc.?

---

### Post by TBABill on 2011-03-15
Can you get the Dell without the nVidia and just use the Intel Core ix chip's on-chip GPU instead? I have a Dell 1564 with i3-330 and the graphics chip works great. I have yet to push it to where it fails on anything. Unless you're gaming I can't imagine needing much more and I haven't found a distro yet that doesn't work well with it (besides PCLinuxOS, which has an xorg too old to support 3D on it). Just a thought, regardless which brand you buy.

---

### Post by donalgodon on 2011-03-15
> **TBABill said:**
> Can you get the Dell without the nVidia and just use the Intel Core ix chip's on-chip GPU instead? I have a Dell 1564 with i3-330 and the graphics chip works great. I have yet to push it to where it fails on anything. Unless you're gaming I can't imagine needing much more and I haven't found a distro yet that doesn't work well with it (besides PCLinuxOS, which has an xorg too old to support 3D on it). Just a thought, regardless which brand you buy.

Yes, I can, but the same config is like $799 with graphics and $1,200 without!?? (customized builds are more expensive, it seems)

So, I think if the Lenovo works out, it might be my best buy. I'm just trying to confirm the OEM for the LenovoWirlessBGN.

---

### Post by Slave2Metal on 2011-03-15
On lenovo.com, for non intel wireless, its showing broadcom, atheros, gemtek, liteon
> **donalgodon said:**
> How about the wireless in this one??

[http://shop.lenovo.com/SEUILibrary/controller/e/web/LenovoPortal/en_US/catalog.workflow:category.details?current-catalog-id=12F0696583E04D86B9B79B0FEC01C087&current-category-id=906E364A9BBD7E7BF1B30DF0790656CB&action=init](http://shop.lenovo.com/SEUILibrary/controller/e/web/LenovoPortal/en_US/catalog.workflow:category.details?current-catalog-id=12F0696583E04D86B9B79B0FEC01C087&current-category-id=906E364A9BBD7E7BF1B30DF0790656CB&action=init)

Looks like it's realtek? or no,maybe Broadcom?

If that's the case, the new Natty kernel should support it, right?

Doesn't it have newer support for Broadcom, etc.?

---

### Post by donalgodon on 2011-03-15
> **Slave2Metal said:**
> On lenovo.com, for non intel wireless, its showing broadcom, atheros, gemtek, liteon

Forgive me, but I didn't see that. Can you please show me where you found that information?

---

### Post by Slave2Metal on 2011-03-15
[http://consumersupport.lenovo.com/us/en/DriversDownloads/drivers.html](http://consumersupport.lenovo.com/us/en/DriversDownloads/drivers.html)
Option 2, select the model you're interested in.

---

### Post by donalgodon on 2011-03-16
> **Slave2Metal said:**
> [http://consumersupport.lenovo.com/us/en/DriversDownloads/drivers.html](http://consumersupport.lenovo.com/us/en/DriversDownloads/drivers.html)
Option 2, select the model you're interested in.

Lenovo confirmed spec sheet says Broadcom.

Is that good news? :) :confused:

---

### Post by donalgodon on 2011-03-16
Am I making a big deal out of nothing? Do the proprietary drivers actually work? I don't have enough experience with Ubuntu to know the status, as I have only used it on two laptops both with Intel HD graphics only and no discrete video.

Anyone make a recommendation about which is the best discrete video for Ubuntu, if any?

---

### Post by Slave2Metal on 2011-03-17
> **donalgodon said:**
> Am I making a big deal out of nothing? Do the proprietary drivers actually work? I don't have enough experience with Ubuntu to know the status, as I have only used it on two laptops both with Intel HD graphics only and no discrete video.

Anyone make a recommendation about which is the best discrete video for Ubuntu, if any?

Did you look through the certified hardware link I posted.  It really depends on how much you like tweaking ubuntu to get things to work.  If not, then get one that uses certified hardware and stay away from nvidia.  I think as a rule, intel seems to have good compatibility. Honestly, I would get a T series with integrated graphics.  The prices are starting to drop because the new ones release any day. Google lenovo coupon codes if lenovo isn't having any discounts.  DEALIGG comes to mind.  SB sounds great,  it will be expensive on high end models right now or forced to buy lower end.  Again, if you like tweaking ubuntu and experimenting, get the xps, it's an ok machine.  But my next one will be a thinkpad.  Main thing is, do some research to see what potential problems may arise in a laptop you're considering.  If you get an optimus card, you will have to apply a fix to turn it off in linux so it doesn't draw power/heat.  Because it is useless for linux ATM.

---

### Post by donalgodon on 2011-03-17
> **Slave2Metal said:**
> Did you look through the certified hardware link I posted.  It really depends on how much you like tweaking ubuntu to get things to work.  If not, then get one that uses certified hardware and stay away from nvidia.  I think as a rule, intel seems to have good compatibility. Honestly, I would get a T series with integrated graphics.  The prices are starting to drop because the new ones release any day. Google lenovo coupon codes if lenovo isn't having any discounts.  DEALIGG comes to mind.  SB sounds great,  it will be expensive on high end models right now or forced to buy lower end.  Again, if you like tweaking ubuntu and experimenting, get the xps, it's an ok machine.  But my next one will be a thinkpad.  Main thing is, do some research to see what potential problems may arise in a laptop you're considering.

Thanks for the input. I did see the list, but I'm trying to get the newest thing I can which will serve me... best bang for the buck... so to speak, so I don't end up with something that's too outdated too quickly, which I realize is (on some level) inevitable.

I don't mind tweaking, it's more that I don't want to be stuck with something that, even after tweaking, doesn't basically work right. I'm assuming (maybe incorrectly) that the driver issues will eventually be resolved, so that a more powerful computer will be a better investment for performance.

I've read that the Broadcom wifi support was added to the newest kernel, so I was hoping that this would benefit me, because I do like the spec of the G570. It has everything I wanted for a pretty good price, but I will have to look a little more.

Thanks for the tips and suggestions. I really appreciate it.

---

### Post by Zevaka on 2011-03-17
acer aspire timeline 5810TG + ubuntu 10.10 + some effor = up to 10 hours of battery work \m/

---

### Post by donalgodon on 2011-04-28
Just to follow up and resolve my own OP, I settled on the Dell Inspiron N5110, which has the Core i5 and is FULLY supported out of the box with Natty!

Just FYI. I'm loving it. I get 15 levels of brightness control by default. That's just super.

---

### Post by Yellow Pasque on 2011-04-28
> **donalgodon said:**
> Just to follow up and resolve my own OP, I settled on the Dell Inspiron N5110, which has the Core i5 and is FULLY supported out of the box with Natty!

Just FYI. I'm loving it. I get 15 levels of brightness control by default. That's just super.
Good for you. You did your homework. Lately, there have been far too many posts from people that didn't and ended up with hybrid graphics.

---

### Post by donalgodon on 2011-05-02
Follow up part 2....

If anyone is thinking about the new 15r (N5110) I mentioned purchasing it is a great bargain and runs Ubuntu very, very well out of the box, but... if you plan on swapping the internal HD be aware that you must literally disassemble the entire case and remove the motherboard to do it. Fair warning on an utterly stupid design, as the HD is beneath the motherboard with no door access. 

On a positive note, the service manual illustrates the process pretty clearly, but it's still a pain to do. Just swapped it out for an SSD.

Whoever designed this model needs to be severely beaten before they are fired. Since the drive is beneath the board, it would have been simple to add an access door!

---

### Post by Muflon on 2011-06-09
> **donalgodon said:**
> Just to follow up and resolve my own OP, I settled on the Dell Inspiron N5110, which has the Core i5 and is FULLY supported out of the box with Natty!

Just FYI. I'm loving it. I get 15 levels of brightness control by default. That's just super.

I am thinking of getting the same laptop.  Which graphics card did you opt for?

Thanks

Muflon

---

### Post by donalgodon on 2011-06-09
> **Muflon said:**
> I am thinking of getting the same laptop.  Which graphics card did you opt for?

Thanks

Muflon

I just went with the standard HD3000 graphics, because they are good enough for my needs. I've been extremely pleased with the performance so far. It's a great value.

---

### Post by Muflon on 2011-06-20
I have taken the plunge and just ordered the same laptop. :)

Muflon

---

### Post by donalgodon on 2011-06-20
> **Muflon said:**
> I have taken the plunge and just ordered the same laptop. :)

Muflon

I think you'll be pleased, until you decide to change the hard drive, that is! ;)

One more positive point is that it comes with 4GB in one slot and one empty.

---

### Post by PapaGary on 2011-06-20
> **donalgodon said:**
> 

If anyone is thinking about the new 15r (N5110) I mentioned purchasing it is a great bargain and runs Ubuntu very, very well out of the box, but... if you plan on swapping the internal HD be aware that you must literally disassemble the entire case and remove the motherboard to do it. Fair warning on an utterly stupid design, as the HD is beneath the motherboard with no door access. 

On a positive note, the service manual illustrates the process pretty clearly, but it's still a pain to do. Just swapped it out for an SSD.

Whoever designed this model needs to be severely beaten before they are fired. Since the drive is beneath the board, it would have been simple to add an access door!

(Slightly off topic)- That's what I love about my Toshiba L635: two screws on the bottom allow a panel to open exposing both the RAM modules and the hard drive. That and it is only $349 at Best Buy and Crucial sells an 8G RAM upgrade for $89.:)

---

### Post by Muflon on 2011-06-21
> **donalgodon said:**
> I think you'll be pleased, until you decide to change the hard drive, that is! ;)

One more positive point is that it comes with 4GB in one slot and one empty.

Hi donalgodon 

Which SSD did you go for and does it make a noticable difference to performance and battery life?

Thanks

Muflon

---

### Post by donalgodon on 2011-06-23
> **Muflon said:**
> Hi donalgodon 

Which SSD did you go for and does it make a noticable difference to performance and battery life?

Thanks

Muflon

I put in a second gen Intel ssd 160 GB and yes, it does make a HUGE improvement in performance and a fairly noticeable improvement in battery life. Put one in my HP also, and I'll never use a standard platter HD again. I'm spoiled by the instantaneous response.

---

### Post by Muflon on 2011-06-23
> **donalgodon said:**
> I put in a second gen Intel ssd 160 GB and yes, it does make a HUGE improvement in performance and a fairly noticeable improvement in battery life. Put one in my HP also, and I'll never use a standard platter HD again. I'm spoiled by the instantaneous response.

Just ordered a Crucial m4 SSD 128 GB, so I can look forward to replacing the standard drive :)

Muflon

---

### Post by donalgodon on 2011-06-24
> **Muflon said:**
> Just ordered a Crucial m4 SSD 128 GB, so I can look forward to replacing the standard drive :)

Muflon

Just download the service manual from dell's website. It details the process pretty well... take your time... because you literally have to remove the motherboard completely. Just a tip: Be sure to check all the connectors and double check them before you reassemble. There are a couple of very small connectors on the front end of the board which are easy to wiggle loose in the process (they just press down into the socket) and also make sure that you tighten the hinge screws, because if not, you might have clicking.

It's easier than it looks, if you have a little patience.

What helps me is to take a piece of paper and clear tape for each set of screws and label them, so I know what goes where.

---

### Post by Muflon on 2011-06-27
> **donalgodon said:**
> Just download the service manual from dell's website. It details the process pretty well... take your time... because you literally have to remove the motherboard completely. Just a tip: Be sure to check all the connectors and double check them before you reassemble. There are a couple of very small connectors on the front end of the board which are easy to wiggle loose in the process (they just press down into the socket) and also make sure that you tighten the hinge screws, because if not, you might have clicking.

It's easier than it looks, if you have a little patience.

What helps me is to take a piece of paper and clear tape for each set of screws and label them, so I know what goes where.

I have got stuck on step 8 of the Removing the Palm-Rest Assembly.  I can't see how you remove the Palm-Rest Assembly after removing the keyboard.

Muflon

---

### Post by donalgodon on 2011-06-27
> **Muflon said:**
> I have got stuck on step 8 of the Removing the Palm-Rest Assembly.  I can't see how you remove the Palm-Rest Assembly after removing the keyboard.

Muflon

Start at the top corner and separate it. It's held by clips. Just take your time. You can do it. :)

It pops all around as it's held by maybe 8-10 clips if I recall. Once you can start the first one, the rest are easier.

Start at the top corner (the left one worked best for me) at the base of the screen hinge. You can see the seam there, if you look closely. If you have a small teflon spreader, it'll be easier, but you can do it with your hands.

If I can be of any more help, just let me know.

---

### Post by Muflon on 2011-06-28
> **donalgodon said:**
> Start at the top corner and separate it. It's held by clips. Just take your time. You can do it. :)

It pops all around as it's held by maybe 8-10 clips if I recall. Once you can start the first one, the rest are easier.

Start at the top corner (the left one worked best for me) at the base of the screen hinge. You can see the seam there, if you look closely. If you have a small teflon spreader, it'll be easier, but you can do it with your hands.

If I can be of any more help, just let me know.

Just got finished installing the hard drive and installing Ubuntu. The laptop now boots up in about 20 seconds (including typing my password) :D

Thanks for all the help!  I owe you a beer.

Muflon

---

### Post by donalgodon on 2011-06-28
> **Muflon said:**
> Just got finished installing the hard drive and installing Ubuntu. The laptop now boots up in about 20 seconds (including typing my password) :D

Thanks for all the help!  I owe you a beer.

Muflon

No problem, my friend. Any time. Glad I could help.

---

