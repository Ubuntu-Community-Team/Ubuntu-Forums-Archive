---
title: "Firewall blocks network printer"
date: 2009-06-11
forum: Hardware
---

### Post by doublempi on 2009-06-11
I have found some similar posts here and by google, but now answers. I am running the latest version of Ubuntu, and have an HP Officejet J4680 attached to the network by its built-in wireless, at 192.168.0.7.

Briefly, I adminster my firewall with Guarddog. When the firewall is off, I can install and print to the printer without any problems. When the firewall is on, I can't see the printer, and obviously can't print to it. I have ports 9100 to 9290 opened, but still no joy. The only way that I can use the printer is with the firewall turned off, which I don't like to do.

I've tried everything that I can think of, but I'm far from an expert, especially in security areas. Can anyone help?

Thanks,
Mike

---

### Post by ttmon on 2009-06-12
Hi Mike,

I had the same problem with my HP Photosmart c6280 and only got it resolved last night. The solution was to also add/enable UDP 161 (SNMP). From the HP website, it states that HP Jetadmin uses SNMP to configure and query the status of the HP Jetdirect device. See the link below for more detail on the HP Jetdirect Ports.

_[COLOR=Blue]http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&taskId=120&prodSeriesId=27905&prodTypeId=18972&objectID=bpj01014[/COLOR]_

In summary you need the following ports:

TCP 9100 - for printing
TCP 9290 - for scanning
UDP 161   - to configure and query the printer status

Hope this works for you.

Michael

---

### Post by doublempi on 2009-06-12
Thanks, ttmon. It worked!!!

Mike

---

### Post by ttmon on 2009-06-12
Cheers!

---

