---
title: "How to test mSATA SSD?"
date: 2011-06-28
forum: Hardware
---

### Post by Roasted on 2011-06-28
I have a CR-48. I was having random issues with it detecting the hard drive. Random lockups, freezes, sometimes the InsydeH20 BIOS reporting no disk drive found when booting, etc.

I replaced the SSD with another mSATA SSD from MyDigitalDesigns. So far, I haven't had a single lockup, however it's only been 2 days or so.

In Ubuntu 11.04 within Disk Utility, when I would check out the SMART status, it said healthy. However when I tried to run a test on the drive, whether short or extended, it would cancel within 2-3 seconds after starting it. Since the new SSD is in, I do not exhibit this behavior, and I can complete the tests now.

My question is, I'm not entirely sure if it was the re-seating of the drive by replacing it fixed it, or if the old SSD itself was bad. Is there a way I can hook up an mSATA SSD via a USB bridge or something to run tests on it to see? This is more for learning experience, since I currently seem to have a working system with the newer SSD installed. Thanks!

---

### Post by gordintoronto on 2011-06-28
There are many inexpensive adapters to use an internal drive as an external drive. Example:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16817392032&cm_re=usb_sata_adapter-_-17-392-032-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16817392032&cm_re=usb_sata_adapter-_-17-392-032-_-Product)

---

### Post by Roasted on 2011-06-28
I just wonder if mSATA drives would work on a standard SATA adapter like those you're talking about. They have different pin-outs, which is where I get skeptical on what kind of adapters would work.

[IMG]http://www.storagereview.com/images/mSATA.JPG[/IMG]

When I hold this mSATA drive up to a standard 3.5" SATA hard drive, they are closely similar, but definitely different in the number of pins.

---

### Post by Mars11 on 2011-06-29
I also had this problem, but I just tightened the connector to the motherboard and all my problems were fixed.

---

### Post by Roasted on 2011-06-29
> **Mars11 said:**
> I also had this problem, but I just tightened the connector to the motherboard and all my problems were fixed.

For real? You were exhibiting the random hangups like I was? Mine was happening once every 2 hours or so. Is that what you were seeing?

We're going on 2 days now. No issues. Question for you... when you tightened your motherboard connector, did you specifically see that it was loose? Or did you just tighten it "more" when it already felt secure and that still solved it? Reason I ask is I noticed mine felt tightly secured in place, so I didn't think that was the issue. It wasn't until later I thought, ya know, maybe re-seating it alone would have fixed it...

I'd hate to have paid for this drive when I didn't need it. But it's faster response time and double the onboard space is an attractive reason to keep it. *shrug*

---

### Post by Mars11 on 2011-06-29
It didn't look loose, but I just tightened it anyways. Though it didn't lock-up every two hours but at least twice a week. Icons would disappear and programs wouldn't open up. I would restart it and then it would say that there was not boot device or something similar, I would shake the Cr-48 a little then it would be fine.

---

### Post by Roasted on 2011-06-29
> **Mars11 said:**
> It didn't look loose, but I just tightened it anyways. Though it didn't lock-up every two hours but at least twice a week. Icons would disappear and programs wouldn't open up. I would restart it and then it would say that there was not boot device or something similar, I would shake the Cr-48 a little then it would be fine.

Hmm... that's what I was seeing, however mine was so often I almost didn't use the darn laptop because of it. So far it's going on 3 days with no further issue...

---

### Post by Mars11 on 2011-06-29
You might have just received a faulty SSD.

---

### Post by Roasted on 2011-06-29
> **Mars11 said:**
> You might have just received a faulty SSD.

It's possible. My SMART data was telling me the drive was healthy, but every time I went to run a short or extended test via Disk Utility it would just cancel itself 2-3 seconds in without warning or error. Click test - stopped "Cancelled". Yet I never cancelled it.

With the new SSD, I can do these tasks just fine now. It's nice having a usable system... It drove me CRAZY before.

---

### Post by gordintoronto on 2011-06-29
> **Roasted said:**
> I just wonder if mSATA drives would work on a standard SATA adapter like those you're talking about. They have different pin-outs, which is where I get skeptical on what kind of adapters would work...

I didn't know that. It appears there are adapters, but eventually it starts to get silly.

When I searched Newegg for SSD USB adapter, there were a few hits which appeared to be what you would need, at less than $20.

---

### Post by Roasted on 2011-06-29
> **gordintoronto said:**
> I didn't know that. It appears there are adapters, but eventually it starts to get silly.

When I searched Newegg for SSD USB adapter, there were a few hits which appeared to be what you would need, at less than $20.

Yeah, I saw that too. You see, I thought mSATA was just the type of chip it was, as if there were two different kinds of the actual SATA hookup. I didn't realize mSATA was Micro SATA and actually a different pin count. Ah well.

---

