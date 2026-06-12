---
title: "Coudn't make printer work by lbp660 driver in utsy"
date: 2007-11-14
forum: Hardware &amp; Laptops
---

### Post by jis on 2007-11-14
I meant in Gutsy. And the printer is Canon LBP-660.

I tried to install the latest driver, that is version 0.3.1, from here:
[http://www.boichat.ch/nicolas/lbp660/](http://www.boichat.ch/nicolas/lbp660/)

Actually I used
sudo checkinstall
instead of
make install
but I am not sure, if it make sense to remove the driver by
sudo dpkg -r lbp660
later, if it is not needed anymore or if it does not work.

I edited restartcups.sh to just do
/etc/init.d/cupsys restart
and wait 5 seconds.

Finally after running
sudo make cups-install-660-a4
I thought I could start printing.

I can see the printer in printer config dialog and I tried to print from Abiword, but it does not print. I can see the job in printer jobs dialog, but it soon shows status stopped. Nothing gets printed. I am not familiar with the printer, but can you say what is wrong?

---

### Post by mirkuma on 2007-11-15
I have installed printer as stated in this post: [http://ubuntuforums.org/showthread.php?t=610734]("http://ubuntuforums.org/showthread.php?t=610734")

But I have exactly the same problems as you...meaning: the printer is installed, but I can't print.
I get the LBP-660 "/usr/lib/cups/filter/foomatic-rip failed" message in the [http://localhost:631](http://localhost:631) page.

This is error log from var/log/cups/error_log file:
Purge-Jobs: Unauthorized
Pause-Printer: Unauthorized
Resume-Printer: Unauthorized
PID 5449 (/usr/lib/cups/filter/foomatic-rip) stopped with status 3!
[Job 13] Job stopped due to filter errors.

Runing Ubuntu 7.10.

---

