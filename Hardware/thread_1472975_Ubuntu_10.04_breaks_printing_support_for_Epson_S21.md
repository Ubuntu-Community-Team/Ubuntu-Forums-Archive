---
title: "Ubuntu 10.04 breaks printing support for Epson S21"
date: 2010-05-04
forum: Hardware
---

### Post by nickpick on 2010-05-04
Hi,

I have an Epson Stylus S21. It works like a charm under 9.10 (tested by booting from LiveUSB), but refuses to print under Ubuntu/Lubuntu (also booted from LiveUSB). It recognises the printer and, at least supposedly, installs it. Once I try printing a document, it says that the printing is going fine, but never actually prints anything. It's obviously sending something to the printer, because I can hear the cartridge moving and the little green indicator light keeps blinking. Once the blinking and the movement stop, Ubuntu simply reports that the printing job was completed successfully.

Any ideas where to start or how to fix it? (other than booting 9.10 from LiveUSB and hope that somebody releases a fix soon).

Best regards,

Nick

---

### Post by dave collin on 2010-05-05
Sorry, do not have an answer but same here. I have that printer also. Does exactly what you say. Have gone back to 9.04 for the moment (duel boot with 10.04) as printer really important.
Dave

---

### Post by F W Adams on 2010-05-10
I've got an Epson Stylus D92, similar symptoms - prints nothing but I get status of "Stopped - Printer configuration error"

On pressing help I eventually get a message that there is a file missing but can find no reference to the file on google or synaptic.
/usr/lib/cups/filter/commandtoepsom for printer Stylus_D92 not available

I only print about 1 page a week but it's still very annoying when it doesn't work

---

### Post by leandromartinez98 on 2010-05-10
Yes, apparently printing support for many Epson printers is broken
in Lucid. The bug to be followed is this one, I think:

[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/569190](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/569190)

Please provide more information for that bug if you have.

---

### Post by sundol on 2010-05-12
Same problem for Ricoh Imagio MP-C4000.

I freshly install 10.04. Previouly, 9.10 on same machine printed well but 10.04 doesn't.

'Print Test page' did not print at all but 'Print Self-test page' printed a few line information.

Today (May 13), after updating gnome-printer related packages, 10.04 print human unreadable special characters instead of printing nothing.

---

### Post by whvw on 2010-05-13
Same with my Samsung ML-2250. I got away with a few *temporary* fixes for a session or two, but no more. The printer actually *will* print, but you must wait about 40 minutes for the first page, with a few minutes in between the others. Help!

---

### Post by F W Adams on 2010-05-14
Just in case it might be helpful. I fixed the problem with my printer. This is worth considering if you don't have cups-driver-gutenprint installed. If you do already have it installed then my problem was a different one to yours.

See post #58 onwards here for what fixed it for me.
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/569190](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/569190)

---

