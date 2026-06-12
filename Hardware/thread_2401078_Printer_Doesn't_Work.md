---
title: "Printer Doesn't Work"
date: 2018-09-13
forum: Hardware
---

### Post by skyesharica on 2018-09-13
Hi friends. I upgraded to Ubuntu 18.04 LTS recently, and was delighted that I got a printer at last ... it just automatically happened. I could hardly believe my luck. It is a Hewlett Packard LaserJet M1212nf MFP. All of a sudden it isn't working. I tested the scanner and the paper feeder is working. But when I try to print, I get the thing listed in print queue. But it keeps saying "Held". When I press the button to print again, it flashes for a while, and then malfunctions and goes back to "Held". Also it says that the printing item is Job No. 80. Does that mean there's a malfunction ... I've printed more than 80 things on it ... maybe 80 things have malfunctioned but I seriously doubt it. The manuals show absolutely no light. They are a scam. The instructions are almost devoid of any use. My green light is flashing, which means something is wrong, but there's no instructional message on the LCD display. So I think it might be software.

---

### Post by The Cog on 2018-09-13
I have seen this occasionally and have cleared it by going into the printer administration of cups (http port 631) and doing something there, either delete the stopped job, re-enable the queue or both, I forget the details.

---

### Post by Autodave on 2018-09-13
Try emptying the queue to start with: that normally will solve the problem.  Is this wired (USB), wireless, or ethernet connected?

---

### Post by skyesharica on 2018-09-13
> **The Cog said:**
> I have seen this occasionally and have cleared it by going into the printer administration of cups (http port 631) and doing something there, either delete the stopped job, re-enable the queue or both, I forget the details.

Thanks so much. I'm not a programmer - just ordinary PC level. I've tried finding that port 631, and reading about it here, but it's too complex for me. Can you tell me exactly how I get to this port please? I don't even know what a port is. I tried reading Ubuntu files and Google pages but it's too advanced for me. The print queue might be the problem because it said my last attempt was Print Job 80 ... so maybe 80 attempts are stuck somewhere.  :p

---

### Post by skyesharica on 2018-09-13
> **Autodave said:**
> Try emptying the queue to start with: that normally will solve the problem.  Is this wired (USB), wireless, or ethernet connected?

Thanks. The printer is attached with USB. I've tried to go to the print queue but it's empty. Somehow, however, a print job is number 80! Is the 80 instructions left in cyber space? Can you tell me exactly how to empty that because there's no simple way?

---

### Post by skyesharica on 2018-09-14
Oh sorry, I made a mistake - forgot to put the USB cord in! It's fine.

---

