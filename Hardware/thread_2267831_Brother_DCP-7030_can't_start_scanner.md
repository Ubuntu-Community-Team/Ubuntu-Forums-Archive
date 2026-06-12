---
title: "Brother DCP-7030 can't start scanner"
date: 2015-03-04
forum: Hardware
---

### Post by ukasz5 on 2015-03-04
Hello 
I have problem with my new laptop and Brother DCP-7030. I have installed brother's drivers same as on my previous computer. On my old machine with Ubuntu 14.04 everything works great, but now scanner can't start scanning. I have no idea what's wrong...
Help please:-)

---

### Post by leclerc65 on 2015-03-04
Try this
 ```

 sudo gedit /lib/udev/rules.d/40-libsane.rules

    Add the following 2 lines before "LABEL="libsane_rules_end"".

    # Brother scanners
    ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"

```

---

### Post by ukasz5 on 2015-03-04
It doesn't work:-(

---

### Post by gifford on 2015-03-04
Is the scanner recognized by Simple Scan?
Also, is this USB connected or network?

---

### Post by ukasz5 on 2015-03-04
I think that scanner is recognized by Simple Scan, because in preferences it is visible and ticked as scanning source. As for USB connection I don't know, but printing works...

---

### Post by plucky on 2015-03-05
Have you installed sane-utils?

```
sudo apt-get install sane-utils
```

Does it work using sudo?

```
sudo simple-scan
```

Please post output for ```
dpkg -l | grep -i brother
```

---

### Post by ukasz5 on 2015-03-05
With sudo it doesn't work. [COLOR=#000000][FONT=Ubuntu Mono]dpkg -l | grep -i brother gave me:
[/FONT][/COLOR]hary@laptop:~$ dpkg -l | grep -i brother
ii  brdcp7030lpr                                          2.0.2-1                                             i386         Brother DCP-7030 LPR driver
ii  brother-udev-rule-type1                               1.0.0-1                                             all          Brother udev rule type 1
ii  brscan-skey                                           0.2.4-1                                             amd64        Brother Linux scanner S-KEY tool
ii  brscan3                                               0.2.11-5                                            amd64        Brother Scanner Driver
ii  cupswrapperdcp7030                                    2.0.2-1                                             i386         Brother DCP7030 CUPS wrapper driver
ii  printer-driver-ptouch                                 1.3-8                                               amd64        printer driver Brother P-touch label printers


[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR][INDENT]
[/INDENT]

---

### Post by plucky on 2015-03-05
Don't know if this is relevant for you as simple-scan sees your scanner.

On my 64-bit system I had to from a terminal run ```
sudo cp /usr/lib64/* /usr/lib
sudo cp /usr/lib64/sane/* /usr/lib/sane
``` use these two commands and then reboot before my scanner could be seen and used by simple scan.

Good Luck

---

### Post by ukasz5 on 2015-03-05
After that commands terminal said that they are the same files... I have no idea what's wrong:-(

---

### Post by plucky on 2015-03-05
> After that commands terminal said that they are the same files... I have no idea what's wrong

Does that mean the files have already been copied.

Can you post output of ```
ls -l /usr/lib/sane
```

It would be useful if you posted the output of commands to the forum and put them between [noparse]```
Your text
```[/noparse] blocks so the format is preserved.

Did you install sane-utils?

---

### Post by ukasz5 on 2015-03-05
```
hary@laptop:~$ ls -l /usr/lib/sanerazem 148
lrwxrwxrwx 1 root root     41 mar  4 12:49 libsane-brother3.so -> /usr/lib64/sane/libsane-brother3.so.1.0.7
lrwxrwxrwx 1 root root     41 mar  4 12:49 libsane-brother3.so.1 -> /usr/lib64/sane/libsane-brother3.so.1.0.7
lrwxrwxrwx 1 root root     41 mar  4 12:49 libsane-brother3.so.1.0.7 -> /usr/lib64/sane/libsane-brother3.so.1.0.7
lrwxrwxrwx 1 root root     22 mar  4 12:39 libsane-hpaio.so.1 -> libsane-hpaio.so.1.0.0
-rw-r--r-- 1 root root 150288 maj 13  2014 libsane-hpaio.so.1.0.0
```
Yes I installed sane-utils

---

### Post by plucky on 2015-03-06
> dpkg -l | grep -i brother
ii brdcp7030lpr 2.0.2-1 i386 Brother DCP-7030 LPR driver
ii brother-udev-rule-type1 1.0.0-1 all Brother udev rule type 1
ii brscan-skey 0.2.4-1 amd64 Brother Linux scanner S-KEY tool
ii brscan3 0.2.11-5 amd64 Brother Scanner Driver
ii cupswrapperdcp7030 2.0.2-1 i386 Brother DCP7030 CUPS wrapper driver
ii printer-driver-ptouch 1.3-8 amd64 printer driver Brother P-touch label printers

I wonder if it might be worth downloading and installing the i386 scanner drivers instead of the 64-bit version.

Good Luck

---

### Post by ukasz5 on 2015-03-06
I tried but still nothin:-( It is mistery because scannig works on my old computer, but on my new laptop Acer E5-572G-57Y9 not. I tried even on my wife's laptop Lenovo and it does't work either...

---

### Post by ukasz5 on 2015-03-07
Any ideas pls?

---

### Post by ukasz5 on 2015-03-07
I found the solution!:-) If you have same problem just distable USB3 driver in BIOS and scaner will work :-). So simple...:-)

---

### Post by plucky on 2015-03-07
> **ukasz5 said:**
> I found the solution!:-) If you have same problem just distable USB3 driver in BIOS and scaner will work :-). So simple...:-)

Well done,can you please mark the thread as solved in [Thread Tools] at the top of the page.

Do you have USB2 outlets on the laptop?

Have you tried one of those?

---

### Post by ukasz5 on 2015-03-07
Yes I have and I tried all of them. It's quite mysterious, but this solution works for me:-). Thanks for your help.

---

