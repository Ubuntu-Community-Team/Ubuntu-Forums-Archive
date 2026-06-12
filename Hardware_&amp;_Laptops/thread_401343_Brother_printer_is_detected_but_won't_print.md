---
title: "Brother printer is detected but won't print"
date: 2007-04-04
forum: Hardware &amp; Laptops
---

### Post by hatdragon on 2007-04-04
I have a Brother DCP-8065DN printer. It's a monster, and actually belongs to my whole floor. Brother provides a cups wrapper driver for debian, and the printer is hooked up to the network. With the driver installed, I wasn't able to detect the printer on the network, but I was able to specify it by ip address and queue name, and Ubuntu was happy with that. 

Now, when I print anything (test page or otherwise), the job is put on the queue, sits there for a second or so, and then disappears, exactly as if it had been printed. In fact, I can go to localhost:631 and check completed jobs, and the print jobs are all there. As far as my computer knows, it worked. However, the printer gets the job, blinks its "printing" light, and then does nothing. Everyone else (Windows and Mac users) can print to the printer with no problem whatsoever.

What on earth can I do to fix this problem?!?! Thanks so very much for any replies, even if you're not sure of the solution.

---

### Post by toroblanco on 2007-04-04
I'm not sure exactly how the printer needs to be configure on cups but I think it should look something like this: socket:\\Ip address:9100 this is the default port for jetdirect card give it a try.

Toroblanco

---

### Post by josephus on 2007-04-04
I don't do any printing from linux so I don't know if this related or not:

[http://www.lprng.com/LPRng-HOWTO-Multipart/x10889.htm](http://www.lprng.com/LPRng-HOWTO-Multipart/x10889.htm)
[http://osr600doc.sco.com/en/PR_cups/sam.html#LPD_OPTIONS](http://osr600doc.sco.com/en/PR_cups/sam.html#LPD_OPTIONS)

Basically a print job consists of two parts, the control+data.  Usually control is sent first followed by data, some printers require data followed by control.  Second link tells you how to set that option.

---

### Post by hatdragon on 2007-04-04
Well, the LPD option seemed promising, but using both options resulted in the same behavior.

For more information, the printer is currently configured to accept jobs from lpd://172.16.1.218/binary_p1 I also briefly configured it to accept jobs in RAW form on port 9100; it continued to work for my roommates, but continued to not work (in exactly the same way) for me.

---

