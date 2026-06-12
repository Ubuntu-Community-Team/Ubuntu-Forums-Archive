---
title: "Kitty knocked over external HDD, is it ok?"
date: 2023-05-07
forum: Hardware
---

### Post by kpatz on 2023-05-07
I was running a backup of my main file server to an external 12TB Seagate HDD (model STKP12000400) when my 9 month old kitten knocked the external drive over.  It sits vertically normally so it tipped over and landed on its side on the desk.

The drive made noises like it does when it first powers up (head unparking etc.) so I'm guessing an internal accelerometer sensed the tip and put the drive into a protection mode momentarily?  Once it went through its restart cycle it resumed receiving my backup seemingly unharmed.

I'm running an extended SMART self test on the drive now, to make sure there's no damage or bad sectors created by the fall.

This isn't my only backup so if it does fail it's not the end of the world, but I'd like reassurance that it's going to be ok (or not).

Thanks...

---

### Post by QIII on 2023-05-07
Modern rust has more built-in protections (like head parking) than 30 years ago.  Modern disk management tools are better able to make adjustments.

Let see what the testing tells you.

As for the kitty ... a small squirt bottle full of water is a great training aid.  :twisted::twisted:

---

### Post by kpatz on 2023-05-08
The drive passed the SMART long test without any errors.  I think it&#8217;s ok.

My concern was that the drive was writing at the time it was knocked over.  I guess I was lucky that time.  I should hook it up and run a zpool scrub on it to make sure no other corruption occurred.

As for kitty, she&#8217;s adorable so she gets away with it. :)

---

### Post by TheFu on 2023-05-08
I had a new HDD fall off the top of a tower case while I was still setting up the partitions - before there was any data.  It never worked again.  Fortunately, the credit card I used has 100% replacement within the first 90 days for failed purchases.  10 minutes to fill out online forms and a few days later, they'd credited my account for the cost.  

STKP12000400  hummmm.   [https://arstechnica.com/gadgets/2023/05/hdds-typically-fail-in-under-3-years-backblaze-study-of-17155-drives-finds/](https://arstechnica.com/gadgets/2023/05/hdds-typically-fail-in-under-3-years-backblaze-study-of-17155-drives-finds/) doesn't have that specific model, but it would be worth your time to look at the failure rates so your future decisions are based on performance across the vendor's line.

---

### Post by SeijiSensei on 2023-05-09
I just shipped my new 14 TB Seagate for replacement after it fell. I have a 2 TB Seagate in the cigarette-pack format. It seems invulnerable to physical shocks, and it's had quite a few! Not so it's big brother.

---

### Post by kpatz on 2023-05-13
Long SMART test and zfs scrub both passed.  Looks like the drive is ok (for now).

I have two of them, so I do have redundancy.  It only tipped over on the desk, it didn't fall off the desk onto the floor.

---

