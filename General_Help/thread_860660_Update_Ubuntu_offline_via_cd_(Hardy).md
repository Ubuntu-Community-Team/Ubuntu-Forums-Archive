---
title: "Update Ubuntu offline via cd (Hardy)"
date: 2008-07-15
forum: General Help
---

### Post by vancouverite on 2008-07-15
I have a computer that is connected to the net via a dial-up modem.  Some updates are prohibitively large for this connection and I am looking for another way to keep my OS up to date.

Is it possible to have Synaptic output a list of packages for updating, take that list to another computer that is connected to the net via high speed, download the packages, burn them to CD then take that CD to the dial-up machine and install them?

Doing this when I see download sizes greater than about 8MB would be better than having my phone line tied up for hours on end.

Thanks.

PS, I live in a rural location where HS is not offered.

---

### Post by lswb on 2008-07-15
On the Synaptic/File menu is an option to generate a package download script, seems to be just what you want. It uses wget to download files to the current directory, so you could run it as-is on another linux or unix box (I'm guessing most have wget installed, maybe macs do as well) You could also use a windows machine but you would need to translate the script to something windows can use or find a windows version of wget.

---

### Post by Sef on 2008-07-15
Also if you could do it, you can download the [DVD version]("http://cdimage.ubuntu.com/releases/hardy/release/") of Hardy Heron.

---

### Post by vancouverite on 2008-07-15
> **lswb said:**
> On the Synaptic/File menu is an option to generate a package download script, seems to be just what you want. It uses wget to download files to the current directory, so you could run it as-is on another linux or unix box (I'm guessing most have wget installed, maybe macs do as well) You could also use a windows machine but you would need to translate the script to something windows can use or find a windows version of wget.

Thanks for the replies.  I think the synaptic download script looks like just what I'm after.  Oddly Synaptic crashes when I select that option.  It issues the following in the system log:

Jul 15 20:02:28 [computer] kernel: [79467.788336] synaptic[16540]: segfault at 00000000 eip 00000000 esp bfe2888c error 4

I was able to get around this by first saving the markings, then saving the script.

Cheers,
Van

---

