---
title: "Inspiron 6000, Feisty, Suspend and SD/MMC slot"
date: 2007-04-27
forum: Hardware &amp; Laptops
---

### Post by ianmac on 2007-04-27
Hey folks,

So I upgraded to Feisty, and it worked great!  My suspend issues were finally resolved, so I could suspend and resume without problem.

Until a week or so ago.  I tried suspend and it didn't power off.  Strange.  I didn't have time to investigate further until later.  When I did, suspend worked without any problem.

Then, it happened again.  Suspend would again do what it did before - it would seem to put all its software in suspend state, it would remove my wireless driver, and would blank the screen and power it off (the backlight was off and all).  But it would hang there.  The power would be on, but everything else would be off.  Oh no.

After trying to look through the logs and not being able to locate what was going wrong, I was frustrated.  But, somehow, I randomly discovered that the problem was related to my SD/MMC slot.  If I remove the card from the slot, then I can suspend without and trouble.  If I have the card in, it behaves as described above.

Tests that I did:
powering up, and then suspending without inserting the card - everything works as expected.
powering up, inserting the card, removing the card, suspending - everything works as expected.
powering up, inserting the card, unmounting the volume, suspending - doesn't work, as above
powering up, inserting the card, suspending - doesn't work, as described above

So, I think I have isolated the problem as being caused by the built-in card reader.  Okay.  But how do I fix it?  Is there a module that I could add to my hibernate/ram.conf file so that it would remove the module?  I wouldn't think that this would do it since if I remove the card the module is still there.  But maybe it would?

Any suggestions?
Ian

---

### Post by king_growler on 2007-04-27
> **ianmac said:**
> Hey folks,

So I upgraded to Feisty, and it worked great!  My suspend issues were finally resolved, so I could suspend and resume without problem.

Until a week or so ago.  I tried suspend and it didn't power off.  Strange.  I didn't have time to investigate further until later.  When I did, suspend worked without any problem.

Then, it happened again.  Suspend would again do what it did before - it would seem to put all its software in suspend state, it would remove my wireless driver, and would blank the screen and power it off (the backlight was off and all).  But it would hang there.  The power would be on, but everything else would be off.  Oh no.

After trying to look through the logs and not being able to locate what was going wrong, I was frustrated.  But, somehow, I randomly discovered that the problem was related to my SD/MMC slot.  If I remove the card from the slot, then I can suspend without and trouble.  If I have the card in, it behaves as described above.

Tests that I did:
powering up, and then suspending without inserting the card - everything works as expected.
powering up, inserting the card, removing the card, suspending - everything works as expected.
powering up, inserting the card, unmounting the volume, suspending - doesn't work, as above
powering up, inserting the card, suspending - doesn't work, as described above

So, I think I have isolated the problem as being caused by the built-in card reader.  Okay.  But how do I fix it?  Is there a module that I could add to my hibernate/ram.conf file so that it would remove the module?  I wouldn't think that this would do it since if I remove the card the module is still there.  But maybe it would?

Any suggestions?
IanCheck to see if module "tifm_sd" is loaded, and if so, add that to the MODULES section of "acpi-support" -- I had to do that on my Edgy installation. Good luck!

---

### Post by cshen12 on 2007-04-30
I installed feisty on my Inspiron 9300 and removing he SD/MMC card from the slot worked for me, too.  

Thanks,
Chris

---

### Post by blakegrover on 2007-06-05
I have a inspiron 9300 and I am running feisty and I had never been able to get it to standby but removing my sd card it works great!  I looked to see if that module "tifm_sd" was loaded and it isn't.

Does anyone know how I can get it to standby with a sd card?

Thanks
Blake

---

