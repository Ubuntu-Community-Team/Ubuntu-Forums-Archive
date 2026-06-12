---
title: "Brother printer stopped after Feb 23, 2010 update"
date: 2010-02-24
forum: Hardware
---

### Post by rewyllys on 2010-02-24
Sometime during the morning of Feb 23, 2010, I accepted Update Manager's updates on both my desktop and my laptop, both of which are running  Karmic and both of which have been regularly updated by Update Manager.

Before the updates, which I think I saw included an update to CUPS, my Brother MFC-8820D printer had been running satisfactorily.  Since the updates, all the printer yields, in response to my attempts to print from either my desktop or my laptop, is the following six lines:

ERROR NAME;
      configurationerror
COMMAND;
      setpagedevice
OPERAND STACK;
      --dicttype---

Any suggestions will be greatly appreciated.  Assuming I'm correct that CUPS was updated yesterday, is there some way to find out what the latest CUPS update involved, and/or how to return to a prior version?

---

### Post by tcchris on 2010-02-24
I have a mfc465cn printer , I am running update now , but I didn't notice a cups update .
After the update I will post if my printer still works .
Your next step , to me would be to go to cups interface and reconfigure your printer .
localhost:631

---

### Post by tcchris on 2010-02-24
I can confirm that after the update my printer still works 
Mine is networked

---

### Post by rewyllys on 2010-02-24
After I posted this problem also in the Installation & Upgrades section, bumanie was kind enough to post the following:

> **bumanie said:**
> Once had a similar problem (not the exact same error output) with a HP printer - I uninstalled the printer and then reinstalled it by letting ubuntu search for the printer and then drivers without any user input. The printer now works fine. Can't promise it will work in your situation, but might be worth a try.
                                                                                               __________________
                Windows is the best virus detector on the market!
Ubuntu attracts Human Beings - Windows attracts viruses and worms

Bumanie's suggestion worked beautifully on both my desktop and my laptop!:popcorn:

Why couldn't I have thought of this myself?:(

My thanks go also to tcchris.:D

---

