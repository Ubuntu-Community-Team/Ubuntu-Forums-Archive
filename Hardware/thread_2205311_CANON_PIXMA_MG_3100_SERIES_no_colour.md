---
title: "CANON PIXMA MG 3100 SERIES no colour"
date: 2014-02-13
forum: Hardware
---

### Post by christon74 on 2014-02-13
Good morning  fellow-Ubunters :D

I have this all in one printer which perfectly fits my needs. The only problem is that when I load Ubuntu, it will only print in black and white_ Yet it says it is correctly calibrated (device color profiles). I am 100% sure I have the correct driver. So when I absolutely need to print anything in colour, I have to restart my system and load Vista Pro.
Once more, heartfelt thanks to anybody who has the solution to my printing problem.

With friendly greetings from the blue banana region (Lake Geneva)
Chris.
*Dual boot = Ubuntu 12.04 LTS / Vista Pro

---

### Post by aikishugyo on 2014-02-13
How will anyone be able to confirm anything if you do not give us any information?
Well, here is some from my side to help you: gutenprint 2.5.9 supports the MG3100, although experimentally.

---

### Post by christon74 on 2014-02-14
The printer is a CANON Pixma MG 3100 _ if that is ANY information; the OS is Ubuntu 12.04 LTS _ again, if that is ANY information and if you do not feel like helping me then why bother typing an answer?

---

### Post by christon74 on 2014-02-14
Erratum! The printer is a CANON PIXMA MG 3150. But the driver recommended is for MG 3100 series. I am just wondering if this could explain why the printer will not print colours?

---

### Post by aikishugyo on 2014-02-16
No, it is not ANY information: what is the driver you are complaining about?
PS time is precious, you should not feel offended at short replies.

---

### Post by christon74 on 2014-02-22
Canon PIXMA MG3100 - CUPS+Gutenprint v5.2.8-pre1

---

### Post by aikishugyo on 2014-02-23
Hi Christo,
OK, that is an old buggy driver, a pre-release of 5.2.8 (which quickly became a functionally identical 5.2.9 release), so the only thing I can tell you is that problems are expected and you need to use 5.2.9 before I can help you with debugging---provided the problem actually exists in the production driver.
I am sure there is a PPA with 5.2.9, please search the forums (or maybe someone else can answer), I compile my own but I would not expect you to try that unless there is no other choice.
Someone (Till Kampeter I presume) is actually packaging the latest 5.2.10 driver (no difference for the MG3100 so you do not need it) in case you want to test that.
Regards,
Gernot Hassenpflug

---

### Post by aikishugyo on 2014-02-23
Christo,
You might as well check your CUPS printing options, since if those are incorrect for color printing, a new driver will not help you. Canon printers do not permit free assignment of all the possible values, the firmware has specific input requirements which it is the responsibility of the driver to produce. CUPS on the other hand is one-way only, so no chance to get error messages from the printer, plus all options are exposed to the user in the PPD, so the driver code has to select defaults based on priorities (which is up to the driver code) if there are mis-matches in selections.

So, assuming you are printing on normal paper:
1. color model must be "RGB"
2. mode selection must be a color mode for the selected media, so no mode with "mono" in it (I don't remember what the exact modes were for pre-5.2.8). Probably "300x300 DPI" would be the best to test.
3. ink cartridge selection must be "both", not "black" and not "color"
4. media selection must be "plain"

In 5.2.9 the logic for default modes depending on the other selections, and the matching of other selections if a specific mode is chosen (a specific mode chosen generally takes priority, unless incompatible with the selected media or simplex/duplex choice which is not relevant for the MG3100), is completed, but it certainly was not in 5.2.8.

Regards,
Gernot Hassenpflug

---

### Post by christon74 on 2014-02-25
Yep! RGB. Cannot choose both 'black and colour' 
The only options given are 'color' or 'monochrome'
have changed to 300X300 dpi but have not yet printed a test page. will do it presently. Still no colour. As for the Gutenprint 5.2.9, it is simply just not there. I have looked for it using the synaptic package manager. I do not see any solution. I am glad I am on dual boot and can resort to Vista when I need print things in colour.....

---

