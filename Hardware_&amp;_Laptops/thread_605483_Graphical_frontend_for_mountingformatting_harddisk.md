---
title: "Graphical frontend for mounting/formatting harddisks?"
date: 2007-11-07
forum: Hardware &amp; Laptops
---

### Post by Irwin J. Finster on 2007-11-07
Hi,

I just put a new HD into my Computer, and would like to know if there is a graphical frontend for setting the mountpount and/or formatting harddisks in Ubuntu?

TIA

---

### Post by tact on 2007-11-07
You can use gparted to format and mount drives.  
sudo apt-get install gparted

It wont set a permanent mount tho.  If you want to set up a permanent mount you have to edit /etc/fstab appropriately.  fstab is not a file for the faint-hearted to mess with tho.  make sure you have a back up and read  a lot before you mess with it.

---

### Post by Irwin J. Finster on 2007-11-07
Ah, thanks a lot, this works fine! But now I need an idiot's guide how to mount them permanently!

---

