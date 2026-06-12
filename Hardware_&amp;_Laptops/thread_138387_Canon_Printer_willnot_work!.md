---
title: "Canon Printer willnot work!"
date: 2006-03-01
forum: Hardware &amp; Laptops
---

### Post by drmcclure on 2006-03-01
My Canon BJC-2100 used to work.  I think...since I put in a firewire adapter now it want work.  I found the command below in one of the forums and this is what I got.  Does anyone have any ideas on how to get the printer working?  Thanks!


dennis@ubuntu:~$ ps -ef|grep cupsd
cupsys    9154     1  1 20:13 ?        00:00:00 /usr/sbin/cupsd -F

here's my error log.

I [01/Mar/2006:07:35:11 -0500] Listening to 7f000001:631
E [01/Mar/2006:07:35:11 -0500] Unknown Location directive <Location on line 857.
I [01/Mar/2006:07:35:11 -0500] Loaded configuration file "/etc/cups/cupsd.conf"
I [01/Mar/2006:07:35:11 -0500] Configured for up to 100 clients.
I [01/Mar/2006:07:35:11 -0500] Allowing up to 100 client connections per host.
I [01/Mar/2006:07:35:11 -0500] Full reload is required.
I [01/Mar/2006:07:35:12 -0500] LoadPPDs: Read "/etc/cups/ppds.dat", 4182 PPDs...
I [01/Mar/2006:07:35:12 -0500] LoadPPDs: No new or changed PPDs...
I [01/Mar/2006:07:35:12 -0500] Full reload complete.
I [01/Mar/2006:20:07:10 -0500] Scheduler shutting down normally.
I [01/Mar/2006:20:07:10 -0500] Listening to 7f000001:631
E [01/Mar/2006:20:07:10 -0500] Unknown Location directive <Location on line 857.
I [01/Mar/2006:20:07:10 -0500] Loaded configuration file "/etc/cups/cupsd.conf"
I [01/Mar/2006:20:07:10 -0500] Configured for up to 100 clients.
I [01/Mar/2006:20:07:10 -0500] Allowing up to 100 client connections per host.
I [01/Mar/2006:20:07:10 -0500] Full reload is required.
I [01/Mar/2006:20:07:11 -0500] LoadPPDs: Read "/etc/cups/ppds.dat", 4182 PPDs...
I [01/Mar/2006:20:07:12 -0500] LoadPPDs: No new or changed PPDs...
I [01/Mar/2006:20:07:12 -0500] Full reload complete.
I [01/Mar/2006:20:08:41 -0500] Adding start banner page "none" to job 54.
I [01/Mar/2006:20:08:41 -0500] Adding end banner page "none" to job 54.
I [01/Mar/2006:20:08:41 -0500] Job 54 queued on 'dennis' by 'dennis'.
I [01/Mar/2006:20:08:41 -0500] Started filter /usr/lib/cups/filter/pstops (PID 8775) for job 54.
I [01/Mar/2006:20:08:41 -0500] Started filter /usr/lib/cups/filter/foomatic-rip (PID 8776) for job 54.

---

### Post by wetland on 2006-03-02
drmcclure:

New to this myself.

If you look at: E [01/Mar/2006:07:35:11 -0500] Unknown Location directive <Location on line 857.
I believe this is telling you there is an Unknown Location directive on line 857 in your /etc/cups/cupsd.conf file? Not sure myself? Maybe someone with more experience can help you out?

In the meantime take a look at line 857 in your cupsd.conf file.

---

