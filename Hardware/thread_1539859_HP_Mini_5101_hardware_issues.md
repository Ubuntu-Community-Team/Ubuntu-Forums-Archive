---
title: "HP Mini 5101 hardware issues"
date: 2010-07-27
forum: Hardware
---

### Post by Rahsennor on 2010-07-27
Bluetooth. I'm sure the 5101's supposed to have it, but my machine stubbornly dissagrees. bluetooth-properties (Applications -> Settings -> Bluetooth) just says "No bluetooth adapters present". My google-fu only turned up people saying it worked out-of-the-box.

I don't even know where to start. This being my first bluetooth-capapable computer, it could well be a layer 5 error. :D

---

### Post by P4man on 2010-07-27
You may just have to turn it on. Some laptops have a hardware button for it; or a key combination like Fn+somefunction key. Ive also seen machines where the BT radio is only on if wifi is on.

---

### Post by gordintoronto on 2010-07-27
According to the 5101 manual, some models of 5101 have Bluetooth, others do not. It also has one reference which makes me think enabling Bluetooth is done in the BIOS.

---

### Post by Rahsennor on 2010-07-28
> **gordintoronto said:**
> According to the 5101 manual, some models of 5101 have Bluetooth, others do not. It also has one reference which makes me think enabling Bluetooth is done in the BIOS.

:( [I was afraid of that.]("http://apcmag.com/notebookhunter/hp-mini-5101-notebook-pc-vm531pa.htm?VisibleAttributes=true") Thanks for the replies, even if all you did was point out my own stupidity. Bluetooth adapters are a dime a dozen anyway. :)

I do have one final question, if I can stretch the topic a little. I can't get vertical sync going. It's not exactly a gaming machine, but the tearing gives me a headache. Any hints?

---

### Post by P4man on 2010-07-28
You may have a free mini PCi slot in that machine. Just put a bluetooth card in there; they cost next to nothing. If there is no free slot; you can probably replace the wifi module with a combined wifi+bluetooth module.

As for vsync, no idea. But that intel GPU isnt the best supported :S.

---

### Post by Rahsennor on 2010-07-28
Didn't think of that... maybe since it involves a screwdriver. :shock: I've probably voided the warranty already by putting Ubuntu on it, so why not? :p It should have a free mini PCI-e slot where the WWAN adaptor would have gone.

The GMA 950 drivers aren't that good. But they work; sure beats the Radeon in my desktop. :roll: So far I've only poked around with xorg.conf. Where else should I look?

[EDIT: GMA950 drivers now support vsync in OpenGL. Compiz or similar is required to add vsync to 2D graphics. Took me ages to figure out, so I'll put it here in case anyone else happens to google this. Also works for aformentioned Radeon.]

---

