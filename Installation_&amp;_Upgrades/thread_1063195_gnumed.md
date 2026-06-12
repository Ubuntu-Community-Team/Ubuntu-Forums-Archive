---
title: "gnumed"
date: 2009-02-07
forum: Installation &amp; Upgrades
---

### Post by rjpilla on 2009-02-07
I installed a backend for gnumed on my local machine. I can connect to it by using any-doc however i have no administrative privilages. I do not know where to get the password for gm-dbo or how to set it in postgresql. I did the bootstrap going to v9 in the database and it never asked me to set the password here. Does anyone know how i can set an administrative password with a local backend gnumed. Thank you.

---

### Post by orthodoc on 2009-02-09
Rjpilla, thats well done!!

I have been trying to install gnumed myself for such a long time. I haven't been able to get to bootstrapping to v9 at all. Mine fails at v2 itself.

When you say you have managed to log in successfully as any-doc you are probably talking about the public gnumed server which is located in germany. The gnumed client on my machine cannot even do that.

If you need help with assigning passwords for gm-dbo in postgresql I cna help you with that. But please do let me know what you did for bootstrapping. Maybe I am missing out on some important detail.

---

### Post by orthodoc on 2009-02-11
I contacted one of the gnumed developers.

There was an issue with the installation scripts. That is sorted out now. The gnumed versions available in the launchpad ppa works well on a ubuntu intrepid 32 bit machine. However this needs installation of postgresql and its configuration which is detailed at the gnumed wiki.

God luck!!

---

### Post by shilbert on 2009-05-07
The packages for 0.3.12 and newer let you create a fully local installation including local postgresql dtabase. I am in the process of uploading packages for verison 0.4.4 which add loads of new features. Details at [http://wiki.gnumed.de](http://wiki.gnumed.de)

---

