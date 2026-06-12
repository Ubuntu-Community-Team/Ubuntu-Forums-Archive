---
title: "[SOLVED] Brother Printer stopped working after upgrading to Gutsy"
date: 2007-10-30
forum: Hardware &amp; Laptops
---

### Post by CyberBob on 2007-10-30
The excitement over upgrading my laptop to (32-bit) Ubuntu 7.10 quickly vanished when I found that the printer driver I had been using with the previous Edgy and Feisty versions simply stopped.  The printer I am concerned about is a thermal label printer, the Brother QL-500, that I did manage to get working about a year ago with the help of some very nice people at the Linux Foundation - see: [http://forums.linux-foundation.org/read.php?24,49](http://forums.linux-foundation.org/read.php?24,49)

I thought, OK maybe something new in the kernel changed things, or something new in CUPS broke it ... so I tried to repeat the procedure referenced above - and again there is just no output.  There is only an error message that appears in the CUPS web interface that says: 

Brother_QL-500_USB_1 "/usr/lib/cups/filter/foomatic-rip failed"


I did post a follow-up back at the Linux Foundation "Printers from Brother" forum where I first got this thing to work - but it appears that few are paying attention to this nearly year-old thread even though there are recent posts.

So, Ubuntu Community - has anyone got a clue why something like this would happen in Gutsy?  Everything else seems to work except this one piece of peripheral hardware.  Unfortunately, I depend on it a lot for printing shipping labels - which I happen to do a lot of from my home office.  To add insult to injury, I have to resort to using a Windows XP machine to make any labels now.  

HELP!  PLEASE!

---

### Post by markharding557 on 2007-11-01
i had a simular problem had to reinstall the drivers worked after that

---

### Post by CyberBob on 2007-11-05
I tried re-installing the drivers but this did not fix the problem.  Symptom is the same error:

Brother_QL-500_USB_1 "/usr/lib/cups/filter/foomatic-rip failed"


UPDATE:  PROBLEM SOLVED!

I was actually starting to prepare for a move to Debian Etch, having installed that distro to a spare HD, when I discovered in another thread about this little command:

```
$ sudo aa-complain cupsd
```

... and after doing that, my little Brother QL-500 thermal label printer started humming again! I have no idea why cupsd "broke" during the distro upgrade from Feisty to Gutsy, but the command above fixed my problem.

---

### Post by jay019 on 2008-02-21
I've been trying to get this printer to work today. I tried the CUPS wrapper drivers from the brother website. I managed to make my own .ppd file as I found it inside one of the scripts it installed, but for some reason CUPS can only manage to print a test page. When i try printing from oo or evince the light flashes constatly until i power it down and up again. The CUPS web admin page says that the document printed, but no it didnt.

Any idea how to get this going. Im using ubuntu 7.04 and have cups 1.2.8 installed.

Jay

---

