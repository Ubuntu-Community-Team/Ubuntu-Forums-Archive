---
title: "smartcard laptop no access empty card"
date: 2006-06-04
forum: Hardware &amp; Laptops
---

### Post by Gossie on 2006-06-04
Hi,

My Acer Travelmate 610 is blocked by the smart card thing.

I had it repaired and then they loosened the Bios battery for a short time, and now the smartcard block has turned on.

But I never used the smartcards: they are empty. At least they don't work, whichever way I stick them into the laptop (upside down, :(  backside first).

I have a password on the harddrive, (thanks to the ubuntuguide.org!) but now I cannot reach my harddrive, and I cannot reach the Bios as well. The computer asks for the smart card before I can get into the Bios or load a cd rom.

So I called the Acer office here in the Netherlands and they said I had to go to this company in another city. I asked how much the unblocking costs and they ask me more then one hundred euro's (abuot one hundred US Dollars) to unblock the laptop. Shops that sell Acer, I called to them too, but they say they don't want to open the laptop. 

Does anyone know a non-mafia solution to this problem? It has nothing to do with Ubuntu, of course. But I want my Ubuntu laptop back! Now I only have an old Mac (so I'm still lucky to have a computer at all).

Lucas

---

### Post by Gossie on 2006-08-17
I've hade two reactions via e-mail. Soon a friend will try solution number one for me.

1.
'I had to go into the laptop and turn off the card using the internal dip
switches. I don't know which switch it was but you can disable the smart
card completely. That's what I chose to do as I didn't want this to happen
again unexpectedly. Sorry I can't be more specific.' (D.W.)

2.
'Now and then I get questions about this. The only solution I could find
was to make Acer disable the feature, while having it on repair.
Involves having them label it as "stolen", for some strange reason. Anyhow,
after that the laptop lasted only half a year. Not using Acer laptops
anymore now.' (A.N.)

---

### Post by nonameleft on 2006-08-30
Gossie,
Having the same problem, tried the DIP switches (located under the keyboard) 1 block X 4 switches all off as default, I was able to get past the "insert smart card" message and into set up .... BUT now the hard drive isn't found! Let me know if you come up with a solution, I'll do same. Also tried taking out the card socket but still askes for the card. Nothing in the set up screens to disable."Emergency card" is crap as well.

---

### Post by Ogami Ito on 2006-10-09
^^^^Posting to confirm that this does work. 

This is what I think happened. I painted some of the laptop and while seperating the 2 halves you are forced to unplug the bios battery which will trigger the PlatinumPAS "security" features when you turn it on again. 

Here is what to look for. You will find the 4 switches under a useless piece of metal which I assume is there just to cover its location, I couldnt find another purpose for it other then that. Sorry about the bad images, hope this helps. 

[IMG]http://robotinstitute.com/comp1.jpg[/IMG]
I left the smartcard drive unplugged at this point, I dont know whether it needs to be or not for it to work, I didnt test it.

[IMG]http://robotinstitute.com/comp2.jpg[/IMG]

I will assume also that this would probably work on any laptop with PlatinumPAS, so much for your corporate secrets being safe.

---

