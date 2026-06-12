---
title: "Brothers MFC490CW photo scan quality"
date: 2009-02-03
forum: Hardware
---

### Post by aeronutt on 2009-02-03
Hi folks,
First post, but not a complete Linux rookie. I've been using Ubuntu for about 6 months now, and have used Unix based systems for years (as user, not admin).

I just installed a Brothers MFC490CW printer/scanner/copier using Brothers drivers available online (brscan2 32bit).  All works well EXCEPT, when using XSANE to scan photos, the color is off. eg, very bright areas (sky, clouds) show up yellow.  Nohting I've tried in the XSANE settings seem to help. Scanning the same picture using the Brothers Windows XP software works fine, scanned picture color is fine, so it's not the hardware.

I'm currently using Ubuntu 8.04.

Any ideas for next step?

---

### Post by aeronutt on 2009-02-05
Any thoughts?

---

### Post by aeronutt on 2009-02-07
FYI, I'm giving up and returning the scanner/printer today. Too bad because I really like all other aspects of the MFC. Guess I'll fall to the masses and get an HP. :D

---

### Post by mario_q_82 on 2009-02-19
Im wondering how you even got your mfc-490cw to scan.  I've downloaded and installed all the drivers from the brother website and I can print, but I still cannot get xsane to detect this scanner

---

### Post by mario_q_82 on 2009-02-19
Also, maybe you should've tried brscan3 instead.  Maybe that would've fixed your issue, being that the mfc-490cw falls under that category

---

### Post by myislanduniverse on 2010-04-13
I know this is a bit of a necro-thread, but I just wanted to share that I've gotten my MFC490CW printing and scanning with XSANE.  The issue with XSANE not finding a device is that the drivers have to be moved from the default install location (usr/local/Brother/sane) into the (usr/share/sane) directory.  Then I ran the brsaneconfig3 commands as detailed here ([http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1b.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1b.html)) and restarted XSANE.

Now it's hummin' along.

---

