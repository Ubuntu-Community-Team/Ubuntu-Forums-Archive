---
title: "Device file path for SAMBA printer?"
date: 2011-07-18
forum: Hardware
---

### Post by zazuzimbo on 2011-07-18
Hello,

I have installed a shared printer from windows on Ubuntu. I used the "windows printer via SAMBA". So the device URI is now something like:

smb://GROUP/PRINTER-PC/printerName

Now I want to know what device file this printer is on Ubuntu, so I can directly write to it (e.g., "/dev/lp0" is for normal local printers).

How do I find this device path?

Or, in another approach, how do I directly write to that printer?

---

### Post by psusi on 2011-07-18
There isn't one.  You write to it by choosing to print from an application.

---

### Post by zazuzimbo on 2011-07-18
> **psusi said:**
> There isn't one.  You write to it by choosing to print from an application.

But how do I print from the terminal, then?

---

### Post by Morbius1 on 2011-07-18
The same way you do with a locally attached printer. For example, to print your home directory and the remote printer is your default printer:
```
ls -al | lpr
```If it's not then specify the printer:
```
ls -al | lpr -P printer-name
```

---

### Post by zazuzimbo on 2011-07-18
Oh, that is really good! :)

I have tested it and it worked.

Although it had a little glitch to work through:

```

$ ls|lpr
lpr: Bad copies value 0.
$ man lpr
$ ls|lpr -#1

```

I wanted to have the device path to send plain text to the printer. But since this can be done with **lpr**, the thread may be marked as solved.

---

