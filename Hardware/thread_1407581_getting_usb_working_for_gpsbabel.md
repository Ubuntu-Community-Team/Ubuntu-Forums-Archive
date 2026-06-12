---
title: "getting usb working for gpsbabel"
date: 2010-02-15
forum: Hardware
---

### Post by gopher38 on 2010-02-15
Hello,

Trying to get my Garmin 305 GPS watch working with Ubuntu Jaunty on a HP DV9000 series notebook.  I used to use SportTracks to track my running under Vista, and now SportsTracks has been ported to Linux.  The problem is that you have to do an extra step in Linux.  SportTracks under Vista will read directly from the Garmin.  Under Linux, you have to get the data from the Garmin to a file, which you can then import to SportTracks.

Two methods were suggested to do this (transfer from Garmin to file in Linux): gpsbabel and garmintools.  I'm trying to get gpsbabel working.

gpsbabel comes in an rpm file, which I discovered that I needed alien to install on Ubuntu.  That's done, and it seems to be installed correctly (but I say that with 80% confidence).  For gpsbabel, you're supposed to run a command line command of the form: 

```
gpsbabel -t -i garmin -f /dev/ttyUSB2 -o gtrnctr -F outputfile
```

When I do that, I get the following:

```
[ERROR] XSERIAL: Cannot open serial port '/dev/ttyUSB2': No such file or directory
[ERROR] Cannot open serial port '/dev/ttyUSB2'
GARMIN:Can't init /dev/ttyUSB2

```

So I'm trying to find out where the right USB port is. Under "/dev" on my system, there is nothing of the form "/dev/ttyUSB#".  There is "tty#", and something like, "/dev/usbdev1.1_ep00", but no "/dev/ttyUSB#". 

If I look at the end of the "dmesg" command after plugging in the Garmin, I get:

```
[  709.432049] usb 3-1: new full speed USB device using ohci_hcd and address 4
[  709.636451] usb 3-1: configuration #1 chosen from 1 choice
```

So Ubuntu somehow sees it.  Also, "lsusb" gives:

```
Bus 003 Device 004: ID 091e:0003 Garmin International GPSmap (various models)
```

So, once again, Ubuntu seems to detect something is attached, but I don't know where/if it's assigned to a port.

One thing that is worrying, I found a thread on detecting USB ports (nothing to do with the Garmin though), and that person received something like this from "dmesg":

```
[ 22.444000] pl2303 3-1:1.0: pl2303 converter detected
[ 22.444000] usb 3-1: pl2303 converter now attached to ttyUSB0
[ 22.444000] usbcore: registered new interface driver pl2303

```

You can see that that person had a note from dmesg that said: "... now attached to ttyUSB0".  I get nothing like that in my message.

So my question is: how can I find out which /dev the Garmin is assigned to? Or, is it not working correctly at all, since I don't get the "attached to ttyUSB" part?

Thanks.

---

### Post by GeorgeVita on 2010-02-15
Hi **gopher38**,
to determine system activity for your USB peripheral (and a possible /dev/ttyUSBx port creation) follow the procedure below:

- boot without USB peripheral, **wait** for the system to load
- open a terminal window and try: **sudo dmesg -c**
(this will show all system activity till then and will 'clear' this log. Next simple **dmesg** will show only 'new' activity)
- from terminal: **lsusb**
- kernel version (from terminal): **uname -a**
- attach USB peripheral (and power it ON)
- **wait** 30-40 seconds
- from terminal: **dmesg**
- from terminal: **lsusb**

NOTE: do NOT post output of the 'sudo dmesg -c' as this is huge and without data for your peripheral!

Notice any changes comparing 'lsusb' outputs. The 'new line' must be the Garmin: > Bus 003 Device 004: ID 091e:0003 Garmin International GPSmap (various models)

Second 'dmesg' will show all system activity, possible drivers used and any communication port created. If you see something like **ttyUSB0** you can 'list it' using: **ls /dev/ttyU***

If not try to create one:
```
sudo modprobe usbserial vendor=0x091e product=0x0003
``` and check again dmesg.

Post any progress to follow up,
regards,
George

---

### Post by gopher38 on 2010-02-15
Hello George and thanks for the reply.  I seem to be making progress.

First,

uname -a gives:

```
Linux ubuntupass 2.6.28-18-generic #59-Ubuntu SMP Thu Jan 28 01:23:03 UTC 2010 i686 GNU/Linux
```

dmesg after clear gives:

```
[  248.612043] usb 3-1: new full speed USB device using ohci_hcd and address 3
[  248.816497] usb 3-1: configuration #1 chosen from 1 choice

```

And the only difference in lsusb is still:

```
Bus 003 Device 003: ID 091e:0003 Garmin International GPSmap (various models)

```

So I tried your modprobe command and this was added to dmesg:

```
[  452.039377] usbcore: registered new interface driver usbserial
[  452.039417] USB Serial support registered for generic
[  452.039462] usbserial_generic 3-1:1.0: generic converter detected
[  452.039640] usb 3-1: generic converter now attached to ttyUSB0
[  452.039676] usbcore: registered new interface driver usbserial_generic
[  452.039682] usbserial: USB Serial Driver core

```

And I now see a ttyUSB0 in /dev

So things are moving forward.

Now, when I run my gpsbabel command (gpsbabel -t -i garmin -f /dev/ttyUSB0 -o gtrnctr -F outputfile), I get:

```
[ERROR] GPS_Packet_Read: Timeout.  No data received.

GARMIN:Can't init /dev/ttyUSB0


```

So I'm going to do some googling on those messages and see if I can get this working.  I'll report back.

By the way, is the modprobe command below permanent, or do I have to add it to a script somewhere? Thanks.

---

### Post by GeorgeVita on 2010-02-16
Hi **gopher38**,
modprobe command is not permanent (issued from terminal), so you must repeat it after a new boot. When you finish your tests you can create a udev rule.

I found a similar thread: [http://ubuntuforums.org/showthread.php?t=1403398](http://ubuntuforums.org/showthread.php?t=1403398)

Another idea is to try a newer Ubuntu version (LiveCD?).

Regards,
George

---

### Post by gopher38 on 2010-02-17
Hello again George,

You got me on the right track.  Based on your suggestion above, I did a search on "rules.d", "gpsbabel" and "garmin", and I found this thread on another forum: 

[http://www.gpspassion.com/forumsen/topic.asp?TOPIC_ID=124627]("http://www.gpspassion.com/forumsen/topic.asp?TOPIC_ID=124627")

It shows what to add in the rules.d directory.  They also suggest a simple gui for gpsbabel, which I installed.  Both GPSBabel and SportTracks are working well now, except for Google satellite image display (Google maps works well).  A number of people mentioned this (minor) limitation, but I couldn't find a solution anywhere.

So for anyone in the future, Garmin 305 to Ubuntu jaunty using SportTracks and gpsbabel works well (just missing google satellite images).  

Thanks for your help.

---

### Post by konsum on 2010-03-30
Hello,

Has anyone used Altina GGM308U USB GPS device in linux. It works perfectly in Windows Vista, but it don't want to work in linux. My PC is Dell studio 1535 and linux version is Ubuntu 9.10.

I would be grateful for any help.
konsum

---

### Post by edopizza on 2010-04-24
I have a similar issue. 

**lsusb**
Bus 003 Device 007: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC

**sudo modprobe usbserial vendor=0x0403 product=0x6001**

**dmesg**
[11144.306373] usb 3-2: new full speed USB device using uhci_hcd and address 11
[11144.566666] usb 3-2: configuration #1 chosen from 1 choice
[11144.571862] usbserial_generic 3-2:1.0: generic converter detected
[11144.572728] usb 3-2: generic converter now attached to ttyUSB0

What puzzle me is that in the dmesg there is no citation of a driver like that one here above or in other threads: 

[  452.039676] usbcore: registered new interface driver usbserial_generic
[  452.039682] usbserial: USB Serial Driver core

Is the driver installed? 

**ls ttyUSB0 -l**
crw-rw---- 1 root dialout 188, 0 2010-04-24 11:52 ttyUSB0

After I use the script in this post 
[http://ubuntuforums.org/showthread.php?t=875478](http://ubuntuforums.org/showthread.php?t=875478) 
and I get the error 

[ERROR] SERIAL: tcgetattr error: Input/output error
[ERROR] Cannot open serial port '/dev/ttyS0'
GARMIN:Can't init /dev/ttyS0

I also tryed to chmod ttyS0 and ttyUSB0 but with no results. 

Any idea? 
Thanks in advance!

---

### Post by gcordoba on 2011-09-30
Hi,
I fond something that maybe helps Edopizza :

gpsbabel -t -i garmin -f usb:

(see [https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/202061?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/202061?comments=all) )

However, I have a remaining problem because what I need it to read a .gdb file (for grass gis import), thus telling gpsbabel that I will use an usb port is useless for me. 
Please, does anyone knows how to do that?

---

