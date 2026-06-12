---
title: "Need help from a Laptop user - Need ls of /usr/bin"
date: 2007-05-23
forum: Hardware &amp; Laptops
---

### Post by Freaky_Llama on 2007-05-23
Preferably someone with 7.04 Ubuntu. 

I need someone to output their complete /usr/bin directory showing file permissions, (ls -ltr | you may need to make your scrollback larger) 

If you can, paste it here, zip it in a txt or pm me. Please someone help as soon as possible.

I have a Toshiba A135.

Packages I'm MOST interested in are anything Network related (mdns, atheros, avahi) , the HAL files, and anything related to the GUI. But please don't let that stop anyone from uploading the entire list.

Thanks dearly to all! :popcorn:

---

### Post by Metacarpal on 2007-05-23
Here ya go - from one Toshiba Feisty user to another.
Not sure how this'll help ya, but good luck.

Wait, let me try that again...

---

### Post by Metacarpal on 2007-05-23
Here!

---

### Post by stchman on 2007-05-23
> **Freaky_Llama said:**
> Preferably someone with 7.04 Ubuntu. 

I need someone to output their complete /usr/bin directory showing file permissions, (ls -ltr | you may need to make your scrollback larger) 

If you can, paste it here, zip it in a txt or pm me. Please someone help as soon as possible.

I have a Toshiba A135.

Packages I'm MOST interested in are anything Network related (mdns, atheros, avahi) , the HAL files, and anything related to the GUI. But please don't let that stop anyone from uploading the entire list.

Thanks dearly to all! :popcorn:

What exactly is the problem?  A list of the /usr/bin may or may not help.  Let us know exactly what the problem is.

I have Feisty running well on my A135-S2246 laptop.  What model Toshiba laptop do you have?

---

### Post by Freaky_Llama on 2007-05-23
its an s4527 and I inadvertently set 755 to all the files. Now zeroconf isn't working right and dhcp isn't auto renewing. I thought reinstalling them would fix the permissions, but apparently not.

And thanks Metacarpal for the file. I really do appreciate it.

Edit: It looks like it is working again. here's what files had their permissions messed up:

```

COMMAND=/bin/chmod a+sx at
COMMAND=/bin/chmod 2755 bsd-write
COMMAND=/bin/chmod 2755 chage
COMMAND=/bin/chmod 4755 chfn
COMMAND=/bin/chmod 4755 chsh
COMMAND=/bin/chmod 2755 crontab
COMMAND=/bin/chmod 2755 expiry
COMMAND=/bin/chmod 4755 fileshareset
COMMAND=/bin/chmod 4755 fping
COMMAND=/bin/chmod 4755 fping6
COMMAND=/bin/chmod 4755 gpasswd
COMMAND=/bin/chmod 2755 kdesud
COMMAND=/bin/chmod 4755 kpac_dhcp_helper
COMMAND=/bin/chmod 4755 lppasswd
COMMAND=/bin/chmod 4755 mtr
COMMAND=/bin/chmod 4755 newgrp
COMMAND=/bin/chmod 4755 passwd
COMMAND=/bin/chmod 4754 pmount
COMMAND=/bin/chmod 4754 pumount
COMMAND=/bin/chmod 2755 screen
COMMAND=/bin/chmod 2755 slocate
COMMAND=/bin/chmod 2755 ssh-agent
COMMAND=/bin/chmod 4755 start_kdeinit
COMMAND=/bin/chmod 4755 sudoedit
COMMAND=/bin/chmod 4755 traceroute6
COMMAND=/bin/chmod 2755 wall
COMMAND=/bin/chmod a+sx X
COMMAND=/bin/chmod 2755 xterm

```

---

### Post by Metacarpal on 2007-05-24
Ah, okay - yep, permissions will get you every time.
(Quick tip - never change permissions on your home folder itself. It can keep you from logging in.)

---

