---
title: "sorry for redundancy.   quick setup Q"
date: 2008-08-10
forum: General Help
---

### Post by meicalnissyen on 2008-08-10
gettin tired of reinstalling windows (been gettin tired since 3.11)

bought ubuntu from best buy, did clean install to old WD 10gig on ide1
starts fine

click firefox,  buncha garbage pops up
 MAIN Q, I need the secret to access the internet (bill solved this one)

tried the media player,
more garbage about needing engraved invitations to look at files on the other drives

every thing is ntfs, and the drive is listed in the interface thing, just wearing this chastity belt

THANKS FOR THE HELP

---

### Post by pytheas22 on 2008-08-10
I'm not sure I understand your question, but I'll try to help if you can explain it more.  Is the problem that you don't have Internet access on Ubuntu and you're wondering how to make it work?  If so, how are you trying to connect--via ethernet or wirelessly--and what is the output of these commands:
```

lshw -C Network
lspci -nn
ifconfig
```

If you're trying to solve a different problem, please let me know what it is and hopefully I'll be able to help.

---

### Post by Mgiacchetti on 2008-08-10
also do a 


cat /etc/issue

Reason im saying this, 8.04 read ntfs fine oob

Would also suggest getting the latest desktop edition from [here]("http://www.ubuntu.com/getubuntu/download")

---

