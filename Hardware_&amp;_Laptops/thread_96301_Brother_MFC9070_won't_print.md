---
title: "Brother MFC9070 won't print"
date: 2005-11-28
forum: Hardware &amp; Laptops
---

### Post by jocke on 2005-11-28
I'm not so used to printing technologies, but I have read a lot now about CUPS etc., and searched the forums, and then tested of course. This is what I have done:

1. Downloaded LPD driver and CUPS wrapper from [Brother]("http://solutions.brother.com/linux/en_us/index.html")

2. According to [this]("http://www.ubuntuforums.org/showthread.php?t=71104&highlight=mfc"), I installed csh. I don't think this is necessary, but it can't hurt, or can it?
```
sudo apt-get install csh
```

3. According to the [printers supported]("https://wiki.ubuntu.com/HardwareSupportComponentsPrinters"), MFC9070 is not tested, but there is a piece of info about HL-2070N: > Bro's d/l old Debian setup requires 2x manual dpkg after "sudo ln -s /etc/init.d/cupsys /etc/init.d/cups", Bro's setup assumes USB...So I did:
```
sudo ln -s /etc/init.d/cupsys /etc/init.d/cups
```
I don't think this is really neccessary either, am I wrong?

4. According to instructions at Brother I then did:
```
sudo ln -s /etc/init.d/cupsys /etc/init.d/lpd
```
This one I am sure is necessary though, it won't install the LPD driver unless it's done.

5. Installed the drivers:
```
sudo dpkg -i /home/jocke/old/mfc9070lpr-1.1.2-1.i386.deb
sudo dpkg -i /home/jocke/old/cupswrapperMFC9070-1.0.2-1.i386.deb
```
No errors, it just installs, yihaa! :)

6. According to instructions at Brother the link created in step 4 should be removed. Don't think this matters so much, but I did so:
```
sudo rm /etc/init.d/lpd
```

7. Attached printer to USB, then restarted cups:
```
sudo /etc/init.d/cupsys restart
```

8. On the web interface of CUPS I could add the printer, it was detected and the driver also showed. Everything seems ok.

9. I printed a test page, but nothing actually happens except for a message on the printer displaying "warming up" and "wait". Then it just stopps. The /var/log/cups/error_log looks ok (I guess) except for these errors:
```
[Job 2] /usr/lib/cups/filter/brlpdwrapperMFC9070: line 37: PPD=/etc/cups/ppd/MFC9070.ppd: No such file or directory
[Job 2] Error: -dx OFF :invalid option !!
[Job 2] Error: -dxt LONG :invalid option !!
...
get_file: 4 filename=/usr/share/cups/doc-root/favicon.ico size=-1
SendError: 4 code=404 (Not Found)
CloseClient: 4
CloseClient: Removing fd 4 from InputSet and OutputSet...
[Job 2] Error: -cp 1 :invalid option !!
[Job 2] Error: -sp PRINTER :invalid option !!
[Job 2] /usr/local/Brother//lpd/psconvert: line 51: exec: -r: invalid option
[Job 2] exec: usage: exec [-cl] [-a name] file [redirection ...]
```

The file /etc/cups/ppd/MFC9070.ppd exists and seems to be ok, but still the CUPS log file complains and says it doesn't. By default CUPS runs as user cupsys. Both directory ppd and file MFC9070 is owned by cupsys and has r+w, so the rights should be ok. Why does it complain? Is that message the reason it doesn't work? Please, can someone help me! I'm out of ideas and links regarding this. Help is really, really appreciated! ;) Thanx, and best wishes of course!

---

### Post by umuro on 2006-06-29
I exactly did the same thing for MFC7820N. The installation procedure described by Brother is the same.
And I got the same problem. That is, no errors during installation. And the printer becomes "stopped" on trying to print anything. Nothing can be printed. 

By the way, I went to brother support site to submit this error. But no. The error form does not work.

Is this a problem of Dapper or Brother, I wonder.

---

### Post by umuro on 2006-06-30
I did "sudo chmod 666 /dev/usblp0". And scanner started to work WITHOUT ANY PROBLEMS. However, printer error changed to "PRINTER NOT CONNECTED".

Sigh, at least. I have a working scanner now.

---

### Post by umuro on 2006-07-02
Howto: Brother MFC7820N USB Printer

My printer worked! So here is the final corrections for MFC7820N. The stardard installation has a few bugs after the latest upgrades. So that previously working recipes became invalid. But fortunately recovery is not too difficult.

First make sure that you have followed the steps in
[http://ubuntuforums.org/showthread.php?t=105703&highlight=mfc210]("http://ubuntuforums.org/showthread.php?t=105703&highlight=mfc210")

Go and create a udev rule so that our printer scanner is accessible at all. ```
sudo nano /etc/udev/rules.d/45-libsane.rule
```s 

Append those lines

```
# Brother MFC-7820N: We have to allow others because this is a printer as well
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="0181", MODE="666", GROUP="scanner"
```

You could put it in another file in that directory. But I put it there as it is a scanner as well...         

At this stage the scanner should be working already.

Now find the DeviceURI of the printer. The printer must be connected and turned on
```
lsusb
```                

This will give you something like
```
direct usb://Brother/MFC-7820N
```

Put that reference into printers.conf
```
sudo nano /etc/sups/printers.conf
```

For example, my printers.conf is now

```
# Printer configuration file for CUPS v1.2.1
# Written by cupsd on 2006-06-30 02:48
<DefaultPrinter MFC7820N>
Info MFC7820N
DeviceURI usb://Brother/MFC-7820N
State Idle
StateTime 1151628508
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy stop-printer
</Printer>

```

Restart cups
```
sudo /etc/init.d/cups restart
```

Oops. Before that empty your printer queue. Previously, I had queued 20 test pages. On restarting cups, all got printed!

---

### Post by umuro on 2006-07-02
```

sudo nano /etc/udev/rules.d/45-libsane.rules

```

Typo correction for above

---

### Post by umuro on 2006-07-02
Oops. I FORGOT to say... Reboot your machine after editing "/etc/udev/rules.d/45-libsane.rules".  Or do
```
sudo chmod 666 /dev/usblp0

```
Otherwise you cannot access the printer.

---

