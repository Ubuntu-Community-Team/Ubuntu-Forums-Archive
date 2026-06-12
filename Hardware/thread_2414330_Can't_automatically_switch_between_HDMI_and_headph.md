---
title: "Can't automatically switch between HDMI and headphones for audio out"
date: 2019-03-08
forum: Hardware
---

### Post by bronolol on 2019-03-08
**Background:** This is a pretty much fresh install of Ubuntu 18.10, on a pretty normal-seeming desktop I recently picked up 2nd-hand.

**Summary:** I only ever want to switch between HDMI and Headphones for my audio output. An S/PDIF output I want nothing to do with keeps getting in the way.

**Hardware:**

[LIST]
[*]The Headphone output and the S/PDIF output are seen by the system as being part of the same "Built-in" card (I think)
[*]The HDMI (video + audio) output is on the video card (Nvidia GTX 650)
[/LIST]

**Desired behaviour:**

[LIST]
[*]Headphones unplugged -> audio output via HDMI
[*]Headphones plugged in -> audio output via Headphones
[/LIST]

[B]Current behaviour:
[/B]
[LIST]
[*]HDMI selected + Headphones become plugged in -> HDMI remains selected
[*]HDMI selected + Headphones become unplugged -> HDMI remains selected
[*]Headphones selected + Headphones become unplugged -> S/PDIF becomes selected
[*]S/PDIF selected + Headphones become plugged in -> Headphones become selected
[/LIST]
[INDENT][SIZE=1]*(as observed through the Settings app, and reflected by where the sound comes from)*[/SIZE][/INDENT]

[HR][/HR]
Output of `pacmd list`: [https://pastebin.com/qTWv4YYj](https://pastebin.com/qTWv4YYj)

---

