---
title: "No sound on my laptop"
date: 2007-03-14
forum: Hardware &amp; Laptops
---

### Post by royrules22 on 2007-03-14
Hi, I hope this is the right place for this question. In any case I have a new install of Edgy on my Asus W3J+ laptop (Intel T2500 | Mobility Radeon X1600 | integrated soundcard (Intel HDA?)). So far everything is great, except for the sound. No sound comes out at all. Now I tried following all troubleshooting advice (alsamixer says nothing is muted, and all bars are at 100%, etc) but still to no avail. Sometimes I can hear a very faint static noise, but usually nothing comes out. I'm stumped. Any suggestions?

Thanks

---

### Post by spier on 2007-03-14
Check what is selected in the sound applet preferences. Maybe your sound is redrirect to the wrong device!

hth

---

### Post by royrules22 on 2007-03-14
I'm sorry but I'm still a n00b when it comes to linux. I know how to do stuff, but when it comes to command line commands I'm still clueless (besides your ls, cds, and diffs I don't know much).
How do I check the sound applet preferences?

---

### Post by spier on 2007-03-14
Sorry my foreign "consise style'  - less writing, less errors ;)

You should have a speaker icon in a panel: right-click it, choose Preferences. Among other things like volume, should have a list of devices to the applet take control of, like front/rear jack, headphones  (guessing as I'm not at my laptop right now)

---

### Post by glotz on 2007-03-14
Seen this? [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

If you're not sure whether you've actually got intel hda, type lshw into command line and see what it says under *multimedia.

---

