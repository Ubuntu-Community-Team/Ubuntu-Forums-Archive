---
title: "8800GT problems"
date: 2008-01-18
forum: Hardware &amp; Laptops
---

### Post by Borbus on 2008-01-18
Hi, I use an 8800GT and I have had the Nvidia drivers working with X and compiz-fusion for ages and that is all great.

However, the ubuntu splash screen has never worked for me. It always turns the monitor off, so I decided to try and fix it today. I removed the options spash and quiet from menu.lst (because I want to see the verbose startup) and added vga=795. With this option the monitor does not go off, it just stays blank, but it is at the desired resolution (1280x1024). This happens at startup and also in the other ttys. X continues to work fine.

Any idea how to get this to work? Does anyone know a vga setting that will work with an 8800GT? Thanks.

---

