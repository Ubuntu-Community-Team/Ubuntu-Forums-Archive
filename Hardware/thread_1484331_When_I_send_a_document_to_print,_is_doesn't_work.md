---
title: "When I send a document to print, is doesn't work"
date: 2010-05-15
forum: Hardware
---

### Post by calande on 2010-05-15
Hello,

My printer is installed, but it's listed twice in the list of printers. When I send a document to print, Ubuntu says the document was received in the print queue, and then the document disappears from the print queue as if it were printed. But nothing is printed at all :(
I tried choosing both LBP2900 and LPB2900-2 (the names of my printer) but nothing happens. Also if I send a document from my remote Windows PC, Windows says the print server is down. Could you help me please?
I have Lucid Lynx and a Canon LPB2900 printer. My computer is both a CUPS server and client.
Thanks,

---

### Post by calande on 2010-05-16
Hey guys, please gimme a hand :)

---

### Post by stuart.reinke on 2010-05-16
I just ran into a similar problem with a HP printer while setting up Linux for a friend.

It behaved the exact same way. Everything on the computer showed that it was printing except nothing happened.

It turned out to be a bad printer.  He got a new one, plugged it in and everything worked perfectly.

I would try a different printer before digging to deep into troubleshooting the operating system.

---

### Post by calande on 2010-05-16
Thanks. The thing is that the printer works like a charm when I boot into W7...

---

### Post by stuart.reinke on 2010-05-16
I'm afraid I'm not much help when it comes to troubleshooting drivers etc.

I saw that you had the same symptoms that I reciently experienced and thought I would share the solution that fixed my problem.

Hopefully someone who knows how to hlep will take notice of your thread and I wish you the best of luck.

---

### Post by calande on 2010-05-16
Thanks, buddy, I hope some one can help me solve the problem...

---

### Post by gillmt on 2010-05-16
Don't know what is happening with your printer but if I was in the same position I would delete the printers, reinstall CUPS (which I had to do with all three of my Lucid installs and then everything was great).

When setting up the printer again,I would look carefully at page set up and all the other printer options - make sure the page size is correct - sometimes it is set to letter instead of A4 and there is no helpful message, it just doesn't work.

Have you had a look at the Linux Printing website to see which drivers work best with your Canon?

Good luck

---

### Post by calande on 2010-05-16
I will try reinstalling CUPS. I used [this tutorial]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900/") to install my printer.

---

### Post by calande on 2010-05-18
I have reinstalled both CUPS and my printer but I am unable to send a document from my Windows laptop to my Ubuntu desktop to print.

---

### Post by crustyBarnacle on 2010-05-18
calande: How did you install the printer in Windows 7?
I find the only reliable method to be the network install, and to point to:

```
http://my-print-server:631/printers/myPrinter

Example: http://localhost:631/printers/Stylus-NX300
```

---

### Post by eltonw on 2010-05-18
> **calande said:**
> I have reinstalled both CUPS and my printer but I am unable to send a document from my Windows laptop to my Ubuntu desktop to print.
You need to set PERMISSIONS for Windows to write to the Ubuntu partition.

seeing that you are new to linux, these links should help you become more familiar with this OS:[http://ubuntuforums.org/showthread.php?t=1483371]("http://ubuntuforums.org/showthread.php?t=1483371")

HTH...

---

