---
title: "dcopserver issues"
date: 2008-08-24
forum: General Help
---

### Post by sriram.venkataramani on 2008-08-24
This just started today. I'm trying to run pidgin and it just hangs after a few seconds. When I tried to run it from a terminal I get an error that it could not connect to dcop. So I started the dcopserver and pidgin seems to run fine.

Amarok has similar issues. It cannot connect to klauncher. So I started kdeinit and amarok works fine now too. I guess the issue is that kdeinit and dcopserver are not starting automatically when the machine starts. I rebooted my laptop a couple of times but it looks like these services do not start when the machine starts. 

How can I get these to start automatically? Any idea why they stopped?

---

### Post by Kabezon on 2008-08-24
I had a similar issue last night. MPlayer was lauching really slowly, and then I realized dcopserver wasn't running, so I just ran it and MPlayer was now working fine. But then Amarok starting telling me that it couldn't connect to klauncher. I tried ending dcopserver and Amarok worked fine. But I thought to myself... that sucks :P So then I realized that if I ran dcopserver and kdeinit at the same time both apps worked great =] So then I just went to System > Preferences > Sessions and added them both to start automatically with each session. I guess you could do the same.

---

### Post by sriram.venkataramani on 2008-08-24
Worked like a charm. Thanks! I added kdeinit to my Session as you said and piding and amarok just started fine.

---

