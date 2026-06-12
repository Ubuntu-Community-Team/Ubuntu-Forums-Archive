---
title: "Memory test shows errors"
date: 2008-07-30
forum: Hardware
---

### Post by RyanVanDiemen on 2008-07-30
Hi guys, recently I bought new MB with CPU and memory. After installing ubuntu I had a weird lines on screen (as somebody draw the lines with blue pen...), wasnt a driver problem because I had them in BIOS too. Firstly I thought the error might be with IGP, so I bought the card for PCI-E, but then even weirder things happened. The ubuntu wouldn`t load at all showing some errors, if I solve one another comes out... Than I realized it might be some memory problem. I moved it to second B slot and these lines disappeared in BIOS but ubuntu still couldn`t load. Than I ran the memory test (the one on Live CD`s initial menu) and it showed hundreds of errors (in both slots). Do you think this is the slot problem or the memory? Or is it somewhere else (e.g. 300 W ATX should be enough, but am not sure). I tried to load both 32 and 64-bit system. If I try to install windows (that`s how desperat I am), it stops when copying files to hdd with error, it can`t copy the file and if I hit escape blue screen comes out...

This is my configuration:
Athlon X2 64-bit
MB: Asus M2N-MXSE PLUS with Nvidia GeForce 6100/nForce 430
1GB Apacer UNB PC2-6400 DDR2/800
Barracuda SATA 120 GB HDD
WD IDE 320 GB HDD
1 DVD RW
ATX 300 W

Thanks guys...

---

### Post by Kevbert on 2008-07-30
I've had this problem in the past.
1. Are you taking antistatic precautions when installing/removing the memory ?
2. Try just fitting one memory module at a time.  If the memory fails try it in another slot.  It can be possible to fit the memory so it's not seated properly (this was my 'frustrating' problem).  Each time run the memtest for several passes as it may fail as it warms up.
3.  If a memory chip works in a certain slot try the suspect memory in that slot and try the the good memory in a bad slot.
If the memory is new, can you take it back to the place where you bought it and get them to check it.
Good luck.

---

### Post by RyanVanDiemen on 2008-07-30
Thank you for your reply Kevbert. The problem is I have only one memory... Yes I tried to re-install the memory few times in each slot. The problem is that it shows this screen lines only when in A slot. It doesn`t show those lines when it`s installed in second slot, however fails memtest in each of them... I`m afraid that the A slot might be somehow corrupted and because I had the memory in this slot it might corrupted the memory itself and that`s why it fails test in second slot... Yes, I bought it just last weekend, the problem is that it was 250 km from where I live, I`m going there in September, so until then I`d like to find out if someone else has this experience... The weird thing is that WinXP installation fails every time while copying files...and every time it fails on different file (CD is absolutely clean...). Not sure if also this might be caused by memory...

---

### Post by Kevbert on 2008-07-30
Can you check the power requirements of the motherboard in particular ?  300W nowadays is quite a low rated PSU and graphics in particular takes up a lot of power.  What I suggest you try is to fit the memory in slot A and run a memory test noting where the first errors occur.  Take the memory out of slot A and then refit it and see if you get errors at the same place. If you get inconsistant errors that will confirm a badly fitting memory chip.  If you get a consistant error that could still be a damaged socket or even a damaged (cracked) motherboard track as well as memory.  If by moving the memory to another socket you get errors occurring at the same start point it suggests the memory is faulty.

---

### Post by RyanVanDiemen on 2008-07-30
Power requirements should be enough because on specs it shows 300 w as enough. I didn`t see exactly where the memtest errors occur as there was hundreds of them (they just rolled on the screen), but I will check when I come home today if they start occuring in both slots at the same place... Thanks, I`ll post the results tomorrow...

---

### Post by RyanVanDiemen on 2008-07-31
Hi, I checked the memorty test, where the errors start occuring. In Slot A they start around 890 MB in slot B around 760MB. Does this confirm that the slots on MB don`t work correctly and memory is actually correct?

---

### Post by Kevbert on 2008-07-31
Hi.  It suggests that the memory might be OK, but it looks more likely that the connection between the slot and the memory is the problem.  Sorry for being so vague. The connections on both the connector and memory should all be bright and shiny (be careful not to touch either of these with your fingers.  The connection is normally quite tight between the two, you may have to press down quite hard to fit the memory into its slot (but not too hard as you could crack the motherboard circuitry).  Is there anywhere you can get the memory checked (friends for example) ?  The initial POST test (when the PC is turned on) is not good enough, you need to run a longer test.

---

### Post by RyanVanDiemen on 2008-07-31
Hi, thank you for your reply. I ran the test from the Ubuntu CD memory test not the one when the computer boots-up. I think this test is quite long (it ran for 10 minutes, then I just turned it off as it showed over a million errors...). Also I pressed the memory quite hard into each of the slots quite a few times, so the problem shouldn`t be there. Yes, you`re right, I will have to check the memory on some other computer. Thanks for now, I`ll keep you updated :)

---

### Post by Kevbert on 2008-07-31
Your welcome. Hopefully it is just the memory.

---

### Post by RyanVanDiemen on 2008-08-04
Hi, I gave the memory to my friend to check, but it didn`t fit into his computer as he doesn`t have ddr2 slots on his MB... Unfortunately I will have to wait until September when I will be able to go to the shop where I bought it all...

---

