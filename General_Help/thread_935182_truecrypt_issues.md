---
title: "truecrypt issues"
date: 2008-10-01
forum: General Help
---

### Post by mrchrister on 2008-10-01
hey guys,
i'm new to the linux community and decided to use ubuntu on my dedicated server. great progress so far... but when i tried to use truecrypt i run into some issues. i tried resolving them by reading a lo tfor like the last 6 hours but i didn't get any further

I managed to install truecrypt and I was able to open the GUI
Now ideally I would like to encrypt a file container with an ext3 system. i want to store bigger files then 4GB so FAT is not an option. Now truecrypt doesn't give me an option to format as ext3.
When I try to format the container as FAT I get an error:
mount: wrong fs type, bad option, bad superblock on /dev/loop0

now my questions are... is there a way to use ext3 and to resolve this error?

thanks,
chriss

---

### Post by briandu on 2008-10-01
I have no problem creating 100MB FAT file using truecrypt.

It is the common denominator for Win NT and Linux so the files are portable - exactly as I use them.

---

### Post by Washer on 2008-10-14
/dev/loop0? Are you using the most recent version?

---

