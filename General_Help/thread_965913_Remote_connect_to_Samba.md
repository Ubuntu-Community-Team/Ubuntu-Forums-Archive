---
title: "Remote connect to Samba?"
date: 2008-10-31
forum: General Help
---

### Post by Airjoe on 2008-10-31
I want to map a network drive to my linux box's samba server from a WinXP box. I'm connecting by mapping a drive to \\MyServerIP\MySharedFolder

It connects, but prompts me for a password. 

Relevant samba cnf:

hosts allow = 192.168.1. 127. MyExternalIpHere
[SharedDocs]
        writeable = yes
        printable = no
        path = /MyPath
        guest only = yes
        public = yes
        guest ok = yes


Is there any way to do this? Thanks!

[edit]
I used to connect from the local network without problem and without a password.

---

### Post by alienprdkt on 2008-10-31
try adding browseable = yes   ???

---

### Post by Airjoe on 2008-10-31
Nope, still prompting for a password. Any other ideas? Thanks!

---

### Post by Airjoe on 2008-11-02
Any ideas?

---

### Post by Airjoe on 2008-11-07
Anyone?

---

### Post by Airjoe on 2008-11-28
No one? Really?

---

