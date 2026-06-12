---
title: "Samba + Cups + HP Laserjet = maximum one copy of the document"
date: 2006-10-27
forum: Hardware &amp; Laptops
---

### Post by MblKiTA on 2006-10-27
I've got HP Color Laserjet 2550 installed on my computer (Kubuntu 6.06). Everything works fine when I print documents from my computer. 
But the printer is also shared through Samba to clients with WinXP. Printing works fine. But when they request to print more than one copy of the document the printer prints just one copy. It's not a problem when they need 2-3 copies of the document. And when they need 50 copies? :-? 
Can it be fixed somehow?

---

### Post by nashnash on 2006-10-30
same as in my network, im using HP Deskjet-710C and the maximum is only one copy even though i write 3 copies

someone please help

---

### Post by Gimli on 2008-02-19
/bump

This seems like an old thread but it is relevant to me. If someone could help I would appreciate it. I have searched far and wide and I am not finding a solution.

I have an Ubuntu Server 7.10 with Samba and Cups for our small office. HP Laser1300 printer attached via usb. 

When I print an open office document from another linux box and want to print multiple copies it works. But if I print from an XP client, it always only prints one.

If you can, please help

Regards

---

### Post by oldsoundguy on 2008-02-19
Install the driver for the printer in the XP machine also.  I have printers on both XP machines and Gutsy machines and can share either way, but I had to make sure the XP machines had the drivers for the printers on the Linux machines installed!  (since it prints, you at least have the URI correct!)(a mistake I made and it took me DAYS to find the typo! LOL)

---

### Post by Gimli on 2008-02-20
Thanks for the reply but I can confirm that the drivers for the printer is installed on the XP machine as well. I have an idea that the issue is between Samba and Cups. Between those two the 'amount of copies' gets dropped.

---

### Post by oldsoundguy on 2008-02-20
I just used the install printer from the Adminstration options.  Did not try to take the step THROUGH Samba.  Samba is enabled for file sharing only.  (had problems with an earlier build using Samba to install printers and have never done so since.)

---

### Post by Gimli on 2008-02-22
Sounds like a good option, can you point me in the right way to do that using command line, since this  is a headless server.

Regards

---

