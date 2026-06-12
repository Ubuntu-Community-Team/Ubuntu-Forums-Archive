---
title: "[SOLVED] installing dreamlinux"
date: 2008-09-16
forum: General Help
---

### Post by N4zgu1 on 2008-09-16
I am interested in installing dreamlinux on my computer but I have an special situation

1 I have a laptop with dual boot: ubuntu and windows vista
2 I have five partitions:ubuntu (/), ubuntu(/home), windows vista, grub and swap

I want to install dreamlinux:
1 without touching the vista partition
2 replacing the "/" partiton of ubuntu with root partition of dreamlinux
3 and keeping the "/home" partition as home (or equivalent partition) for dreamlinux
4 keeping the swap as swap

Can somebody give me instructions please

---

### Post by cariboo on 2008-09-16
If you plan on using the same /home partition, it might be a good idea to get rid of all the hidden files and folders, except for ~/.mozilla and if you use thunderbird ~/.mozilla-thunderbird. The reasoning behinnd the suggestion is that the hidden files and folders contain configuration data for programs that may not work as you expect them to in your new installation.

Jim

---

### Post by N4zgu1 on 2008-09-16
Thanks cariboo907

and I have another question

Do I have to change grub??

---

### Post by Toxicity999 on 2008-09-16
I'm going to say... most likely not. It's the same partition, and if it's standardized, should boot relatively the same. If it offers you a new grub partition, however, take the chance, as it will use it's own, and inqure it being in working condition after install.
 
That aside, was ther anything about ubuntu that you particularly did not care for? We're always open for tips and criticisms. Unless you're just tasting around town, which is perfectly understandable.

---

### Post by N4zgu1 on 2008-09-16
I had a problem with my wireless car, but it look that it doesnt work neither in ubuntu nor dreamlinux

---

