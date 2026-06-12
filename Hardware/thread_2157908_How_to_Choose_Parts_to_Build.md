---
title: "How to Choose Parts to Build"
date: 2013-06-27
forum: Hardware
---

### Post by Acharn on 2013-06-27
This may not be the best forum for what I'm looking for. I think I have to replace my motherboard, so I got started looking for options. Since I want to use my old case and CPU, I felt lucky to find a mobo with a Socket 775. This got me to thinking.

Is there any site (other than Tom's Hardware, which I'm already exploring) which can get me started learning about the currently available hardware? I have the feeling that Socket 775 isn't going to be around much longer, but what is the best alternative? Which one is likely to still be in use five years from now? OK, I know that's impossible to be sure of, but at least what looks probable?

My current motherboard turns out to be micro-ATX. Is there any reason to think some other form factor would be better? I'm pretty old and feel more comfortable with a "grandpa box," as Asok, the intern in Dilbert, calls desktop towers.

Knowing that most of my use will be browsing the web, but that I want to be able to play an occasional game like Rome:Total War, how do I start to choose a CPU? Go to Newegg and check what fits my price range? Is there any web site that summarizes this? Yes, Tom's Hardware does have a chart which is a helpful starting point; is that all there is?

Tom's Hardware also has an occasional article on how to build a budget gaming computer. Is that a good place to start? I don't need that much power, but that might be a good way to at least choose a CPU. Any other suggestions?

---

### Post by dino99 on 2013-06-27
hey i feel you should be able to grab some second hand mobo with a socket 775 in your brotherhood for a couple bucks (<50), like other users/integrators/hardware shops/social networks/...

---

### Post by Yellow Pasque on 2013-06-27
> Which one is likely to still be in use five years from now? OK, I know that's impossible to be sure of, but at least what looks probable?

Expecting a socket to be in use for 5 years is unreasonable (or unrealistic, at least). It's like buying a car and expecting parts to be readily available 2 decades later.

As for hardware review sites, I like techreport.com. You'll probably find this helpful: [http://techreport.com/review/23750/amd-fx-8350-processor-reviewed/14](http://techreport.com/review/23750/amd-fx-8350-processor-reviewed/14)

---

### Post by Cheesemill on 2013-06-27
Another good tech site which I use for most of my research...

[http://www.bit-tech.net/](http://www.bit-tech.net/)

---

### Post by dannyboy79 on 2013-06-27
i am still using socket 775 (1.8Ghz core2duo) as well but I am upgrading very soon. i am going to go with Ivy bridge (3570k) as it's fairly recent (1 gen behind haswell) and it's capabilities are very high (USB 3.0, PCIe 3.0). the chip is also easily overclocked IF I want to squeeze more out of it.

it comes down to how much money you have, because if you make the jump from that old of a socket to a newer 1 you'll most likely need to buy everything new besides maybe your case. New MB's and CPU's require new PSU connection and new RAM, so that's pretty much everything, then if you want to game you'll have to decide if the integrated GPU is good enough or to get a discrete GPU.

your cheapest option will be to purchase a new socket 775 motherboard, what CPU do you currently have I can help you spec a new MB and hopefully they're still available on either tigerdirect or newegg. it's really your choice to stick with micro atx but also depends on how many features you want and what size your current case is.

I use phoronix.com for all my latest linux and hardware info and compatibility

---

### Post by Yellow Pasque on 2013-06-27
If I was building a new box right now for your intended usage, I would use a Core i5-4570. It's not a "budget" chip, but you get a very capable GPU on the chip that should slice through older/lighter games and is ideal for video playback. A Q85 or Z87 mobo is necessary for Intel ClearVideo (offloading video processing).  Q85 boards don't seem to be readily available yet, so I would consider cheaper Z87 boards: [http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007627+600315497+600438204+600009017&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&IsNodeId=1&Subcategory=280&description=&hisInDesc=&Ntk=&CFG=&SpeTabStoreType=&AdvancedSearch=1&srchInDesc=](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007627+600315497+600438204+600009017&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&IsNodeId=1&Subcategory=280&description=&hisInDesc=&Ntk=&CFG=&SpeTabStoreType=&AdvancedSearch=1&srchInDesc=)

> My current motherboard turns out to be micro-ATX. Is there any reason to think some other form factor would be better?
Probably not. Reasons to use full-sized ATX:
- You need room for an exotic cooling solution
- You have a lot of PCI(-e) peripheral cards and need a bunch of slots
- You have an extra long GPU card

In terms of going smaller that microATX, there's mini-ITX, but that limits the power your system can use (especially if you're trying to build a reasonably quiet system).

---

### Post by Acharn on 2013-06-28
Thanks to everyone for helping me out here.

Dino99: You're probably right. I haven't taken the box to the one shop I know about yet. Waiting for my pension to arrive next week. After the further research I've been doing I realize it may not be the motherboard as such, it might just be the BIOS ROM, which I think could be replaced cheaply. When I plug it in I still get a signal -- one long, one short beeps -- but then nothing else happens. I live in Thailand, so I have less of a support network than you might be used to. 

Temujin, Cheesemill: Many thanks. That was what I was looking for. Actually, after posting yesterday I took a closer look at both Tom's Hardware and Newegg, and there's more there than I realized to help me make a selection. I just have to start budgeting some time to get caught up on the current chips. Makes me long for the 80386, except memory management was such a nightmare.

---

### Post by dannyboy79 on 2013-06-28
it may just be your cmos battery which stores the bios. if the battery is dead the computer normally won't post or it's behavior is very weird. try replacing the cmos battery (in the states here it's normally a CR2032) BUT your battery may be different, just take it out and see what it is. I would wear a static electric wrist band whenever you stick your hands into your case. Good luck

PS (personally I wouldn't go with a haswell chip since they are so new, who knows if the intel drivers are up to par yet except for what I've read on phoronix.com)

---

### Post by Acharn on 2013-06-29
Thanks for the mention of photonix.com. I'll check them out.

You could be right about the battery. That'd be a hoot. As things were deteriorating a couple of times I got three short beeps during the POST, and now what I get is a long and a short beep. From Google I learn that for the Award BIOS this means a RAM problem of some kind. Luckily I also find from the Internet that the Advice computer company here in Thailand has DDR2 SDRAM available for about $30 for 2GB -- and that would be double the RAM that I had originally.

Obviously I need to have a technician look at it. I can't test the RAM because I don't have another RAM stick available. I can't check the CMOS battery because I don't have a good one handy to try out. Still, I'm glad this got me to start looking at current hardware.

---

