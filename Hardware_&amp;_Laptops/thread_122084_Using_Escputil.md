---
title: "Using Escputil"
date: 2006-01-26
forum: Hardware &amp; Laptops
---

### Post by SteveF on 2006-01-26
I'm trying to use escputil to monitor my Epson 820 printer.  Whenever I enter the command :
sudo escputil -i -r /dev/usb/lp0

I get the message:
Read from printer timed out

Once I print to the printer using any app (which works fine), then I can use escputil without problems.  It seems like the printer is blocked until I print.

Any ideas on what I can change to get escputil to work without having to print first?

Steve

---

### Post by static chaser on 2006-06-02
Did you ever get an answer or figure it out?  I have a CX5400 that say the same thing.

---

### Post by SteveF on 2006-06-06
Sorry, did not figure it out yet.  On another note, it works when I run Kubuntu (I have both Ubuntu and Kubuntu installed in their own partitions).  So it may be a gnome/wine issue.  I'm going to see what happens when I upgrade to Dapper (testing out upgrade on Kubuntu first).

Steve

---

### Post by static chaser on 2006-06-17
I loaded Dapper onto my machine and escputil works ok now. The command I use is
sudo escputil -i -r /dev/usblp0

---

### Post by SteveF on 2006-06-25
[QUOTE=static chaser]I loaded Dapper onto my machine and escputil works ok now. The command I use is
sudo escputil -i -r /dev/usblp0[/QUOTE]

Worked for me as well.  Fixed in Dapper.

Steve

---

### Post by rgsteele on 2006-07-01
I'm trying to use escputil to perform a head cleaning and nozzle test on my Epson C40UX. The command appears to complete successfully, but the printer doesn't do anything. I'm able to get ink and status information. Anybody have any ideas what's going on?

```
ryan@ryan-desktop:~$ sudo escputil -d -q -r /dev/usblp0
EPSON Stylus C40

ryan@ryan-desktop:~$ sudo escputil -i -q -r /dev/usblp0
         Ink color       Percent remaining
             Black                      88
              Cyan                      72
           Magenta                      71
            Yellow                      70

ryan@ryan-desktop:~$ sudo escputil -s -q -r /dev/usblp0
@BDC ST
ST:04
IQ:58484746
RV:0
AI:CW:0200000000

ryan@ryan-desktop:~$ sudo escputil -c -q -r /dev/usblp0
Cleaning heads...
```

---

### Post by rgsteele on 2006-07-05
I figured it out; apparently the C40UX is one of the "newer" printers that requires the -u switch.

---

### Post by static chaser on 2006-07-07
bump

---

