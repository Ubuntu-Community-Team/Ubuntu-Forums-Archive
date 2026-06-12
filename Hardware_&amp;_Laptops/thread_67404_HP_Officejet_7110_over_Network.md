---
title: "HP Officejet 7110 over Network"
date: 2005-09-20
forum: Hardware &amp; Laptops
---

### Post by er4z0r on 2005-09-20
Hi folks,

We are using Ubuntu Breezy as an internal File- and Printserver here.

I have two printers
[list]
[*] a HP Laserjet 1300
[*] a HP Officejet 7110
[/list]

Both of these printers are connected to small Printserver on our Office-LAN (using the BSD-Printing System).
The Ubunut machine shall provide printing services to our Windows-Machines, so first configured the normal Unix print System and just ran into trouble:

The  LJ1300 works fine and prints a testpage when I demnand it in gnome-printer-manager.
The OJ 7110 just feeds in paper after paper and prints some gibberish accross the 
first few lines:
```

!PS-Adobe-3.0
        %%Title: PPR Test Page
                %%Pages: 1
                    %%DocumentNeededResources: font He <--- Here the page ends

```
What am I doing wrong?

---

### Post by er4z0r on 2005-09-21
Ok thanks everybody for your numerous posting.

Seems like the Problem is this:

The printer is set to "raw" printing.
(as I want the data from the windows-boxes to be passed on to the printers directly)
And it also seems that the Officejet doesn't support native Postscript, that is why it prints the postscript data that is passed to it instead of interpreting it and formatting the page correctly.

Could it be this or am I completely on the wrong track?

---

