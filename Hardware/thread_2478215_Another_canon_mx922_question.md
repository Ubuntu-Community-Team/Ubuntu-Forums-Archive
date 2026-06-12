---
title: "Another canon mx922 question"
date: 2022-08-19
forum: Hardware
---

### Post by jpjones55 on 2022-08-19
Using kubuntu 22.04 have installed my canon mx922 all-in-one using the  canon driver 3.90.  Prints and scans fine EXCEPT it will not print in  color.  Tried everything I can think of, but still not printing in  color.

Any suggestions?

Thanks,
JP

UPDATE:  Solved this issue.  After doing alot of research and videos, I combined some things from other sources and fixed my issue:

1. I did a fresh reinstall of Kubuntu 22.04
2. Installed synaptic package manager and installed bjnp from synaptic. this installed the cups-backendd (more printer drivers, I think) and the printer-driver-gutenprint and one other file (can't remember what it is).
3. From the cli, sudo install libgtk2.0-0
4. From the cli sudo install libpango1.0-0
5. Went to Printers - Add New - maunual url ipp://192.168.1.162 or whatever your printers ip.  From the list of canon drivers, chose canon pixma mx922 (not the other mx922).
6. Everything works and prints in color like it should.

Hope this helps someone else.

---

