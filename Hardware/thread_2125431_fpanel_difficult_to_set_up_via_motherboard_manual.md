---
title: "fpanel difficult to set up via motherboard manual"
date: 2013-03-14
forum: Hardware
---

### Post by Palu on 2013-03-14
I know this isn't strictly Ubuntu, but it's for a server that will be Ubuntu and you are my favorite people. If this is inappropriate, let me know, but I didn't see anything against it in the stickies here... I am trying to connect power led and power button to the fpanel header pins, but my manual is not something I'm used to.

See png attachment from manual: [ATTACH=CONFIG]240151[/ATTACH] 

I understand from this how to number the pins (1 to 7, then the next row 8 to 15). However, I don't understand where to plug the stuff in. Is the pin number in the table referring to the positive (colored) cable on the two connectors? Does the negative go on the next pin on the same row? That would place power positive on pin 6 and power negative on pin 7. Then I look at power led and see it's on 5, which suggests by my earlier logic that the negative would go on the 6, which is taken. Therefore, I turned to Google, and everything either referred me to the manual (heh) or had information on less obscure motherboards (it's an Epia M910 for super low power consumption).

My understanding of the fpanel headers:
08 09 10 11 12 13 14 15
01 02 03 04 05 06 07 NA

Or Perhaps I'm mistaken and it is...
02 04 06 08 10 12 14 16
01 03 05 07 09 11 13 NA < Is that what "keyed means? 

Plug-in are both 2 pins...
Power Button: + -
Power LED: + -

If it's the second case, is power led...
02 04 06 08 10 12 14 16
01 03 0+5 0-7 09 11 13 NA
and power button...
02 04 0+6 0-8 10 12 14 16
01 03 05 07 09 11 13 NA
?

Thanks for your help! I hope my diagrams help you answer. :KS

---

### Post by Cheesemill on 2013-03-14
> **Palu said:**
> 02 04 06 08 10 12 14 16
01 03 05 07 09 11 13 NA < Is that what "keyed means? 

Correct.

Power button should plug into 6 and 8 (it doesn't matter which way round as it is only a switch).

Power LED should plug into 5 and 7 (- in 5, + in 7).

---

### Post by Palu on 2013-03-14
Thank you VERY much, Cheesemill. I appreciate the help.

---

