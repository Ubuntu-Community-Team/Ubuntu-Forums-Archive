---
title: "Printer Software"
date: 2011-06-24
forum: Hardware
---

### Post by Manyette on 2011-06-24
I have recently noticed that the latest HPLIP software no longer sends the hp-timedate or timedate.py on bootup, or at least, so it appears. If Aaron or any of the other printer guru's could comment, it used to be that on my HP J6480 Officejet printer, when the computer booted, it reset the time on the printer.  I'm not sure when this stopped but it has not worked on 10.04 and 10.10 and with the 3 latest versions off HPLIP, which right now is 11.5. This is on a clean install of both 10.10 and HPLIP 11.5.  Can anyone offer some advice/suggestions on what I might check, or try to determine why this is happening?  Thanks for any help.

---

### Post by Manyette on 2011-06-25
<bump>

---

### Post by Manyette on 2011-06-27
<bum> No One?

---

### Post by Manyette on 2011-07-12
Even though no one seems interestedm, this appears to be an aritmetic error. The command is apparently being sent, but is advanced by exactly one minute. Sending it from the terminal sets the clock correctly, but a reboot resets the clock advanced by a minute.

---

