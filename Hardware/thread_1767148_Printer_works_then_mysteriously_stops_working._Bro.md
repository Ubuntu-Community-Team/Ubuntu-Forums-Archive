---
title: "Printer works then mysteriously stops working. Brother HL-2170W - dnssd failed"
date: 2011-05-25
forum: Hardware
---

### Post by powerpleb on 2011-05-25
For some reason my printer has started playing up with Ubuntu. It always used to work fine (in Ubuntu 10.04) and still works well under Windows.
It is a Brother HL-2170W wireless laser.

It installs fine and I'm initially able to print. But then when I go to print again 15 minutes later it won't work. 
It says "/usr/lib/cups/backend/dnssd failed" in properties window in the printer manager.

If I then delete the printer and go through the setup it works again... For a short while and then it stops working again. Major frustration!!

Can anyone help??

---

### Post by Zimmer on 2011-05-25
Quick link
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

Have you investigated a Brother driver for this printer?

---

### Post by powerpleb on 2011-05-25
> **Maximus_ARNP said:**
> 
**Part-4: Add Printer in UBUNTU System**
[INDENT][B]Ubuntu ----- START ----- SYSTEM ---- ADMINISTRATION ---- PRINTING.
ADD --- PRINTER ---- NETWORK PRINTER ---- [/B]Wait 30 seconds for the system to detect the printer automatically. If printer is not found automatically, type in IP address of the printer and probe for it. 
**Select Your Printer. Selecting [COLOR="Red"][B]JETDIRECT (PRINTER'S IP ADDRESS)**[/COLOR] works for me.[/B]
**FORWARD**
You may change the name of the printer if you wish.
**APPLY.**
[B]Print TEST PAGE.
DONE.[/INDENT]


OK, Googled a bit more :roll: and I found this. Seems to work so far.

---

### Post by powerpleb on 2011-05-25
> **Zimmer said:**
> Quick link
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

Have you investigated a Brother driver for this printer?

Well, it just worked straight away under Lucid so no.
Maybe I should have.:oops:

---

