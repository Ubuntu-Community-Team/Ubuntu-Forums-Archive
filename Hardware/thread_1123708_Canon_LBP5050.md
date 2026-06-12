---
title: "Canon LBP5050"
date: 2009-04-12
forum: Hardware
---

### Post by keppi.fi on 2009-04-12
First I have to tell that I have just started to use Ubuntu and Linux in general so I'm a "newbie"... 

I have managed to get my desktop to run Ubuntu 9.04 and everything works perfectly even my RAID 1 configuration but I can't get my printer to work. I have a Canon i-SENSYS LBP5050 laser printer and still after several attempts I haven't got it to print. 

Is there a driver available that would work with this printer model and what has to be done to get it printing?

---

### Post by schmidtbag on 2009-04-13
I checked if the printer driver exists in ubuntu, and it doesn't.  theres 1 model older and theres a few newer ones.  go to system>administration>printing, click on new, and try some of the other LBP models and see if they work.  they most likely will but there may or may not be some minor glitches in your printing and you probably won't get full support but you never know.  you could try looking it up online too, just try searching "download cannon lbp5050 linux driver"

---

### Post by keppi.fi on 2009-04-14
Thanks for the tips... However after trying everything including different drivers and this [how-to]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900"), I still can't get my printer to print. Status shows processing after print command but nothing happens. 

Help!!

---

### Post by schmidtbag on 2009-04-14
that howto isn't designed for your printer.  i'm sorry, but it probably isn't compatible at all.  i suppose your only choice now is to ask the company about whether linux drivers will be made or search for something on google.  you could TRY using the software included with the printer but i doubt linux programs will be able to communicate to it

---

### Post by keppi.fi on 2009-04-14
I was afraid of this.... Does anyone have any solution in mind than just changing the printer? Maybe using a Windows PC as a server or some print server (I don't know what you can do with those)?

---

### Post by schmidtbag on 2009-04-14
well you could do a network printer share but the problem with that is i'm pretty sure the OS using that printer has to install it too, so really you don't have much of a choice

---

### Post by keppi.fi on 2009-04-16
Well let's see what happens. I sent a question to canon about the driver. Probably I'll just get something like "not supported".

---

### Post by pmorton on 2009-06-27
> **keppi.fi said:**
> Well let's see what happens. I sent a question to canon about the driver. Probably I'll just get something like "not supported".

I'm not, I'm afraid, going to say anything to help you get your Canon printer working. You may, like me, have bought a Canon printer on the strength of Canon's Specification, which quite clearly states that its LBP printer range is compatible with the Linux operating system,and is quite specific about the distributions with which it is claimed to work. Remarkably, therefore, Canon neither supports nor maintains these drivers, and will provide no assistance whatsoever, as I've found out, when the problem is brought to its attention. Canon ought to be obliged to remove from its product literature all reference to its equipment being Linux-compatible. 

What you can do is send the machine back to the supplier as being in breach of EU consumer regulations by misrepresentation, and ask for your money back.  You can also complain to your MEP that the company is misrepresenting its products. After all, why should Europeans waste their money on imported goods which are mis-described?

---

### Post by nielsek on 2009-07-07
Did you find a solution? i have a friend, that only needs that printer to work, to make the final jump from windows.

---

### Post by flux_x on 2009-11-01
Hi
I found a driver for the LBP 5050 at following link:

  	 	 	 	 	 	  [COLOR=#000080]_[http://support-hk.canon-asia.com/contents/HK/EN/0900772407.html](http://support-hk.canon-asia.com/contents/HK/EN/0900772407.html)_[/COLOR]
 
It works at my SuSE Linux 11.
I hope it will also work on ubuntu.

kind regards
flux_x
:popcorn:

---

### Post by scamu on 2009-11-04
hi all. Did finally someone succeeded in running this LBP 5050 under ubuntu ? 
I was up to buy one but this thread did stop me.
maybe shall I buy the samsung clx 3175 instead cos I don't have weendowz

seb

---

### Post by pmorton on 2009-11-08
Forget it. For years Canon has advertized its LBP printer range as supporting Linux, but the fact is that although it once built a driver of sorts, it has never felt the need to ensure it continues to work. And it doesn't.

I don't know what people think in th US, but how Canon gets away with bringing its products into Europe with this deception is a mystery. Hopefully, sooner or later, Neelie Kroes's people will get to grips with it. 

The answer for anyone reading this is to buy a printer that people agree does what it says on the box. There are others,like Dell, that I know have good or at least adequate Linux support, but HP shows the way.

---

### Post by BuffaloX on 2009-12-01
> **flux_x said:**
> Hi
I found a driver for the LBP 5050 at following link:

  	 	 	 	 	 	  [COLOR=#000080]_[http://support-hk.canon-asia.com/contents/HK/EN/0900772407.html](http://support-hk.canon-asia.com/contents/HK/EN/0900772407.html)_[/COLOR]
 
It works at my SuSE Linux 11.
I hope it will also work on ubuntu.

kind regards
flux_x
:popcorn:

Good find, I've been searching Google quite a bit, to find out if this printer is good on Linux.
How feature complete is this driver, for example: can you make high res color prints? Is there a toner indicator? Can you rotate pages?
Does it support optimized dithering for Photo and presentations?
Is the general print quality good?


> **pmorton said:**
> Forget it. For years Canon has advertized its LBP printer range as supporting Linux, but the fact is that although it once built a driver of sorts, it has never felt the need to ensure it continues to work. And it doesn't.

I don't know what people think in th US, but how Canon gets away with bringing its products into Europe with this deception is a mystery. Hopefully, sooner or later, Neelie Kroes's people will get to grips with it. 

The answer for anyone reading this is to buy a printer that people agree does what it says on the box. There are others,like Dell, that I know have good or at least adequate Linux support, but HP shows the way.

The download page states:
> Linux Printer Driver (CAPT) Ver.1.90E
Last Updated : 07-Sep-2009

So maybe Canon has improved their Linux support?

Unfortunately a comparable HP printer is exactly twice the price where I live, I can make almost a thousand color prints on the Canon for the price difference.

---

### Post by Mott1980 on 2009-12-03
I have this printer and I have been using this driver for some weeks. It works, although it doesn't offer all the features the printer has on windows. It's enough for my needs, but if you're a professional or you need more features, better get another printer (and preferably not canon).

1)  Canon seems to update the CAPT driver once a year. So, their newest printers usually don't get support until september-october. If you buy their latest printer in January, you're probably stuck with a paperweight for 9-10 months.
2) Canon does not ensure that the next driver will provide support for any new printer you may buy. So it's always risky to buy a non-supported printer (at any time, canon might discontinue their linux driver policy).
3) The linux CAPT driver appears to be hidden in some of their Asia subsites (you won't find it nor in their European sites nor in their American ones). Try Canon Singapore for the most straightforward download path.
4) Don't bother to ask Canon for advice, questions or whatever. They'll systematically ignore your mails.

So, this is the state of the so-called "Canon linux support".

Aftermath: All my digital cameras in the last 6 years have been Canon... Until I bought the printer and saw how much they care about linux. My new camera is Olympus.

---

### Post by BuffaloX on 2009-12-03
Too bad, Canon makes a lot of good hardware.
But I already decided that the obscurity of the driver download was a problem.
I'll check out the Samsung CLP 315 printer.
If that fails too, it will be an HP.

---

### Post by Mott1980 on 2010-01-30
One last surprise. When I recently updated to 9.10, I ran into a slight dependency problem. Two crucial packages were missing: libcupsys2 and libstdc5++... I just had to import them from the Jaunty repositories to make the driver work. Of course, this can be found nowhere in the canon documentation.

---

