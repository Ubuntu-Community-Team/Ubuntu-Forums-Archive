---
title: "CUPS Canon i560 paused, no resume"
date: 2005-04-28
forum: Hardware &amp; Laptops
---

### Post by jpt2433 on 2005-04-28
I had my Canon i560 working and last night when trying to print from OpenOffice I found out it no longer works.

I would try to print and the job would simply disappear, but when I'd print a test page from the printer config app it would work just fine. I have tried restarting cupsys, and even rebooting and changing the usb port (the printer shows up fine via lsusb).  I've also uninstalled-reinstalled but it doesn't make a difference.

Now when I print it shows up in the queue, but the printer says "printer paused" attempting to unpause in the default print management gui will unpause the printer, then when it tries to process the queue, it pauses itself.


Every time I attempt to unpause the printer /var/log/cups/error_log looks like:
```

...
D [28/Apr/2005:14:44:08 -0400] [Job 1] 0 %%Trailer
D [28/Apr/2005:14:44:08 -0400] [Job 1] Saw Trailer!
D [28/Apr/2005:14:44:08 -0400] [Job 1] Saw EOF!
E [28/Apr/2005:14:44:08 -0400] PID 10651 stopped with status 0!
D [28/Apr/2005:14:44:08 -0400] UpdateJob: job 1, file 0 is complete.
D [28/Apr/2005:14:44:08 -0400] StopJob: id = 1, force = 0
I [28/Apr/2005:14:44:08 -0400] Saving printers.conf...
D [28/Apr/2005:14:44:08 -0400] StopJob: printer state is 5
D [28/Apr/2005:14:44:11 -0400] ReadClient: 4 POST / HTTP/1.1
D [28/Apr/2005:14:44:11 -0400] ProcessIPPRequest: 4 status_code=0
D [28/Apr/2005:14:44:11 -0400] ReadClient: 4 POST / HTTP/1.1
D [28/Apr/2005:14:44:11 -0400] ProcessIPPRequest: 4 status_code=1
D [28/Apr/2005:14:44:12 -0400] ReadClient: 5 POST / HTTP/1.1
``` 


The lines
```

D [28/Apr/2005:14:44:11 -0400] ReadClient: 4 POST / HTTP/1.1
D [28/Apr/2005:14:44:11 -0400] ProcessIPPRequest: 4 status_code=0
D [28/Apr/2005:14:44:11 -0400] ReadClient: 4 POST / HTTP/1.1
D [28/Apr/2005:14:44:11 -0400] ProcessIPPRequest: 4 status_code=1

```

repeat many times.  StopJob: printer state is 5 seems to be the key line there.  


Checking the state via lpc shows that printing is disabled:
```

lpc> status
PIXUS-560i-ver.2.4:
        printer is on device 'usb' speed -1
        queuing is enabled
        printing is disabled
        no entries
        daemon present

```

If anybody knows what Printer State 5 is, or what I should do if I want to try starting from scratch (uninstall/reinstall all printing stuff) I'd really appreciate your help.

---

### Post by Psquared on 2005-05-05
I don't know if this will be of any help, but I had this problem too -- with an HP 5550. I had to uninstall the driver, disconnect the printer and reboot without the printer connected. Then I reinstalled the driver, reconnected the printer via USB and rebooted again. Viola - it worked.

I was getting the exact same paused message -- in my case it had to do with upgrading to Ooo 2.0. Have you upgraded anything printer related or an app that prints at all?

---

### Post by jpt2433 on 2005-05-05
I didn't expect anyone to reply to this now, but thanks for taking the time to do so.  I've actually resolved the problem, recently I ran out of outlets, and haven't had time to rearrange things, so my roomate has been unplugging my printer when he needs to use the new appliance.  The printer does not seem to like being unplugged, and this is where the pause message was coming from.  I've fixed the problem by doing a command line add of the printer via CUPS.

---

### Post by Rodrigo on 2005-05-06
[QUOTE=jpt2433]I've fixed the problem by doing a command line add of the printer via CUPS.[/QUOTE]

I have almost the same problem with my Canon i250, can you please be more "extensive" in your solution, so I can test it with my printer?

---

### Post by jpt2433 on 2005-05-06
I used lpadmin to fix mine, use the format:
lpadmin -p printer-name -L printer-location -D printer-description -E -v usb:/dev/usb/lp0 -m drivername.ppd

If your printer is hooked up to /dev/usb/lp0 this line should work as is:
lpadmin -p canoni250 -L wherever -D canon-i250 -E -v usb:/dev/usb/lp0 -m ???.ppd

I don't know what the name of the ppd for the canon-i250 is, if you've installed it it should be in /usr/share/cups/model/

---

