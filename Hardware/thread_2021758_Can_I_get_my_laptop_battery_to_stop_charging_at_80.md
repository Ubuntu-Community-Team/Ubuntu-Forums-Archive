---
title: "Can I get my laptop battery to stop charging at 80%?"
date: 2012-07-09
forum: Hardware
---

### Post by jonnyboysmithy on 2012-07-09
After reading _this article_, I decided I wanted to charge my laptop battery only to 80%  to prolonging battery life.

Here's a graph of what the expected cycle life would be: (theoraticaly, note that  practice and theory are never the same :D) 
[CENTER]                   
[/CENTER]
                                           [CENTER]                   
[/CENTER]
                                           [CENTER]                    
[/CENTER]
                                                                [B]Table 4: Discharge cycles and capacity
                    as a function of charge [/B]
                       
                                                                                                                       **Charge level **(V/cell)                      **Discharge cycles**                      **Capacity at full charge**[CENTER]                                                                                                          [4.30]                   [150 &#8211; 250]                                                                                [110%][/CENTER]
                 [CENTER]                                                                                                    **4.20      **              **300 &#8211; 500  **                                                                              **100%**[/CENTER]
                 [CENTER]                                                                                                       4.10                  600 &#8211; 1,000                                                                                  90%[/CENTER]
                 [CENTER]                                                                                                    4.00                 1,200 &#8211; 2,000                                                                             70%[/CENTER]
                 [CENTER]                                                                                                       3.92                 2,400 &#8211; 4,000                                                                           50%
[/CENTER]
                                                
[CENTER]              Every 0.01V drop below 4.20V/cell doubles the cycle; the  retained  capacity drops accordingly. Raising the voltage above  4.20V/cell  stresses the battery and compromises safety.
[/CENTER]

Is there any way I can do this?
Greetings and thanks for looking. :)

EDIT: Hardware is Hp Pavilion DV-6023TX

---

### Post by Redblade20XX on 2012-07-09
I don't think its possible through software since charging is usually done through hardware circuitry. 

- Red

---

### Post by jonnyboysmithy on 2012-07-09
I have found this:[http://askubuntu.com/questions/34452/how-can-i-limit-battery-charging-to-80-capacity](http://askubuntu.com/questions/34452/how-can-i-limit-battery-charging-to-80-capacity)
It can be done on thinkpads: [http://www.thinkwiki.org/wiki/Tp_smapi](http://www.thinkwiki.org/wiki/Tp_smapi)
> The charging thresholds are, very unfortunately, firmware and vendor specific.

---

### Post by Redblade20XX on 2012-07-09
> **jonnyboysmithy said:**
> I have found this:[http://askubuntu.com/questions/34452/how-can-i-limit-battery-charging-to-80-capacity](http://askubuntu.com/questions/34452/how-can-i-limit-battery-charging-to-80-capacity)
It can be done on thinkpads: [http://www.thinkwiki.org/wiki/Tp_smapi](http://www.thinkwiki.org/wiki/Tp_smapi)

Wow! You learn something new each day. :)

Thanks jonnyboysmithy! ;)

- Red

---

### Post by jonnyboysmithy on 2012-07-12
Good!:popcorn:

Bump, anyone know anything else? I'm keen on learning more :)
EDIT: and finding a way to answer my question

---

### Post by jonnyboysmithy on 2012-07-13
Bump

---

### Post by kigconker on 2012-07-13
My computer has it as a BIOS option, and every other time I have seen it was similar. Considering that a battery will charge without a os, there is nothing you can do if your bios doesn't support it. You could probably find a Bios that supports your hardware to replace your current one, but I wouldn't recommend this if you are not a software engineer.

---

