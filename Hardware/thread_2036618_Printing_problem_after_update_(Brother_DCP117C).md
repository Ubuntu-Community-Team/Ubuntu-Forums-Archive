---
title: "Printing problem after update (Brother DCP117C)"
date: 2012-08-02
forum: Hardware
---

### Post by axel112 on 2012-08-02
Hi!

Ubuntu 12.04

After doing an regular update, I can not print anymore. I suppose cups is involved.

/var/log/cups/error.log
```
Returning IPP client-error-document-format-not-supported for Print-Job (ipp://localhost:631/printers/Brother-DCP-117C) from localhost
```

If I start my computer with a liveusbstick ubuntu 12.04, and printerdrivers installed, I can print as usual. I got a cups-update today that I thought would help, but no.

Anybody who can point me in right direction?

---

### Post by axel112 on 2012-08-05
I have now, after much googling and thinking, reinstalled Ubuntu 12.04 with same applications as before except for Ubuntus webapps-preview[http://www.omgubuntu.co.uk/2012/07/how-to-install-ubuntus-new-web-apps-feature]("http://www.omgubuntu.co.uk/2012/07/how-to-install-ubuntus-new-web-apps-feature").

And the printer is happy and printing. Uh! Me to, happy that is.:)

---

### Post by jjinco33 on 2013-03-15
In my experience after an upgrade if I simply reinstall CUPS and then reinstall the issue is fixed.

---

