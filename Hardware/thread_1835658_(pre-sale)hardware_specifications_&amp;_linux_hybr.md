---
title: "(pre-sale)hardware specifications &amp; linux hybrid graphics"
date: 2011-08-29
forum: Hardware
---

### Post by askrym on 2011-08-29
Hello :-)

I need to buy a laptop pc and the problem i ran through is that no manufacturer on their website posts specific information about the peripherals the pc is equipped with.
you just find information like "internal wireless : b/g/n" and stuff like this ; but no clue about card manufacturer and chipset.
I have tried contacting but it's a big problem they are quite disinterested in providing previous-sale assistance .
I've also been told that some components may be different depending on the location :(
Does somebody know where i can find detailed information about laptop components before purchasing?:confused:

thank you):P

---

### Post by Firezap on 2011-08-29
Websites like Tigerdirect and newegg generally give very good descriptions about their computer`s hardware. Most the time though, you can just get the computer model and google it and you should get the specs you need.:popcorn:

---

### Post by .... on 2011-08-30
Yeah, it's extremely frustrating, especially with wireless adapters. If you want assured Linux compatibility, buy from a dedicated Linux vendor like System 76. I find HP to be the best big-time OEM in terms of disclosing technical info on their support site. You can usually look at the specification or driver download page for a given item and determine the chipset.

---

### Post by askrym on 2011-08-30
[SIZE=2]unfortunately there aren't good linux laptops producers in my country :(

I'm going to spam e-mails to the mail-boxes of the tech.assistance I guess :P

but this is the least .

I'd like to buy a Sony laptop SB series since I have quite big portability needs :)
[http://www.sony.it/product/vn-s-series/vpcsb2m9e](http://www.sony.it/product/vn-s-series/vpcsb2m9e)
but I am a little worried for one thing , this laptop like many other super-portable ones uses two graphical units, the one integrated into the sandy-bridge  i3-2310M that is , Intel® HD 3000 and the AMD Radeon&#8482; HD 6470M.
I've seen around that there are some software issues on linux with this Hybrid Graphics Technology but I've also been told that the hybrid system is supported by ATI Drivers on linux and that there shouldn't be any problems.

I've taken a look at the [http://linux-hybrid-graphics.blogspot.com/](http://linux-hybrid-graphics.blogspot.com/) as well to dig deeper into this matter before maybe making a mistake by flushing &#8364; into the W.C. ;
I'm quoting a little piece

[/SIZE]> [SIZE=2]ATI hybrid:
The PowerXpress pre-4.0 models have a mux solution to switch between
discrete and integrated card.
For most ATI/Intel hybrid configurations:

a) try the latest closed-source Catalyst Driver for login/logout card switching,
 or
b) try vga_switcheroo and open-source graphics drivers (kernel 2.6.35 or newer).

The PowerXpress 4.0+ models have a muxless solution to use both cards
and switch on/off the discrete card.
For Muxless PowerXpress 4.0+ models, please submit your DSDT tables
information as described here:
[http://linux-hybrid-graphics.blogspot.com/](http://linux-hybrid-graphics.blogspot.com/)
[/SIZE][SIZE=2]

[/SIZE][SIZE=2]now ; I've tried to get some information from the sony-customer-care but everything i managed to find out is that the Laptop Keyboard has a Button to switch from power saving (intel graphics) to performance (discrete ati graphic card) ,  I tried to ask if this was a hardware or a software handled matter but obviously got no certain answer. Moreover I do not even know if [/SIZE][SIZE=2][SIZE=2]VPCSB2M9E adopts a mux or a muxless mechanism.
[/SIZE][SIZE=2][SIZE=2]In conclusion it seems all a little confusing at least to me , so i've come writing here to seek some real feedback from someone who has actually tested a lot on this matter.
Does anybody have a similar laptop intel/ati hybrid graphics and can tell me if everything is working good?
also any tips are very welcome. :)
thanks very much.:popcorn:

ps. hope didnt run offtopic :S
[/SIZE][/SIZE][/SIZE]

---

### Post by .... on 2011-08-30
Catalyst/PowerXpress only supports switching between two AMD/ATI GPU's at this time: [http://www.phoronix.com/scan.php?page=news_item&px=OTcyMQ](http://www.phoronix.com/scan.php?page=news_item&px=OTcyMQ)

You can still switch between open-source intel and radeon drivers using vgaswitcheroo.

---

### Post by askrym on 2011-08-30
I guess it's going to be working fine then , and maybe future releases of ati drivers will support the whole by itself :)

thank you mr./miss "...." :KS

---

