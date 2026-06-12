---
title: "Bridging Graphic Cards"
date: 2015-04-27
forum: Hardware
---

### Post by Jerid_Hill on 2015-04-27
I built a system running Ubuntu 14.04 LTS and it's running pretty good. I'm using the ASRock Z77 Extreme6 motherboard along with 3 Twin Frozr III 7950 Graphic cards. I had to power the sli slot on the board in order for the cards to keep up. Since then everything has been running smoothly. I am a little confused though, the graphic cards appear to have what I believe is sli/crossfire on them and the main board does support sli/crossfire. Neither MSI nor ASRock was helpful in inquiring on linking these cards. I couldn't even get the proper connection named from the board. I believe they are crossfire but I'm not 100% sure. I purchased sli bridges, but they are too narrow, the cards seem to have 21 pins on the ports. Either way, after viewing other builds that use these cards, no one seems to be bridging them.

Does anyone know if there is a big difference running with or without the bridging. The cards have 2 ports with a 1 or 2 switch. I've seen where people had bridged the first ports on the 1st and 2nd card, the 2nd ports on the 2nd and 3rd card and the 2 port on the 1st card and the first port on the 3rd card. If I do this, I'm wondering how to configure each card with the 1 or 2 switch.

Sorry for the jumbled questions, it just isn't clear and there doesn't seem to be any help or understanding from the manufacturers.

---

### Post by QIII on 2015-04-27
Hello!

SLI connectors are for NVIDIA products.  The technology for AMD is Crossfire.  They are not interchangeable,  so the SLI connectors would not be expected to fit your AMD cards.

The open source Radeon driver does not support Crossfire ghat I know of.  Are you using the proprietary AMD fglrx driver?

---

### Post by Jerid_Hill on 2015-04-27
Thanks for the response. Up to this point, I had been using native drivers. MSI supports crossfire as well as my mainboard. The SLI comment helps! MSI told me to get an SLI bridge made by them. That's what I did and found out they were not correct and why I assumed it was Crossfire.

MSI R7950 Twin Frozr 3GD5/OC Radeon HD 7950 3GB 384-Bit GDDR5 PCI Express 3.0 x16 HDCP Ready CrossFireX Support Video Card

ASRock Z77 Extreme6: Supports AMD Quad CrossFireX&#8482;, CrossFireX&#8482; and NVIDIA® Quad SLI&#8482;, SLI&#8482;

---

### Post by QIII on 2015-04-27
Definitely would need the Crossfire bridges for those cards, BUT:

Crossfire support for Linux is not pretty.  (SLI for NVIDIA is not any better looking, as far as I know.)

I've used multiple cards as computing units running OpenCL before and that doesn't work at all with Crossfire.
  
For graphics, it is hit or miss.  Take a look at AMD's official FAQ [here]("http://support.amd.com/en-us/search/faq/246"). 

If that means anything at all to you, you're a step ahead of me.

That said, you can use multiple cards and drive multiple monitors with the AMD driver by initializing them all

```
sudo amdconfig --initial --adapter=all
```

But that won't get Crossfire working to link them all together to give you output all back to one card.

Eyefinity works just fine to run multiple monitors in a single desktop on Linux.  So, if you had 4 of the cards with 6 DP outputs, all cards initialized, you could run a monster desktop with 24 monitors (provided your PSU could power all the cards).

Crossfire is a different beast.  There you are trying to combine the horsepower of multiple cards to have all the output go to one card -- and however many monitors it is driving.

---

