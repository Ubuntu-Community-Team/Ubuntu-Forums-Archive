---
title: "How to remove CD as default installation medium"
date: 2006-02-18
forum: Installation &amp; Upgrades
---

### Post by Edk on 2006-02-18
I am new to Linux / Ubuntu and am experimenting with a VM of Ubuntu 5.10.  It was obviously installed using a CD.  Each time I try to add software from the reppositories, I am asked for the CD.  How do I get round this, and download the material that was on the CD from a repository - and which one please?

---

### Post by aysiu on 2006-02-18
Open a terminal (Applications > Accessories > Terminal) and type these commands: ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo nano /etc/apt/sources.list
``` You see that first line that has the word *CDROM* in it? Either delete it or put a # sign in front of that line (the # sign essentially deletes it, as far as Ubuntu's concerned). Finally, save (control-x), confirm (y), and exit (Enter). ```
sudo apt-get update
``` should no longer call on the CD.

---

### Post by Edk on 2006-02-18
Worked a treat!  Thank you very much for a straightforward clear response!  Much appreciated.  All the best to you!

---

