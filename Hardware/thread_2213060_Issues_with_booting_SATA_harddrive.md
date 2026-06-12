---
title: "Issues with booting SATA harddrive"
date: 2014-03-24
forum: Hardware
---

### Post by acefromspace on 2014-03-24
I have been having problems getting my SATA hardrive to boot. Even the BIOS doesn't see it. Sometimes it will boot, sometimes not. I never was impressed with the SATA cables... the connections seem weak. My hardrive also has legacy power connector... tried that but no luck, so I supect it's the data connector. Seems to have problems when the room temperature is cold (I live up in the mountains and still very cold in the mornings) Computer is homebuilt desktop with Asus mainboard. Has anyone else had issues with the SATA connectors... is this a common issue? Could it be the harddrive itself? Might not be related, but what does "quick boot" mean (in the BIOS settings) I'm old school and don't understand why so many cables are crappy quality... liked the old ones better. This is not an issue with GRUB... it works fine (if the drive is first recognized by BIOS)

---

### Post by Yellow Pasque on 2014-03-24
1. Make sure your BIOS is updated
2. Try a different SATA port and check the settings in your BIOS. Are you using AHCI or something else?
3. I've never had an issue with SATA cables, even using the (probably) cheap, fluorescent-colored cables included with many a mobo. Get yourself some good SATA cables with SecureConnect if it's really an issue.

> I'm old school and don't understand why so many cables are crappy quality... liked the old ones better
PATA cables?!! You've got to be kidding... There couldn't be any kinks in them and I ended up with a huge stash of them that were just 40 pins and/or longer than the 18" the spec called for, which would have trouble maintaining full speed with more modern disks. Also, the design wasn't the greatest for n00bs, especially in the days before Cable Select.

---

### Post by acefromspace on 2014-03-26
What is AHCI? I noticed this in the BIOS settings... don't know what it means, but think it's set to that right now.

---

### Post by acefromspace on 2014-03-30
"PATA cables?!! You've got to be kidding... There couldn't be any kinks in them and I ended up with a huge stash of them that were just 40 pins and/or longer than the 18" the spec called for, which would have trouble maintaining full speed with more modern disks. Also, the design wasn't the greatest for n00bs, especially in the days before Cable Select."
I meant cables in general... a good example is earbud headphone cables. Yes, I agree ribbon cables were prone to issues. I have some computer speakers that have a broken plug. I could put a new plug on but I know the wires are tiny frail stranded POS... impossible to work with. Anyway, I will buy some new SATA cables as suggested.

---

### Post by acefromspace on 2014-04-29
It seems that the power cable was the problem... not the data cable. The SATA harddrive has optional legacy power connection and this worked. I had tried this before with no luck, but this time I used another power cable. This computer has many power cables and also adapters and some of them are not working. Consider this issue solved (and forgive my rant about cables)

---

