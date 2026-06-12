---
title: "Dell XPS Hard Drive - Not installed"
date: 2023-12-19
forum: Hardware
---

### Post by Phil Binner on 2023-12-19
This is not really a Ubuntu problem but if anyone can help I will be grateful.  I have a 2018 Dell XPS13 2 in 1 laptop.  One day on restart it came up with the message "Hard Drive - Not installed"  We thought it was a hard drive failure so we installed another one, but the error is unchanged.  I subsequently found I can read the old hard drive in an external caddy.  This is a good computer and I'm not ready to ditch it, but replacing the motherboard on spec is a expensive option.  I've run the diagnostics (F12 on boot-up), and just come up with the same message.  Is there anything else I can try to hopefully pin down the issue before incurring more expense.

---

### Post by Autodave on 2023-12-19
Probably not.  If there is a cable connecting the HD to the motherboard, you can try replacing that.  But since this is a laptop, I doubt that there is a cable.

---

### Post by Phil Binner on 2023-12-19
I saw my mate change the HD. Pretty sure he plugged it into the motherboard and then used some sort of binding to ensure the connection was tight.

---

### Post by Autodave on 2023-12-20
Time to tell Santa that you need a new 'puter.

---

### Post by ajgreeny on 2023-12-20
Can you boot to a live system on USB and run a few diagnostic commands on that, eg ```
inxi -Fzx
sudo fdisk -l
```
then copy the output of those commands, which might give us some clues, back here using **Code Tags** please.
See my signature below for a How-to on Code Tags.

---

### Post by Yellow Pasque on 2023-12-20
"Binding"? Is that some kind of glue? As far as I can see, the XPS 13 2in1* only has room for an M.2 SSD. If a known good SSD was inserted and screwed down correctly, there's no reason the system should suddenly not detect it. The only thing you can do physically is try and clean the connector. You can also try updating to the latest BIOS, but that's a long shot if you didn't make any updates/changes to the BIOS right before you started having issues.

*It would be nice if you could tell us exactly which XPS 13 2in1 you have and give a link to the manual. I'm assuming 7390.

---

