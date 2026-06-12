---
title: "Printing on the command-line"
date: 2009-07-28
forum: Hardware
---

### Post by AndyCee on 2009-07-28
Hey peoples.

I've got a USB printer which is my default printer in the Preferences and Administration.

If I type

```
lpstat -a
```

I get the printer details. Can someone tell me where the default printer details are kept? I've made the printer available system-wide (in System-Administration). I'm familiar with a Solaris configuration where the default printer is kept in a .printer file in a user's home directory, but this file DNE in mine.

While I'm here, how can I format html, doc or openoffice documents to print on the command line? Can I just use:

```
lp myfile.doc
```

and expect it to print? I've just printed 30 blank pages and torn 2 testing lp and lpr print commands...

---

### Post by dlmarti on 2009-07-28
lpr document.

---

### Post by argos3016 on 2009-07-28
> **AndyCee said:**
> Hey peoples.

I've got a USB printer which is my default printer in the Preferences and Administration.

If I type

```
lpstat -a
```I get the printer details. Can someone tell me where the default printer details are kept? I've made the printer available system-wide (in System-Administration). I'm familiar with a Solaris configuration where the default printer is kept in a .printer file in a user's home directory, but this file DNE in mine.

While I'm here, how can I format html, doc or openoffice documents to print on the command line? Can I just use:

```
lp myfile.doc
```and expect it to print? I've just printed 30 blank pages and torn 2 testing lp and lpr print commands...
There a command on terminal called man. Type man lpr and maybe you find solution.

---

### Post by AndyCee on 2009-07-29
> **dlmarti said:**
> lpr document.

Thanks. I should have figured it would be that simple.

I also found out that print settings are kept in /etc/cups/printers.conf, using "man -k CUPS".

Hoorah!

---

