---
title: "Just upgraded and issue with desktop effects"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by Unikraken on 2009-04-29
Ok, I just upgraded to Jaunty and after my restart it would no longer allow me to change the desktop effects settings, which I would assume is also why Avant Window Navigator is no longer working as well.
This is the error I'm getting.
"Desktop effects could not be enabled."

I'm still a noob and I don't know where to start to troubleshoot this. Can you help me please? :confused:

---

### Post by cyberhell on 2009-04-29
I'm having the same problem... pls somebody help us!!!!

---

### Post by cyberhell on 2009-04-29
I solved it
  File: / usr / bin / compiz change
T = "$ T 8086:2 a02" # Intel GM965
para
# T = "$ T 8086:2 a02" # Intel GM965 

I dont know why intel is on ubuntu blacklist

good luck

---

### Post by Unikraken on 2009-04-29
Hey thanks! that fixed the issue!

---

### Post by happinesskills on 2009-05-01
> **cyberhell said:**
> I solved it
  File: / usr / bin / compiz change
T = "$ T 8086:2 a02" # Intel GM965
para
# T = "$ T 8086:2 a02" # Intel GM965 

I dont know why intel is on ubuntu blacklist

good luck

The file doesn't have that line in it. Do I just edit the file or what?

---

