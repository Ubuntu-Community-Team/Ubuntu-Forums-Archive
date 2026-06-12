---
title: "[SOLVED] Printing - some applications do, some don't"
date: 2006-10-17
forum: Hardware &amp; Laptops
---

### Post by bedfojo on 2006-10-17
I'm running Ubuntu dapper 6.06. I have a Canon i250 printer.  I have installed the drivers.

Printing works perfectly from Firefox and Thunderbird. But from Evince, gedit and Adobe's pdf reader, printing does not work.  I get a message: printer-stopped. The job will not restart and has to be manually cancelled.

Any ideas?  Seems an odd one.

---

### Post by bedfojo on 2006-10-18
Anyone? This must be something really simple for you experts out there!

---

### Post by bedfojo on 2006-10-18
Clearly a Gnome Print problem.  Help!

---

### Post by bedfojo on 2006-10-21
Bump.

---

### Post by almal on 2006-11-10
> **bedfojo said:**
> I'm running Ubuntu dapper 6.06. I have a Canon i250 printer.  I have installed the drivers.

Printing works perfectly from Firefox and Thunderbird. But from Evince, gedit and Adobe's pdf reader, printing does not work.  I get a message: printer-stopped. The job will not restart and has to be manually cancelled.

Any ideas?  Seems an odd one.
I'm having the same problem with the same printer - I can print fine with OO, Firefox and Thunderbird. I get  the printer stopped message with evince, gedit, abiword and evolution. Opera prints but all the words are squashed together.

Did anyone find a solution? Any ideas - is there something common about the apps that won't print?

---

### Post by bedfojo on 2007-03-16
Yes, my solution was to buy an HP printer, with decent linux drivers. Prints fine from everything.

Anyone want to buy a Canon i250 printer?  I assume not on these forums, I'll try some poor loser still stuck with W**dows. PS Canon - I won't be buying any of your printers again until linux support improves.

---

### Post by robc02 on 2007-05-10
I sometimes get letters squashed together when printing from Opera. (I haven't tried tried from another browser). My printer is a HP Destkjet 520. I have tried different drivers but the problem seems the same.

---

### Post by Elegorod on 2008-05-12
I had similar problem after updating to Hardy. Printing from OpenOffice and Opera worked normally. But from Gnome programs didn't work. I found a workaround.
My computer has 2 Ethernet adapters, with IP 10.6.x.x and 192.168.0.1 . I hadn't enter CUPS ( [http://localhost:631/](http://localhost:631/) ) because of 403 forbidden error. CUPS saw ethernet IP's and not 127.0.0.1 (why?). And gnome programs hadn't access too and couldn't add printer job.
So I edited /etc/cups/cupsd.conf
Added strings which start with Allow
```

# Restrict access to the server...
<Location />
  Order allow,deny
  Allow localhost
  Allow 10.6.6.121
  Allow 192.168.0.1
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
  Allow localhost
  Allow 10.6.6.121
  Allow 192.168.0.1
</Location>

```

---

### Post by yug23 on 2008-07-24
Thanks for that, I had the same problem and this fixed it! :)

---

