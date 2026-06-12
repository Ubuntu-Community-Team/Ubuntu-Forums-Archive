---
title: "Samba: login to own computer? Browsing network?"
date: 2005-11-28
forum: General Help
---

### Post by gosh on 2005-11-28
Hi,

I installed samba on Ubuntu Breezy to share my linux machines with my XP-boxes.
If I try Places->Network Servers to brows the network a pop-up window appears with the question to login to my own computer; it shows the ip-adress of the machine i am working on at that moment. However it does not accept my password and I cannot browse my network.

When I try Places->Connect to Server, Service Type "Windows share", then type in the IP-address of one of the XP-boxes or my Linux computer in the Server-field, I can reach the other computers.

What is actually happening here?

My smb.conf looks like this:

[global]
	workgroup = WORKGROUP
	security = user
	printable = no
	read only = no

[homes]
	browseable = No
	writable = yes

That's all.

---

### Post by gumbald on 2005-12-01
Same problems for me, no matter what I do to smb.conf as told by various places. Can anybody point me to a comprehensive Samba-WIndows guide? :)

---

### Post by soulestream on 2005-12-01
have you created the samba users?


soule

---

### Post by cgjones on 2005-12-01
Try setting browseable=yes, or set up a section for each specific user. That's the way I've always used samba. Check out the existing smb.conf file for examples, if you still have it.

---

### Post by andril on 2005-12-01
Same here - I can't get this to work either. What happened? It worked so damn well with 5.04 now in 5.10 massive issues. Please someone help us :confused:

---

### Post by gosh on 2005-12-02
[QUOTE=cgjones]Try setting browseable=yes, or set up a section for each specific user. That's the way I've always used samba. Check out the existing smb.conf file for examples, if you still have it.[/QUOTE]

It works now .... more or less.

I made the following chances:

securtity = share

browseabel = yes.

Now I can see all my computers and access them from my linux notebook.
On my dualboot desktop I can access everything through XP but not through Ubuntu..:mad: 

Any clues?

---

