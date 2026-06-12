---
title: "medibuntu.org DNS problems?"
date: 2008-07-19
forum: General Help
---

### Post by jbygden on 2008-07-19
I was going to run an 'apt-get dist-upgrade' but wanted to start with an 'apt-get update' but that hang on packages.medibuntu.org.

Is it my local DNS-servers that's gone south or is it a more general problem?

$ dig medibuntu.org

; <<>> DiG 9.4.2-P1 <<>> medibuntu.org
;; global options:  printcmd
;; connection timed out; no servers could be reached
$ dig packages.medibuntu.org

; <<>> DiG 9.4.2-P1 <<>> packages.medibuntu.org
;; global options:  printcmd
;; connection timed out; no servers could be reached
$ 


I have no problem resolving any other hosts in my sources.list.

---

### Post by YaroMan86 on 2008-07-19
This isn't really the place to ask about Medibuntu problems. You'll need to ask in the Medibuntu forums.

---

### Post by drs305 on 2008-07-19
dig just worked fine for me.

---

### Post by jtappin on 2008-07-19
> **YaroMan86 said:**
> This isn't really the place to ask about Medibuntu problems. You'll need to ask in the Medibuntu forums.

Easier said than done when <anything>.medibuntu.org gives an unknown host error.

---

### Post by cariboo on 2008-07-19
I just tried installing kdenlive and it wanted some library files from Medibuntu, it was no go. The repositories seem to be down. I just unchecked the Medibuntu repositories in software sources and it was good to go.

Jim

---

### Post by fragos on 2008-07-20
Up and running now. I just installed GoogleEarth from the Medibuntu repositories.

---

