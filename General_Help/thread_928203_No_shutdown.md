---
title: "No shutdown??"
date: 2008-09-23
forum: General Help
---

### Post by Monotoko on 2008-09-23
My laptop computer has been on for 24 hours, whilst i tried to figure out where my shutdown button had gone.

The day before yesterday i tried to shut it down, and it got stuck half-way through, i had to hold the power button down.

i rebooted it, and found myself without a shutdown or restart button when i clicked the shutdown button at the top right.

Stumped, i went into the terminal, and tried to shut it down that way to see if the command was still on here.

As expected, it started closing down, came up with the end screen (where the bar goes down) but it got stuck VERY, VERY near the end, and once again required a hard reset as it got stuck very near the end.

I reset it, turned it back on again, and tried to login under my main account, it wouldnt work, luckily i had a secondry, and that logged in.

Wondering why the other account hadnt logged in, i went to /home under sudo and directory checked it, the other account didnt exist.

So yeah, here i am, no option to shutdown, my laptop has been on for 24 hours now, i tried everything, i dont want to attempt to shutdown again, in case it needs a hard-reset again, because i think that could be what nackered it in the first place....

Whats the problem? why does ubuntu refuse to shutdown safley?
thanks in advance, cos this has me completly stumped...

---

### Post by Monotoko on 2008-09-23
My laptop is getting rather warm....any help?

---

### Post by Steve1961 on 2008-09-23
> **Monotoko said:**
> My laptop is getting rather warm....any help?

Try this:

sudo touch /forcefsck

and then:

sudo shutdown -h now

This should force a disc check on reboot

---

### Post by Monotoko on 2008-09-23
It got stuck on shutdown, i did the disk check, it reported nothing, but it still gets stuck upon shutdown, is there any way i can see whats happening when it gets stuck? the code instead of the image

---

### Post by Monotoko on 2008-09-23
please?

---

