---
title: "Toshiba x200-16z microphon not working on ubuntu 11.04"
date: 2011-09-04
forum: Hardware
---

### Post by simcomp2003 on 2011-09-04
The Toshiba x200-16Z sound working on the front speakers and headset,  but microphone is not working. I tried all modes for the ALC268 codec. This laptop has 4 front ports, two speakers and subwoofer(harman/kardon), internal microphone, cam, TV-out, HDMI, 6xUSB.... I also tried options:

ALC267/268
 843           quanta-il1    Quanta IL1 mini-notebook
 844           3stack        3-stack model
 845           toshiba       Toshiba A205
 846           acer          Acer laptops
 847           acer-aspire   Acer Aspire One
 848           dell          Dell OEM laptops (Vostro 1200)
 849           zepto         Zepto laptops
 850           test          for testing/debugging purpose, almost all controls can
 851                         adjusted.  Appearing only when compiled with$CONFIG_SND_DEBUG=y
 853           auto          auto-config reading BIOS (default)


3stacks-6ch
3stacks-6ch-dig
probe_mask=1
probe_mask=2
probe_mask=8
position_fix=1
position_fix=2
position_fix=3

but nothing ...

I need help to properly configure this toshiba, it is great laptop and is working super with ubuntu exsept microphone.

---

