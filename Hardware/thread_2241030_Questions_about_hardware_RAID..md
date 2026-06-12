---
title: "Questions about hardware RAID."
date: 2014-08-23
forum: Hardware
---

### Post by josephellengar2 on 2014-08-23
Hi!

I'm creating a RAID 1 setup for my HTPC using [this external enclosure.]("http://www.amazon.com/gp/product/B0089V4WOC/ref=ox_sc_act_title_1?ie=UTF8&psc=1&smid=ATVPDKIKX0DER")

I have two questions about this:

1) I am planning on rotating out three discs. I will keep one in my safe and alternate the other two. Suppose that I have discs A and B in the enclosure (identical), and I then swap A for C. Since C is out of date, will the system automatically update C to have the same content as B? Or, alternatively, would it "update" B to have the same content as C? Or neither?

2) I assume that Ubuntu will "see" the two drives as a single volume. How can I be sure that neither one has failed at any given point? Will the hardware warn me? Or will the software?

Anyway, I couldn't find the answers to these questions online. Any help would be great! Thank you!

---

### Post by gordintoronto on 2014-08-24
Can you find the manual for the device online? It should tell you how the device notifies you that a disk has failed.

Good idea to have three identical drives. Keep the third one safe until one of the others dies, then try to buy another similar drive. The approach you described can only cause trouble.

Note that RAID is not backup. If you delete a file, then decide you want it back, RAID won't help you.

Have you read the reviews on Newegg?

---

### Post by josephellengar2 on 2014-08-24
> **gordintoronto said:**
> Can you find the manual for the device online? It should tell you how the device notifies you that a disk has failed.

Good idea to have three identical drives. Keep the third one safe until one of the others dies, then try to buy another similar drive. The approach you described can only cause trouble.

Note that RAID is not backup. If you delete a file, then decide you want it back, RAID won't help you.

Have you read the reviews on Newegg?

Thanks for your response, gordintoronto.

1) I haven't been able to find the manual. I looked. It does, however, look like the device has warning LEDs on the front, so that's probably what those are for.
2) Thanks for the warning about RAID not being backup. 
3) I have read the reviews on this device in various places. Thanks for the suggestion. 

At this point I'm thinking that this might be more trouble than it's worth. I'll probably stick with a more flexible software RAID system or just moving stuff between the drives manually.

---

