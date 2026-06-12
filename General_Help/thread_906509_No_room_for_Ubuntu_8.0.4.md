---
title: "No room for Ubuntu 8.0.4"
date: 2008-08-31
forum: General Help
---

### Post by flyingtortoise on 2008-08-31
The upgrade (from 6.0.6) asks for 381M more, which I'm sure is there somewhere. Running 

df -Th | grep dev

gives:

/dev/hda9     ext3    4.6G  2.8G  1.6G  64% /
udev         tmpfs    189M  120K  189M   1% /dev
devshm       tmpfs    189M     0  189M   0% /dev/shm

How do I make that 1.6G available?

Many thanks.

---

### Post by Sycron on 2008-08-31
> **flyingtortoise said:**
> The upgrade (from 6.0.6) asks for 381M more, which I'm sure is there somewhere. Running 

df -Th | grep dev

gives:

/dev/hda9     ext3    4.6G  2.8G  1.6G  64% /
udev         tmpfs    189M  120K  189M   1% /dev
devshm       tmpfs    189M     0  189M   0% /dev/shm

How do I make that 1.6G available?

Many thanks.

I think it says that you need 1.6GB+381MB .

---

### Post by Elfy on 2008-08-31
See if clearing the apt-cache gives enough room, but even if it does I would think that you would shortly run out of room again

---

### Post by flyingtortoise on 2008-08-31
> **Sycron said:**
> I think it says that you need 1.6GB+381MB .

you're right, now I'm stuck. can I empty the /tmp folder?

---

### Post by flyingtortoise on 2008-08-31
> **forestpixie said:**
> See if clearing the apt-cache gives enough room, but even if it does I would think that you would shortly run out of room again

Does 
sudo apt-get clean 
clear the apt-cache?

---

### Post by Elfy on 2008-08-31
Yes it does , sorry, I should have put it there.

---

