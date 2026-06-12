---
title: "Hardware for new server computer for thin clients"
date: 2010-07-11
forum: Hardware
---

### Post by educ8 on 2010-07-11
Thin Clients in classroom, in need of new master computer 

--------------------------------------------------------------------------------

Hello,

I've been running an ubuntu lab in my classroom or at least I've been trying to. My server computer has been running off a P4 2.08 with 4 gb of ram and its just too slow. At best it can handle 3-4 thin clients (on a celeron processor). But I have 12 computers that can be thin clients. 

I'm in the process of building a new computer to replace my current master computer but I don't know what I should do for parts.

I've been looking around and I'm thinking that an Intel i7 processor would be best. 

But if anyone could lend a hand in advising what components I should be looking for, I'd greatly appreciate it. 

Thank you

---

### Post by sixserve on 2010-07-11
Do you need server hardware or are you just using desktop parts?

---

### Post by educ8 on 2010-07-11
> **sixserve said:**
> Do you need server hardware or are you just using desktop parts?

I was planning on using desktop parts.  I have a budget of around $700-800 but it is flexible.

---

### Post by tjandracom on 2010-07-11
it is hardly depend on what kind of application do you need to run on the client. here is my server hardware to run 18 thin client (diskless) Linux Terminal Server Project:

-Motherboard: Gigabyte G31M
-Processor: Intel Core 2 Quad 2.66 Ghz
-Memory: 4GB DDR2
-Hard drive: 2 x 320GB SATA Seagate (mirrored)
-OS: Ubuntu 8.04 LTS with kernel upgraded to version 2.6.24-26.

the server running following application:
-xmail (mail server)
-bind9 DNS server
-LTSP server
-dhcp server (due to LTSP server)
-xrdp server
-apache (web server)

and all the client is running OpenOffice, Opera (internet browser), Evolution (mail client), and my own developed application.
it is enough and i think this setup is still sufficient up to 20 clients.
but if you run graphic intensive application such as Inkscape or Qcad, the number of clients that could connected to this server would be hardly decreased.

---

### Post by educ8 on 2010-07-11
thanks for the reply tjandracom.

does it matter what processor is in the thin clients?  
Basically, all the thin clients would need to do is use OpenOffice, Firefox, and random game applications for now and maybe basic photo/video editing.

---

### Post by tjandracom on 2010-07-12
no, the client's processor doesn't matter. all the processing is done on the server (so it is important to have as many core processor as possible on the server side, rather than speed). the client is only doing screen refresh and capturing/send event from/to mouse/keyboard and port2 (USB, LPT). for the client, any processor that has speed above 800Mhz and 256MB RAM would be enough.

---

### Post by educ8 on 2010-07-14
I would assume that if I build a computer with an Intel i7-860 or i7-920, it would be more than enough?

---

### Post by tjandracom on 2010-07-25
yes, it is more than enough.

---

