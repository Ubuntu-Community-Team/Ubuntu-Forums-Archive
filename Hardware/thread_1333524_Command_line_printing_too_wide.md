---
title: "Command line printing too wide"
date: 2009-11-21
forum: Hardware
---

### Post by w6kkt on 2009-11-21
Help! I just installed 9.10 amd64.  Everything works great except printing from root command line.  When I try to print "blkid | lpr" the prin is too wide.  My boot resolution is: vga=792.  Usually after new install I print the blkid & grub.cfg files.  Any and all help would be appreciated

---

### Post by sgosnell on 2009-11-21
Have you changed the default font through your printer settings?

On the printer properties page, go to Job Options, and you should see Text Options, and you can set the chars/inch and lines/inch.  Standard is 10 characters/inch and 6 lines/inch, but you can change that.  10/6 is standard Pica, and 12/8 is standard Elite, from the old typewriter specs, IIRC.

---

### Post by w6kkt on 2009-11-21
Sgosnell: Thanks for quick reply.  It worked!  Thanks:KS:popcorn:

---

