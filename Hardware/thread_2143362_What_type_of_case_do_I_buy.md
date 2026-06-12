---
title: "What type of case do I buy?"
date: 2013-05-08
forum: Hardware
---

### Post by S2UIRR3L on 2013-05-08
I'm looking to upgrade a computer, but there's no room in this tiny case.
My problem, I don't know what kind of case to buy for this mother board.
Is it an ATX, MiniATX, MicroATX, I have no idea what will/won't fit it lol.

I've tried google searches, but can't find anything on it. I really love the
way everything runs on this little setup. It's dual booted with Lucid Lynx
64-bit and Win-7 Ultimate 64-bit (so I can run and play SimCity 2013).

If it helps, this is what I can tell you about it:

Gateway SX2841-09e
Intel Prntium processor G6951
Intel GMA HD graphics
6-GB of DDR3 RAM

The integrated video card and the power supply is what I'm looking to
upgrade (because the on board graphics SUCK, really bad) and I've had
to dull it down to Lego buildings. I want to see grass blowing in the wind!

Also, if I want to upgrade the video card, I'm going to have to buy a
bigger power supply. The one that's in it right now is only 220-watts.
Yeah, everything is decent, but the graphics and PSU are pathetic!!!

What should I look for when buying a case for this mother board...
ATX / Mini ATX / Micro ATX / I don't know :(

---

### Post by Lightning Dragon on 2013-05-08
Hi, 

This would be better suited in the appropriate place on one of the sub-forums. This sub-forum is for Ubuntu support. But anyway, could you look at your motherboard and tell us the name on it? I can't find any details on "Gateway SX2841-09e" other than a full desktop that lacks details on the board. If I had it, I could look for cases you could use.

If it is tiny, then it most likely a mini or micro ATX case. 

EDIT

Removed links to guessed computer.

---

### Post by pqwoerituytrueiwoq on 2013-05-08
can i see some pictures of the inside?
i could select parts if you want a new system, but your current hardware is not that old so it seems like a waste to replace everything
looks like a slim micro atx case to me
this will get the motherboard model number if we are lucky
[FONT=courier new]sudo hwinfo --bios | grep -i product
[/FONT]edit: iirc you are located in Japan right? i don't know what kind of power plugs are used over there, so i will just use what we use here in the US
[http://www.newegg.com/Product/Product.aspx?Item=N82E16817151117](http://www.newegg.com/Product/Product.aspx?Item=N82E16817151117) - psu (remember too many watts means poor efficiency, not all brands are equal, may are outright liar)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814130792](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130792) - gpu (the nvidia gt/gtx 600 series chips are pretty power efficient)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16811147123](http://www.newegg.com/Product/Product.aspx?Item=N82E16811147123) - case (jsut a cheapy nothing special case, will be hard to isntall hdd with the CPU already on the motherboard)

BTW your graphics are not on-board they are on-cpu and are pretty nice on linux, i can play supertuxkart on max with it at 60fps, just cant use pixel shadders

---

### Post by sandyd on 2013-05-08
Moved to Hardware forums

---

### Post by S2UIRR3L on 2013-05-08
Well... I can't seem to find any photos of it with the panel off, but here's a few really clear photos of what it's in right now.
Just to make my self clear... I'm not looking to replace the mother board... I'm looking to put it into another case with room.
I need more room to install a larger power supply and get a full sized video card in there... Oh, and yeah... I'm in the States.

I'm wondering if anyone can tell me what type of mother board this is, just by looking at the rear input/output configuration?

[ATTACH=CONFIG]242355[/ATTACH](click image to enlarge) This is the front of the computer.
[ATTACH=CONFIG]242356[/ATTACH](click image to enlarge) This is the rear of the computer.

---

### Post by S2UIRR3L on 2013-05-08
@sandyd - It's been a while since I've started a thread and the forums have changed a bit. I'm sorry for posting in the wrong area.

---

### Post by Lightning Dragon on 2013-05-08
Hi,

I know you were only looking for a case, I was just hoping you could maybe see the motherboard's name and model. Please give me the full output of this command;

```
sudo dmidecode -t 2
```

That will ouput info on your mobo. And if that doesn't work, please install _*hardinfo*_ from either the terminal or Software Center, and then try to find your motherboard name and model under "DMI". :) 

But I have a strong feeling it is micro ATX or mini ATX (which there are cases/towers that support both), so now it depends on what features you want your case to have. Do you want it modular? Built for awesome airflow? USB3.0 on front panel? Things like that should be considered firstly after knowing what type of case you want.

---

### Post by squakie on 2013-05-09
Judging by the size - see the front view where an optical drive is half the case width and a good 2/3's or more of the height.  I would think microatx at best - perhaps even itx.

---

### Post by fantab on 2013-05-09
The form factor pertains to the size of the MotherBoard. You should tell us what Mobo you have. 
I would always go with ATX form factor for the cabinet. It can be used with all other form factors (miniATX and microATX) and will be more room inside for good ventilation.

Your 220w powersupply is too little in my opinion. You MUST have 500w minimum. Intel HD graphics are good for average multimedia machines. Perhaps underpowered for Gaming purpose. 

If I were you I would only change the power-supply for now. Or Rebuild a new Machine with more powerful Graphics and a Mobo to support it with 16Gigs of RAM from the bottom up.

My two cents...

---

### Post by S2UIRR3L on 2013-05-09
Okay - Here's the deal... A friend of mine just told me that it's a MiniATX.
I have a brand new 750-watt PSU from a different project that never happened.
I'm going to newegg and getting my self a 2-gig nVidia PCIe 2.0 x16 card and
that takes care of the hard ware issues... I'm also buying a great little case for
only $40 that is compatible with both MicroATX and MiniATX mother boards.
It has enough room for a second hard drive and great air flow, not to mention
the bonus blue LED lights. If they're too bright, I'll just buy a few black fans lol.

Thanks for all the help everyone!

---

### Post by pqwoerituytrueiwoq on 2013-05-09
good luck that looks like a low profile/slim case, a full size GPU will not fit much less a ATX psu
750 is way more than you need, maybe if you use 2 GTX 450s you may need 750w, too may ways gets you poor power efficiency

---

### Post by S2UIRR3L on 2013-05-09
If I'm not wrong, it's only a few dollars more on my electric bill. But I "think" I understand what you're saying about the huge PSU.
It's like having a Lamborghini in New York City. It's capable of speeds up to 280-mph, but you're lucky to see 35-mph in the city.

Now, if I can only find the little thing to mark this thread as SOLVED. It's been a while and Ubuntu Forums moved everything lmao.

---

### Post by S2UIRR3L on 2013-05-09
A few posts ago, I lied... I thought it was an nVidia card... It's an EVGA that I'm buying with this case:

mATX/ATX CASE: [http://www.newegg.com/Product/Product.aspx?Item=N82E16811208052](http://www.newegg.com/Product/Product.aspx?Item=N82E16811208052)
GRAPHICS CARD: [URL="http://www.newegg.com/Product/Product.aspx?Item=N82E16814130821"]http://www.newegg.com/Product/Product.aspx?Item=N82E16814130821
[/URL]
By the way - **HOW DO I MARK THIS THREAD AS SOLVED?!?!?**

---

### Post by pqwoerituytrueiwoq on 2013-05-09
edit 1st post ->advanced -> change [other] to [solved]

the chipset is nvidia, the card was assembled my evga

power supplies only get there rating efficiency for 20%-80% IIRC
so if you put a 1k watt unit in a system that uses 80w usually you are going to get poor efficiency
poor efficiency means more [COLOR=#ff0000]heat[/COLOR] and higher power bill, and more heat also means higher bills due to the AC, but may help in the winter so that is a mute point
sometimes the PSU i linked is cheaper at amazon due to shipping, it is a solid, reliable, and quiet unit with a 5 year warranty

you could get more powerful gt640, and save after rebate
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814162113](http://www.newegg.com/Product/Product.aspx?Item=N82E16814162113)

---

### Post by S2UIRR3L on 2013-05-10
Hey - that DOES look like a better card, but I don't think this board is capable of a PCIe "3.0" x16. It says 2.0 on the Gateway website. Something else that I found out about this computer is that the processor is "unlocked" or something and you can buy an "over clock" activation code for it, but I'm not going to over clock it.

That would mean that I'd also have to get a better cooling system, a better heat sink, I'd have to make sure that the actual chip is shaved and greased to make a proper contact with the after market sink... I'm not prepared to put any more money in this unit than I need to. This is just a temporary thing until I build a proper gamer.

I WOULD LOVE TO GO ALL FUJITSU AGAIN - GOD, I LOVE THAT PC!!!

@ pqwoerituytrueiwoq : Thanks for everything bro, ban ya laters! lol

---

