---
title: "Bad RAM? Bad graphics card? Both? Any help here?"
date: 2010-05-12
forum: Hardware
---

### Post by thegreenblob on 2010-05-12
Hey everyone, I recently bought a new graphics card, a Palit Nvidia GTS 250 1GB, and I was having problems with it (any 3D application or game causing the graphics card to stop sending a signal to the monitor within minutes EVERY time, in both Linux and Vista), so I requested an RMA... got a new one, but... this one did the same thing.

So I figured it was something else so I started looking in options in my bios and turned off an option called "Memory Remapping Feature", and this seemed to have fixed my problem. Or so I thought, after about a week I got a crash like the above, rebooting fixed it and it didn't happen again.

But then I decided to run memtest86 it ran for about 4 hours, didn't see any errors, I walk in my room like an hour later (5 hours total), just in time to notice my graphics card stop sending a signal to the monitor, so... that makes me think it's not related to 3D at all (unless memtest86 became a 3D application without my knowledge :P), and then I reboot but now... nothing, the fans for the graphics card to to 100% when I turn on the computer but nothing appears on screen.

I can take the graphics card out and use onboard video (nvidia 7100) just fine. But if I try to use onboard while the gts 250 is still in there, it boots up, I can access my bios, but it won't boot from a hard drive and just stays at a screen with some information.

So... anyone have any ideas? Is this bad RAM, graphics card, both? Other? Any help would be appreciated. 

Oh, and if anyone is thinking over heating, it is definitely not that, the temps for the GPU and CPU were both completely fine when 2 of the crashes occurred. (Was monitoring temps to troubleshoot the problem when I got the first graphics card). Running memtest86 with onboard video right now. No errors so far but I'll post if there is any... or if (hopefully not) my onboard video stops sending a signal >.>

---

### Post by dino99 on 2010-05-12
if you dont have over heating , no need to ask if your card is a standard one or a special fab's built with no genuine nvidia settings ?

the logs and .xsession-errors might help to know why you have these issues. Is it possible that your psu is not strong enought for your config ?

---

### Post by thegreenblob on 2010-05-12
> **dino99 said:**
> if you dont have over heating , no need to ask if your card is a standard one or a special fab's built with no genuine nvidia settings ?

the logs and .xsession-errors might help to know why you have these issues. Is it possible that your psu is not strong enought for your config ?

I'm not sure if it's standard or not. This is my card: [http://www.newegg.com/product/product.aspx?Item=N82E16814261062](http://www.newegg.com/product/product.aspx?Item=N82E16814261062)

I'll check my logs and .xsession-errors after I run memtest for awhile.

I suppose my PSU might not be powerful enough, but I doubt it.

This is my PSU: [http://www.newegg.com/Product/Product.aspx?Item=N82E16817371007](http://www.newegg.com/Product/Product.aspx?Item=N82E16817371007)

I doubt it because there's a review and someone claims to be running a GTX 260 with it and the gtx 260 requires a lot more power than the gts 250.

---

### Post by Objekt on 2010-05-12
It sounds like you got a second defective card.  Cross-platform problems such as you describe are almost always bad hardware.  I'm going to assume you have a big enough power supply.

I had almost the same problem about a year ago, with an XFX GeForce 9800 GTX.  The display would stop getting a signal after just a few minutes any time I was in a text-only environment, such as command-line Linux, BIOS configuration screens, Memtest 86+, or Windows XP installation.

One difference: the display shutoffs never seemed to happen whenever I was running a GUI with the Nvidia drivers loaded.  At the time, that meant Windows XP or Kubuntu with the Nvidia binary driver. 

Much cursing and testing later, I concluded I must have a bad video card.  XFX agreed, so I sent it in.  They replaced it with GeForce 9800 GTX+, the fastest single-core GeForce card ever made.  Not a bad outcome.  It only cost me $10 shipping + a couple of weeks without my primary computer.

At least you can use the built-in video while you wait for the new card.

Also:
Once you have the card out, you could run Memtest 86+ overnight with your built-in video card as the display.  Might as well rule out RAM as a problem.

---

### Post by dino99 on 2010-05-12
> **thegreenblob said:**
> I'm not sure if it's standard or not. This is my card: [http://www.newegg.com/product/product.aspx?Item=N82E16814261062](http://www.newegg.com/product/product.aspx?Item=N82E16814261062)

I'll check my logs and .xsession-errors after I run memtest for awhile.

I suppose my PSU might not be powerful enough, but I doubt it.

This is my PSU: [http://www.newegg.com/Product/Product.aspx?Item=N82E16817371007](http://www.newegg.com/Product/Product.aspx?Item=N82E16817371007)

I doubt it because there's a review and someone claims to be running a GTX 260 with it and the gtx 260 requires a lot more power than the gts 250.

enter your settings here:
[http://support.asus.com/PowerSupplyCalculator/PSCalculator.aspx?SLanguage=en-us](http://support.asus.com/PowerSupplyCalculator/PSCalculator.aspx?SLanguage=en-us)

your card:
System Requirements  	Minimum 450W or greater system power supply (with a minimum 12V current rating of 24A)

your psu:
Output  	+3.3V@25A,+5V@24A,+12V1@22A,+12V2@22A,-12V@0.8A, +5VSB@2.5A

[COLOR="Blue"]as you can see your psu is only 12v/22A and your card need 12v/24A [/COLOR] :)

---

### Post by thegreenblob on 2010-05-12
Well that's a bummer. I plan on running memtest86 all day today (just gonna use my netbook for the day), to determine if it is or isn't a memory problem. I'll post the results tonight. And if it isn't I guess I'll request another RMA :|

But if anyone has any other ideas, please post them.

EDIT: Didn't see previous post. My recommended PSU is 300W, and I have a 500W.

EDIT2: Didn't see previous posts edit.

> your card:
System Requirements Minimum 450W or greater system power supply (with a minimum 12V current rating of 24A)

your psu:
Output +3.3V@25A,+5V@24A,+12V1@22A,+12V2@22A,-12V@0.8A, +5VSB@2.5A

as you can see your psu is only 12v/22A and your card need 12v/24A 

Wow. Well that really sucks :(, wish I would have realized this sooner. Would 2A off really cause this much of a problem? I ask because I see a lot of people in the reviews for my PSU running cards that require the same amount if not more power :/

---

### Post by dino99 on 2010-05-12
> **thegreenblob said:**
> Well that's a bummer. I plan on running memtest86 all day today (just gonna use my netbook for the day), to determine if it is or isn't a memory problem. I'll post the results tonight. And if it isn't I guess I'll request another RMA :|

But if anyone has any other ideas, please post them.

EDIT: Didn't see previous post. My recommended PSU is 300W, and I have a 500W.

EDIT2: Didn't see previous posts edit.



Wow. Well that really sucks :(, wish I would have realized this sooner. Would 2A off really cause this much of a problem? I ask because I see a lot of people in the reviews for my PSU running cards that require the same amount if not more power :/

well you play on the border line, and your card is not alone on the psu , make some additions using the link posted

---

### Post by thegreenblob on 2010-05-12
Whoops. I actually messed up, I left the graphics card at "x0" >.>, recommended is actually 500W. (But I will say that the entire system minus the graphics card ran fine on 250W before I upgraded my power supply)

But if I don't have enough amps, I guess the wattage doesn't matter as much does it? :(

Well thanks for all your help. It really didn't even cross my mind that it was the power supply.

So... anyone want to recommend me a new power supply? Don't want to get that wrong again >_<

---

### Post by dino99 on 2010-05-12
you have two choices:

- select the hardware plugged on that psu and remove what you dont really need

- calculate the real power needed with all your hardware and select a psu with a power >= this real power * 120 %, of course you may choose different psu power and quality

but now you know how to do that :P

---

