---
title: "PC won't accept RAM upgrade. Hardware fault, wrong RAM or RAM too big?"
date: 2014-04-29
forum: Hardware
---

### Post by benawhile on 2014-04-29
Hi
 I have Ubuntu 12.04 and windows XP dual boot and have been preparing to replace Ubuntu 12.04 with 14.04, and from 32 bit to 64.
 I bought 2x2GB RAM cards from Crucial to replace the current 1GB
 Current SWAP size is 2.5GB

 When I booted the new cards I got to the 5 dots loading, but before the login screen I then hung at a black screen with a list of processes that had been going on, the last one was &#8243;stopping System V run level compatibility&#8243;. There was a flashing cursor which didn't respond to keyboard input.

 I forced stop and tried Windows, which loaded but hung just before the welcome screen, with just a multi colour mess of broken graphics

 Put the old cards in, got the login screen, before I logged in to desktop I tried waggling the corners of the RAM cards, (I wear an earthing strap) and something, maybe the waggling, caused a reboot.

 Tried new cards once more to make sure, and tried waggling them too, but no change.
 
 Old cards again, this time not recognised , stalled, presumably on the POST, with an intermittent long bleep. Same happened again when RAM was removed as a check.
 Removed and replaced more carefully, this time got to desktop, but had a couple of error messages,   the first was something like  
 &#8243;cupsd internal error&#8243;
 Then  &#8243;colord&#8243; error, (see screenshots)

 After that it worked OK for an hour, but had to force shut down again once with a hang on broken graphics. Up and in use now. (This is all on the original cards, which had been OK.)

 I can only think of the following possible causes:

 Is this happening because I haven't increased the SWAP partitions to match the bigger RAM? And is it happening in Windows too because the RAM is too big? I have read that Windows XP can't see RAM that is over 3GB.

 Have I got the wrong RAM? (unlikely, I have used Crucial before and found an exact match for my mobo.)

 Is there a physical connection problem with dry joints on the mobo, or loose/dirty edge connectors?
 The system was put together 7 years ago but hasn't suffered any physical abuse that I know of.

 Combination of these?

 I realise I will have to tackle a physical connection problem myself, but can anyone confirm whether the RAM *should* be accepted under the circumstances?

---

### Post by Allavona on 2014-04-29
What is the maximum amount of Ram that your system can make use of? This is regardless of the OS. You may have exceeded it.

---

### Post by sammykur on 2014-04-29
If I rember correctly  sometimes manufactures of MB will upgrade the bios to accept more memory.
Check your bios settings  and see if the bios see both the old and new memory,then check which bios version you have and go to the manufactues website and see if any of the upgrades included a larger memory update.
Do not udate your bios if you dont have to and dont try doing it if you are uncomfortable in any way with it.

---

### Post by sammykur on 2014-04-29
It may be helpfull to post your MB model as well as that of the RAM

---

### Post by benawhile on 2014-04-30
Allavona, I don't know what is the maximum the system will take, but the shop that sold me the mobo has told me that it almost certainly won't take 4G RAM. I don't understand why Crucial supplied me with these 2G cards when they don't work with the mobo. Do you know of an on line source that gives reliable info about compatibility of RAM cards with mobos?
There is a post on the MSI forum that says the board won't take more than 1GB per slot.

Sammykur, My mobo is the MSI K9VGM-V. The RAM supplied is labelled 2GB 240 pin unbuff DIMM 256MX64 DDR2 PC2-6400.
I looked in the BIOS for both sets of cards. 
With the original RAM in Standard CMOS system info said total memory 1919 MB
With the 2x2G in, said total memory 2927, so didn't see all of it.
How about if I used one 2GB card and one 1GB?
I am still on 32 bit, and was going to upgrade to a 64 bit download of 14.04. Do you have an opinion on whether I should go for 64 bit.

So it looks like I am back to 2GB RAM. The pc failed to see the old RAM twice again today, I reseated the cards and then changed them round and they were recognised third attempt, and there was an error message when desktop loaded. They are not a matched pair. Could these error messages be due to the pc being confused by the different RAM cards, or a connection problem?

Best news is that Crucial have kindly offered to refund me for the 2GB cards.:p

---

### Post by benawhile on 2014-04-30
Just looked in the manual that came with the board, which says it supports memory size up to 2GB. lessons learned
Long version: Consult the board manufacturer, not the RAM vendor!
Short version: If all else fails, read the instructions.

---

### Post by sammykur on 2014-04-30
If the old pair was in before I dont see them being mismatched causing the problem you have. Take a can of air and blow out your ram slots just to be sure they are clean(as well as the ram itself)also make sure the locks are fully engaged. I think when I first started with hardware I had a similar problem and the locks weren&#8217;t fully engaged although they did seem to "engage" when i put them in. 
Best off to take the memory back and save the money,but you can try to see if the os would see the 3 gigs (the bios appears to be reading) and go from there.First try getting the old memory to work (sounds like a dirty slot.)

 Also download memtest86 and run it at boot with both sets of Ram

---

### Post by benawhile on 2014-05-01
Thank you Sammykur. I had already blown out the slots, pc has been OK and firing up properly since I put the old RAM back in. To be honest I don't want to risk any further problems if I do try it with 3G, since the MSI manual says it won't support it and I have been offered a refund, so I reluctantly leave it as it is.

---

### Post by Yellow Pasque on 2014-05-01
Please mark thread SOLVED.

---

### Post by benawhile on 2014-05-01
I've been trying to find out how!!! How do you do it?

---

### Post by Yellow Pasque on 2014-05-01
It's under the "Thread tools" menu towards the top.

---

### Post by sammykur on 2014-05-01
Probably your best bet,save the money. glad you got it back working.(I would still run the memtest86)
To mark solved go to the upper right-hand corner under the search and there marked tools is what you use.

---

### Post by benawhile on 2014-05-06
Well, curiosity did get the better of me and I tried replacing just one of the old cards with one of the 2G cards, in what should be the DIMM 1 slot according to the user guide. No joy, I got the repeated long bleep which I assume meant that the RAM wasn't recognised, although I did once get that long bleep with the old mismatched cards too, until I reversed their positions. It was nagging me that I ought to try that and now I have.

---

