---
title: "Brother DCP 7070 DW does not scan"
date: 2015-03-06
forum: Hardware
---

### Post by thomas46 on 2015-03-06
Printing works fine on wireless, but I can not get the scanner to work either with USB or wireless. I have Ubuntu 14.10 installed. Simple scan does not detect the scanner and Xsane detects the scanner, but nothing happens. I am not a computer guy so I am afraid I will make some damage by doing to much adjustments and installations. I think I am asking for a complete walk through here.

---

### Post by thomas46 on 2015-03-06
Here is the output:

```
ii  brother-cups-wrapper-ac                              1.0.3-1-0ubuntu3                         amd64        Cups Wrapper drivers for ac brother printersii  brother-cups-wrapper-bh7                             1.0.0-10-0ubuntu6                        amd64        Cups Wrapper drivers for bh7 brother printers
ii  brother-cups-wrapper-common                          1.0.0-10-0ubuntu6                        amd64        Common files for Brother cups wrapper packages
ii  brother-cups-wrapper-extra                           1.2.1-0ubuntu4                           amd64        Cups Wrapper drivers for extra brother printers
ii  brother-cups-wrapper-laser                           2.0.1-2-0ubuntu6                         amd64        Cups Wrapper drivers for laser brother printers
ii  brother-cups-wrapper-laser1                          1.0.2-1-0ubuntu8                         amd64        Cups Wrapper drivers for laser1 brother printers
ii  brother-cups-wrapper-mfc9420cn                       1.0.0-1-0ubuntu6                         amd64        Cups Wrapper drivers for mfc9420cn brother printers
ii  brother-lpr-drivers-ac                               1.0.3-1-0ubuntu4                         amd64        LPR drivers for ac brother printers
ii  brother-lpr-drivers-bh7                              1.0.1-1-0ubuntu6                         amd64        LPR drivers for bh7 brother printers
ii  brother-lpr-drivers-common                           1.0.0-4-0ubuntu3                         amd64        Common files for brother-lpr-drivers packages
ii  brother-lpr-drivers-extra                            1.2.0-2-0ubuntu5                         amd64        LPR drivers for extra brother printers
ii  brother-lpr-drivers-laser                            2.0.1-3-0ubuntu5                         amd64        LPR drivers for laser brother printers
ii  brother-lpr-drivers-laser1                           1.0.0-3-0ubuntu6                         amd64        LPR drivers for laser1 brother printers
ii  brother-lpr-drivers-mfc9420cn                        1.0.0-3-0ubuntu4                         amd64        LPR driver for mfc9420cn brother printer
ii  brscan-skey                                          0.2.4-1                                  amd64        Brother Linux scanner S-KEY tool
ii  brscan4                                              0.4.3                                    amd64        Brother Scanner Driver
ii  cupswrapperdcp7070dw                                 2.0.4-2                                  i386         Brother DCP7070DW CUPS wrapper driver
ii  dcp7070dwlpr                                         2.1.0-1                                  i386         Brother DCP-7070DW LPR driver
ii  printer-driver-brlaser                               3-3                                      amd64        printer driver for (some) Brother laser printers
ii  printer-driver-ptouch                                1.3-8                                    amd64        printer driver Brother P-touch label printers
```

---

### Post by pdc on 2015-03-07
Brother say you need to edit a file to get the scanner to work; as end-user (it will work if one uses sudo powers.............)

so have a read at post #2 here [http://ubuntuforums.org/showthread.php?t=2267831&highlight=brother](http://ubuntuforums.org/showthread.php?t=2267831&highlight=brother) or get the file from here [http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04](http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04) 

you can see it is called [COLOR="#008000"]brother-udev-rule-type1-1.0.0-1.all.deb[/COLOR]

---

### Post by thomas46 on 2015-03-08
I etited the text and saved it, but no change. As earlier scanner detected in Simple scan and Xsane.

---

### Post by gifford on 2015-03-08
Not sure what your issue is but this thread solved a problem similar to yours: [http://ubuntuforums.org/showthread.php?t=2267831](http://ubuntuforums.org/showthread.php?t=2267831)

---

### Post by thomas46 on 2015-03-09
My problem, as written above, is that Xsane and simple scan detects the scanner, but nothing happens when I try to scan. I believe I got everything needed installed. Here is the output for [COLOR=#000000][FONT=Ubuntu Mono]ls -l /usr/lib/sane[/FONT][/COLOR]

```
thomas@thomas-HP-Pavilion-g6-Notebook-PC:~$ ls -l /usr/lib/sanetotalt 148
lrwxrwxrwx 1 root root     41 aug.  29  2014 libsane-brother4.so -> /usr/lib64/sane/libsane-brother4.so.1.0.7
lrwxrwxrwx 1 root root     41 aug.  29  2014 libsane-brother4.so.1 -> /usr/lib64/sane/libsane-brother4.so.1.0.7
lrwxrwxrwx 1 root root     41 aug.  29  2014 libsane-brother4.so.1.0.7 -> /usr/lib64/sane/libsane-brother4.so.1.0.7
lrwxrwxrwx 1 root root     22 juli  29  2014 libsane-hpaio.so.1 -> libsane-hpaio.so.1.0.0
-rw-r--r-- 1 root root 150296 juli  29  2014 libsane-hpaio.so.1.0.0



```

Maybe I should try this: [COLOR=#000000][INDENT]I found the solution!:smile: If you have same problem just distable USB3 driver in BIOS and scaner will work :smile:. So simple...:smile:

What does that means?

[/INDENT]


[/COLOR]
[COLOR=#000000][B][RIGHT][/RIGHT]
[/B][/COLOR]

---

### Post by thomas46 on 2015-03-09
I am trying to run the scanner/printer on wireless. Printing works fine.

---

### Post by plucky on 2015-03-09
> **thomas46 said:**
> I am trying to run the scanner/printer on wireless. Printing works fine.

You need to tell the scanner driver the network address of the scanner and give it a name 

See [Scanner driver Install for Network](http://support.brother.com/g/s/id/linux/en/instruction_scn1b.html?c=us_ot&lang=en&redirect=on)

> 

Step 5. Setting for your network scanner
    *****Use brsaneconfig (for brscan models), brsaneconfig2 (for brscan2 models) or brsaneconfig3 (for brscan3 models) accordingly.**
    5-1. Add network scanner entry

        Command  :  brsaneconfig4  -a  name=(name  your  device)  model=(model  name)  ip=xx.xx.xx.xx
        Example 

    5-2. Confirm network scanner entry

        Command  :  brsaneconfig4  -q  |  grep  (name  of  your  device)
        Example 


Good Luck

---

### Post by thomas46 on 2015-03-09
I think I have done that. How do I check that, get the output and control I have the right IP?

---

### Post by plucky on 2015-03-09
From a terminal window ```
brsaneconfig4 -q | grep (name of your device)
```

---

### Post by thomas46 on 2015-03-09
Thanks, but how do I find the right IP? Is the same as I use for printing wireless?

---

### Post by plucky on 2015-03-09
> **thomas46 said:**
> Thanks, but how do I find the right IP? Is the same as I use for printing wireless?

Yes or login to your wireless router and it should be there.If you reboot your router,the IP address could change.

Good Luck

---

### Post by thomas46 on 2015-03-09
Scanner detected, but could not connect to scanner. Anybody know what is going on?

---

### Post by gifford on 2015-03-09
How many scanners do you have on your network?
From reading some of your posts it seems you have multiple scanner..Brother and HP. 
Is this correct?

---

### Post by thomas46 on 2015-03-09
No, it is just one, but I have tried to install several times. I have several entries in the scanner menu? Do you think they are in conflict?

---

### Post by gifford on 2015-03-10
It also looks like you have several printer drivers as well. Do you have a Brother MFC9420CN printer?
If it were me, I would start over with the installation and delete all the drivers. My experience with
installing Brother printers and scanning devices has always been with using the terminal and following
the instructions on the Brother site. I have never used the driver install tool nor the scan key tool.
We have always used the printers as shared on our network and have never had problems.

---

### Post by thomas46 on 2015-03-10
I think what you are saying makes sense. How do I delete all the drivers and make the computer ready for a new installation?

---

### Post by thomas46 on 2015-03-11
How do I remove everything and start from scratch? I need to use the scanner for work and want to avoid installing windows.

---

### Post by gifford on 2015-03-11
Probably the best way for you would be to use synaptic package manager. If you do not have it installed, it is available in the software center.
Look for your brother and it should pull up all that you have installed as the check box will be marked. You can remove them by marking for complete removal.

But first, did you follow the advice and code in post #10? Please post what your results are when running the command. Is the ip the same as for your printer?
If not, please post and will advise on how to change it. I just had to do this today as my modem/router was changed and so was the ip of my scanner.

---

### Post by thomas46 on 2015-03-12
I have now removed everything related to Brother in Synaptics. In the new installation should I use Synaptics or go through the terminal? Any pointers to a idiot proof walkthrough?

---

### Post by thomas46 on 2015-03-13
Now I istalled everything with the installer tool and gave the scanner the same IP as the printer. As before the printer works fine, but I can't scan. Just like before. Here are my outputs:
```
$ dpkg -l | grep Brotherii  brscan-skey                                          0.2.4-1                                  amd64        Brother Linux scanner S-KEY tool
ii  brscan4                                              0.4.2-1                                  amd64        Brother Scanner Driver
ii  cupswrapperdcp7070dw                                 2.0.4-2                                  i386         Brother DCP7070DW CUPS wrapper driver
ii  dcp7070dwlpr                                         2.1.0-1                                  i386         Brother DCP-7070DW LPR driver



```

---

### Post by thomas46 on 2015-03-13
I am starting to think it is something wrong with the wireless connection between the laptop and the scanner. But the scanner is still detected in Simple Scan and XSane.

---

### Post by gifford on 2015-03-13
I am not familiar with the S-KEY tool and have never used it. I wonder if this is your problem.
Since Simple Scan and XSane recognize the scanner, there must be something else causing the problem. 
Your printer/scanner is not sold in the US so I assume you are in Europe..the UK?
Try to be patient as a solution will be found.

Do you have GIMP installed? Apparently, it is a requirement for the S-KEY tool.

---

### Post by thomas46 on 2015-03-13
I am located in Norway so it is a kind of local edition, but I was directed to the right drivers in english. Yes, I have Gimp, but I can remove it since the scanner is way more important. Should I try to remove the S-KEY tool?

---

### Post by gifford on 2015-03-13
Keep Gimp. Are you running a firewall? If so, with S-KEY it requires certain ports be open.
Let's see if we can't get it working with S-KEY tool.
Yes, the printer model you have is sold in Europe. 
Again, be patient. The solution will be found.

---

### Post by thomas46 on 2015-03-13
No firewall.

---

### Post by gifford on 2015-03-13
At this point, I would remove the S-KEY tool, reboot and try to scan with Xsane.

---

### Post by thomas46 on 2015-03-14
Thanks, Gifford! I removed the S-Key tool and that worked both with Simple Scan and XSane. But now the printer does not work. No entries shows up and when I open the printer menu under system the "add printer" button is faint and I cant activate it. I also get the message that it is something wrong with cups. So I guess it is a configuration issue

---

### Post by thomas46 on 2015-03-14
Here is my output. From my understanding everything should be there

```
thomas@thomas-HP-Pavilion-g6-Notebook-PC:~$ dpkg  -l  |  grep  Brotherii  brscan4                                              0.4.2-1                                  amd64        Brother Scanner Driver
ii  cupswrapperdcp7070dw                                 2.0.4-2                                  i386         Brother DCP7070DW CUPS wrapper driver
ii  dcp7070dwlpr                                         2.1.0-1                                  i386         Brother DCP-7070DW LPR driver



```

---

### Post by thomas46 on 2015-03-14
Solved! Thanks for the help, Gifford.
I reinstalled the cupswrapper and the printer worked fine! So now I can print and scan both in Simple scan and XSane. If I was doing this again I would install only cupswrapper driver, lpr driver and brscan. It looks like the install tool and S-KEY is asking for trouble.

---

### Post by gifford on 2015-03-14
Glad it worked! As I stated, my experience has always been with what you listed. No install tool or S-KEY.
The good thing is that once you have done this you will know how to do it again and help others. That is
the forum way.

---

### Post by thomas46 on 2015-03-15
It did not work for long! The printer disappeared and the scanner stopped working. When I tried to add the printer in system the add icon is faint and it is not possible to activate the icon. I am able to ping the printer.

---

### Post by thomas46 on 2015-03-15
So I reinstalled everything. When I try to print a test page it tells me that the printer is not responding.

---

### Post by thomas46 on 2015-03-16
The menu for the printer said that the printer was not responding and I should check port 631 since it was blocked in my router. So I forwarded that port with the correct IP for the printer. And I still get the message that I should check the port.

---

### Post by thomas46 on 2015-03-16
So I downloaded everything again. And now I am not able to install anything. The driver tool does not recognize the printer model so I can not use that. And I am not able to install the different drivers packages that I downloaded through the terminal. I have used Ubuntu for 6-7 years and have never had problems like this. I am really close to dropping the whole system because I can not have it like this. Could somebody help me with this?

---

### Post by thomas46 on 2015-03-16
This is what happens when I try to install with the installer tool:

```
thomas@thomas-HP-Pavilion-g6-Notebook-PC:~/Nedlastinger$  gunzip linux-brprinter-installer-*.*.*-*.gzgzip: linux-brprinter-installer-2.0.0-1 already exists; do you wish to overwrite (y or n)? y
thomas@thomas-HP-Pavilion-g6-Notebook-PC:~/Nedlastinger$ sudo bash linux-brprinter-installer-*.*.*-* Brother machine name
Driver-packages cannot be found.
 Confirm the model name.


thomas@thomas-HP-Pavilion-g6-Notebook-PC:~/Nedlastinger$ sudo bash linux-brprinter-installer-*.*.*-* Brother machine name
Driver-packages cannot be found.
 Confirm the model name.


thomas@thomas-HP-Pavilion-g6-Notebook-PC:~/Nedlastinger$ sudo bash linux-brprinter-installer-*.*.*-* Brother dcp7070dw
Driver-packages cannot be found.
 Confirm the model name.



```

---

