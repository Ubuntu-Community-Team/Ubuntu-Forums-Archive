---
title: "Neither bios or os registering all my ram"
date: 2019-12-25
forum: Hardware
---

### Post by chrisflanary on 2019-12-25
I have another ram issue. Im currently running memtest86 and am on pass 3 with no errors but am going to let it run overnight to be thorough. Memtest86 sees all 4 of my ram sticks and they are 4gb each. But memtest86,bios, and the os are all reading that i only have 8gb total ram. I have 16gb total, 4gb in each stick. Ive attached a screenshot of the in progress memtest86 test and circled that i have all 4 sticks being recognized at 4gb each but a total of only 8gb of memory and thats for everything ive used to check my ram info that I stated earlier. So what can I do to get all 16gb recognized if there are indeed no errors? [ATTACH=CONFIG]284681[/ATTACH]

---

### Post by QIII on 2019-12-26
Hello!

Would you please provide you machine specs, particularly the motherboard and the maximum memory it supports.

Cheers!

---

### Post by chrisflanary on 2019-12-26
Yes sorry. I should of stated that. I thought it went without saying but it's always a good idea to be thorough. So yes, my motherboard allows for a max of 16gb of ram to be installed. Hence why i cant figure out why the pc is only using 8gb. Thank you. 

Also, 13 hours in and 6 passes later, there are still no erors in memtest86. Gonna let ir run more while I'm at work today amd will update tonight.

---

### Post by CatKiller on 2019-12-26
> **chrisflanary said:**
> Yes sorry. I should of stated that. I thought it went without saying but it's always a good idea to be thorough. So yes, my motherboard allows for a max of 16gb of ram to be installed. Hence why i cant figure out why the pc is only using 8gb. Thank you. 

No, it really doesn't, and even if a motherboard can handle some RAM configurations that total 16 GB it doesn't mean that it can handle all configurations that total 16 GB. In particular, the motherboard may well not handle larger dual-rank modules. You'd need to consult the QVL for the motherboard to check, or provide the model number so someone else could do it for you as you were already asked to do.

---

