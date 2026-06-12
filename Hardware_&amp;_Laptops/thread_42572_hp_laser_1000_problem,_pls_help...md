---
title: "hp laser 1000 problem, pls help.."
date: 2005-06-18
forum: Hardware &amp; Laptops
---

### Post by luluguegue on 2005-06-18
Hi,
(sorry for my bad english)
i've just install ubuntu network computers ini my small office. the problem is i can not print with my (only one) hp laser 1000. i tried almost one week work houurs with many guide from googling but nothing printed in my ubuntu computer. 
the last guide that i used is :
[http://wiki.clug.org.za/clugwiki/index.php/Adding_an_HP_LaserJet_1000_to_Linux](http://wiki.clug.org.za/clugwiki/index.php/Adding_an_HP_LaserJet_1000_to_Linux)

**but so strange, if i attach this printer to computer with windows2003, i can print perfectly from other computer which ubuntu installed via samba printer. the problem happen if i attach this printer to ubuntu computer  directly and print from these computer**. i'm sure there is no problem with my usb port coz i try with other device such as usb drive and scanner and got no error.

pls helpme, i want totatlly migrate on linux .

here is my copy /var/log/cups/error-log:

 [18/Jun/2005:19:26:27 +0700] LoadPPDs: Wrote "/etc/cups/ppds.dat", 2357 PPDs...
I [18/Jun/2005:19:26:27 +0700] Full reload complete.
I [18/Jun/2005:19:26:54 +0700] Printer 'hplaser' deleted by 'root'.
I [18/Jun/2005:19:26:54 +0700] Saving printers.conf...
I [18/Jun/2005:19:26:58 +0700] Printer 'laserr2' deleted by 'root'.
I [18/Jun/2005:19:26:58 +0700] Saving printers.conf...
I [18/Jun/2005:19:30:34 +0700] Setting hp device-uri to "usb://hp/LaserJet%201000" (was "file:/dev/null".)
I [18/Jun/2005:19:30:34 +0700] Saving printers.conf...
I [18/Jun/2005:19:30:34 +0700] New printer 'hp' added by 'root'.
I [18/Jun/2005:19:30:34 +0700] Saving printers.conf...
I [18/Jun/2005:19:30:34 +0700] Printer 'hp' modified by 'root'.
I [18/Jun/2005:19:30:34 +0700] Saving printers.conf...
I [18/Jun/2005:19:30:34 +0700] Printer 'hp' now accepting jobs ('root').
I [18/Jun/2005:19:30:34 +0700] Saving printers.conf...
I [18/Jun/2005:19:30:34 +0700] Printer 'hp' started by 'root'.
I [18/Jun/2005:19:30:47 +0700] Adding start banner page "none" to job 4.
I [18/Jun/2005:19:30:47 +0700] Adding end banner page "none" to job 4.
I [18/Jun/2005:19:30:47 +0700] Job 4 queued on 'hp' by 'angin'.
I [18/Jun/2005:19:30:47 +0700] Started filter /usr/lib/cups/filter/pstops (PID 7239) for job 4.
I [18/Jun/2005:19:30:47 +0700] Started filter /usr/lib/cups/filter/foomatic-rip (PID 7240) for job 4.
I [18/Jun/2005:19:30:47 +0700] Started backend /usr/lib/cups/backend/usb (PID 7241) for job 4.
I [18/Jun/2005:19:33:05 +0700] Adding start banner page "none" to job 5.
I [18/Jun/2005:19:33:05 +0700] Adding end banner page "none" to job 5.
I [18/Jun/2005:19:33:05 +0700] Job 5 queued on 'hp' by 'root'.
I [18/Jun/2005:19:33:32 +0700] Printer 'hp' deleted by 'root'.
I [18/Jun/2005:19:33:32 +0700] Saving printers.conf...
I [18/Jun/2005:19:36:22 +0700] Setting hplaser device-uri to "usb://hp/LaserJet%201000" (was "file:/dev/null".)
I [18/Jun/2005:19:36:22 +0700] Saving printers.conf...
I [18/Jun/2005:19:36:22 +0700] New printer 'hplaser' added by 'root'.
I [18/Jun/2005:19:36:22 +0700] Saving printers.conf...
I [18/Jun/2005:19:36:22 +0700] Printer 'hplaser' modified by 'root'.
I [18/Jun/2005:19:36:23 +0700] Saving printers.conf...
I [18/Jun/2005:19:36:23 +0700] Printer 'hplaser' now accepting jobs ('root').
I [18/Jun/2005:19:36:23 +0700] Saving printers.conf...
I [18/Jun/2005:19:36:23 +0700] Printer 'hplaser' started by 'root'.
I [18/Jun/2005:19:36:36 +0700] Adding start banner page "none" to job 6.
I [18/Jun/2005:19:36:36 +0700] Adding end banner page "none" to job 6.
I [18/Jun/2005:19:36:36 +0700] Job 6 queued on 'hplaser' by 'root'.
I [18/Jun/2005:19:36:36 +0700] Started filter /usr/lib/cups/filter/pstops (PID 7306) for job 6.
I [18/Jun/2005:19:36:36 +0700] Started filter /usr/lib/cups/filter/foomatic-rip (PID 7307) for job 6.
I [18/Jun/2005:19:36:36 +0700] Started backend /usr/lib/cups/backend/usb (PID 7308) for job 6.

thanks for all.
Lulu.

---

