---
title: "Update and Synaptic Error"
date: 2009-03-24
forum: Installation &amp; Upgrades
---

### Post by be249322 on 2009-03-24
Macbook 1,1 Ubuntu
Whenever i try to update or run synaptic i get this Error...

E: Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_intrepid_main_binary-i386_Packages (1)
E: The package lists or status file could not be parsed or opened.

What now???

Thanks for the help in advance...

(SOLVED)

---

### Post by snova on 2009-03-24
Try running this in a terminal:

```
sudo apt-get update
```

---

### Post by be249322 on 2009-03-24
I tried that already and I get:

Reading package lists... Error!
E: Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_intrepid_main_binary-i386_Packages (1)
E: The package lists or status file could not be parsed or opened.

Which is the same thing?

---

### Post by be249322 on 2009-03-25
Well i solved my problem...

System--> Administration--> Software Sources-->

It had a - in the source code box... so i changed the server from which i was downloading to main server and ran it again... something freed up and it is all back to normal now.

---

