---
title: "HP Photosmart Printing Problem"
date: 2007-06-30
forum: Hardware &amp; Laptops
---

### Post by tak1150 on 2007-06-30
Hi,

I have a Photosmart 3210 and have it set up as a network printer that serves both a desktop and a laptop (both are Ubuntu 7.04). It has been working flawlessly... until about a week ago.

Whenever I print something from the laptop to the printer, I get a printout that has no line spaces. It's as if the printer ignores all the space between lines and paragraphs.

This happens with PDFs, regular docs, and web pages that I print. It does not happen with the testpage. However, everything is working properly with the Desktop computer.

Desktop and Laptop both have Ubuntu 7.04 and HPLIP and print through CUPS.

Any help would be appreciated! Thanks!

---

### Post by tak1150 on 2007-07-02
OK, I figured this out.

I had installed the newest HPLIP (v. 2.7.6). When I downgraded to 1.7.4, it worked!

---

