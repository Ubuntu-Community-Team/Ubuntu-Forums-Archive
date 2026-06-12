---
title: "Samsung ML-1520 printer"
date: 2005-07-14
forum: Hardware &amp; Laptops
---

### Post by namedontwant on 2005-07-14
If you have this printer, neurosion helped me with his explanation for the ML-1710. Just do the same thing, and it will work!!!!!

here is the explanation (from him, not from me!):
[http://ubuntuforums.org/showthread.php?t=31796&page=1&pp=10](http://ubuntuforums.org/showthread.php?t=31796&page=1&pp=10)

OK, here's the full how-to (off the top of my head) for getting the ML-1740 up and running on Ubuntu i386:

1) Download the latest drivers from here.

2) Extract the archive somewhere you can get at it.

3) Use the package manager to fetch libgtk 1.2

4) Open a terminal window.

5) Type: sudo adduser cupsys shadow

6) Type: sudo /etc/init.d/cupsys restart

7) Type: sudo passwd root [sets up a temporary root password]

8. Go to wherever you extracted the drivers and type: ./setup.sh

9) Follow the prompts. If all goes well you should end up in Samsung's setup utility. If you somehow don't get there, typing linux-config in a terminal will get you there.

10) "Add printer"

11) Enter the root password you created in step 7

12) Follow the prompts; I can't help you here, these settings depend on your actual setup

13) When you're all done, type: sudo passwd -l root [disables root password]

Your printer should be configured and available in System -> Administration -> Printing.

Hope it helps.

---

### Post by namedontwant on 2005-07-24
forgot to mention: to prevent problems, use the root terminal!!!!

---

### Post by oneTime on 2006-09-10
Try this one:

[http://www.ubuntuforums.org/showthread.php?t=254479&highlight=samsung+ML-1520](http://www.ubuntuforums.org/showthread.php?t=254479&highlight=samsung+ML-1520)

And good luck!
-OneTime

---

