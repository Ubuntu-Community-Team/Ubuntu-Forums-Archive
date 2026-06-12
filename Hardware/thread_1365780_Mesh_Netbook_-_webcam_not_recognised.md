---
title: "Mesh Netbook - webcam not recognised"
date: 2009-12-27
forum: Hardware
---

### Post by siabost on 2009-12-27
Hi,

Mesh Edge10 Pro as per this link: [http://www.meshcomputers.com/Default.aspx?PAGE=PRODUCTVIEWPAGE&USG=PRODUCT&ENT=PRODUCT&KEY=684142](http://www.meshcomputers.com/Default.aspx?PAGE=PRODUCTVIEWPAGE&USG=PRODUCT&ENT=PRODUCT&KEY=684142)

The netbook came with Ubuntu Netbook Remix 9.04 pre-installed.
It's a great little machine but I can't get the built-in webcam to be recognised.

Neither "Cheese" nor "aMSN" can find it. Power is supposed to be switched to the webcam via the keys fn+F10 but this seems to have no effect.

Does anyone have any ideas?

Many thanks.

ADDITIONAL: Initially both wired & wireless internet connections worked - after update only wireless works. Not a major problem but nice to know how to fix it.

---

### Post by siabost on 2009-12-28
Anybody...?

---

### Post by Nuts&amp;Bolts on 2009-12-29
> ADDITIONAL: Initially both wired & wireless internet connections worked - after update only wireless works. Not a major problem but nice to know how to fix it.
 I spotted the following on the Mesh Forum (right at the bottom):
 [http://www.meshcomputersownersclub.com/forum/new-guides-faqs/7874-mesh-edge-10-pro-recovery-procedure.html](http://www.meshcomputersownersclub.com/forum/new-guides-faqs/7874-mesh-edge-10-pro-recovery-procedure.html)
 

> **Lan port not working after an update?**
Under Accessories on the left, open Terminal.
Type the following:
**sudo –i** The Press ENTER
enter the password you used when setting up your Netbook at the password prompt.
Type the follow.
**cd /usr/jmmod** Then Press ENTER
**sh fix.sh** Then Press ENTER

The system will re-compile the network driver for the current kernel, and re-enable it, once back at the prompt, just type ‘exit’ to close the terminal.
 Other than that, I have no idea about the web cam.

---

### Post by siabost on 2009-12-29
Thanks Nuts&Bolts re the LAN pointer - unfortunately I don't seem to have the directory /usr/jmmod.

I will try the Mesh forum too.

Thanks :)

---

### Post by siabost on 2009-12-31
WEP security seems to have been the problem re wireless for UNR 9.10.

Switching to WPA-SPK security got me onto the internet and with UNR 9.10 installed wired ethernet is back also.

Still no joy with the webcam but I can live without that for the present.

:P

---

