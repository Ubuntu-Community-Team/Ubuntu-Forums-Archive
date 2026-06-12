---
title: "netbook printing"
date: 2010-04-14
forum: Hardware
---

### Post by lucaslanga on 2010-04-14
Hi all,

I have installed a copy of ubuntu netbook remix on an Acer Aspire One,my only problem is,I have an Extech printer that came with USB to Serial converter, so I've connected my USB into netbook slot,2) I run dmesg command and it picks it up as ttyUSB0,it prints fine from the command,now my problem is when I try to add new printer in GUI,it searches but cannot detect it.I went to System > under Administration > Printing > then New, the system start searching for printer but not finding it,the options that I have under Devices are : Other and Network Printer,and no printer detected in there, Is there another way of setting up a printer beside the one I went through,any assistance is appreciated.


Thanks in advance,
L

---

### Post by anglican on 2010-04-14
> **lucaslanga said:**
> Hi all,

I have installed a copy of ubuntu netbook remix on an Acer Aspire One,my only problem is,I have an Extech printer that came with USB to Serial converter, so I've connected my USB into netbook slot,2) I run dmesg command and it picks it up as ttyUSB0, it prints fine from the command, now my problem is when I try to add new printer in GUI,it searches but cannot detect it.I went to System > under Administration > Printing > then New, the system start searching for printer but not finding it,the options that I have under Devices are : Other and Network Printer,and no printer detected in there, Is there another way of setting up a printer beside the one I went through,any assistance is appreciated.


Thanks in advance,
L

I can't understand what you mean here "it prints fine from the command". Which command? Anyway, another way to add printers is via the CUPS web interface. Just put localhost:631 into your browser. See if you have more luck this way.

H

---

### Post by lucaslanga on 2010-04-15
> **anglican said:**
> I can't understand what you mean here "it prints fine from the command". Which command? Anyway, another way to add printers is via the CUPS web interface. Just put localhost:631 into your browser. See if you have more luck this way.

H
Hi H,

Thanks for the response,I meant typing cat /etc/hosts > /dev/ttyUSB0 works fine, I've also tried via CUPS by going to localhost:631 into my browser and it still doen's add it. Any ideas??

---

### Post by anglican on 2010-04-15
> **lucaslanga said:**
> Hi H,

Thanks for the response,I meant typing cat /etc/hosts > /dev/ttyUSB0 works fine, I've also tried via CUPS by going to localhost:631 into my browser and it still doen's add it. Any ideas??

Have you tried (from System > Administration > Printing > New)  choosing "Other" and then entering the device URI something like:

serial:/dev/ttyUSBO?baud=11500

(set your baud rate accordingly, of course)?

H

---

### Post by lucaslanga on 2010-04-15
> **anglican said:**
> Have you tried (from System > Administration > Printing > New)  choosing "Other" and then entering the device URI something like:

serial:/dev/ttyUSBO?baud=11500

(set your baud rate accordingly, of course)?

H
Hi H,

Thanks for being a player,
I have just adding it that way again and when I try to print to it this is what I get: "Unable to open device file:"/dev/ttyUSB0":Permission denied

Cheers,
L

---

### Post by anglican on 2010-04-15
> **lucaslanga said:**
> Hi H,

Thanks for being a player,
I have just adding it that way again and when I try to print to it this is what I get: "Unable to open device file:"/dev/ttyUSB0":Permission denied

Cheers,
L

So what does "ls -l /dev/ttyUSB0" show... and what happens if you try "sudo chmod 666 /dev/ttyUSB0" and "sudo chgrp lp /dev/ttyUSB0" (assuming ls -l doesn't show rw-rw-rw- for that device file)?

H

---

### Post by lucaslanga on 2010-04-16
> **anglican said:**
> So what does "ls -l /dev/ttyUSB0" show... and what happens if you try "sudo chmod 666 /dev/ttyUSB0" and "sudo chgrp lp /dev/ttyUSB0" (assuming ls -l doesn't show rw-rw-rw- for that device file)?

H
Thanks again H,

Here are my results from trying the command you've suggested and still can't come all right:

root@wdemos:~# ls -l /dev/ttyUSB0
crw-rw-rw- 1 root lp 188, 0 2010-04-16 07:44 /dev/ttyUSB0
root@wdemos:~# chmod 666 /dev/ttyUSB0
root@wdemos:~# chgrp lp /dev/ttyUSB0
root@wdemos:~#

When I try sending a job again,it still doesnt show any sign of printing.
It just sits in the que and doesn't go through.I tried restarting the printer and this didn't help.

Any ideas please!

Thanks,
L

---

### Post by lucaslanga on 2010-04-16
Thanks again H,

Here are my results from trying the command you've suggested and still can't come all right:

root@wdemos:~# ls -l /dev/ttyUSB0
crw-rw-rw- 1 root lp 188, 0 2010-04-16 07:44 /dev/ttyUSB0
root@wdemos:~# chmod 666 /dev/ttyUSB0
root@wdemos:~# chgrp lp /dev/ttyUSB0
root@wdemos:~#

When I try sending a job again,it still doesnt show any sign of printing.
It just sits in the que and doesn't go through.I tried restarting the printer and this didn't help.

Any ideas please!

Thanks,
L

---

### Post by anglican on 2010-04-16
> **lucaslanga said:**
> 
When I try sending a job again,it still doesnt show any sign of printing.
It just sits in the que and doesn't go through.I tried restarting the printer and this didn't help.

Any ideas please!

Thanks,
L

Does anything show up in /var/log/cups/error.log? Also, does it help if you send a subsequent pagefeed to the printer:

echo -en "\f" > /dev/[I]ttyUSB0

H
[/I]

---

### Post by lucaslanga on 2010-04-16
> **anglican said:**
> Does anything show up in /var/log/cups/error.log? Also, does it help if you send a subsequent pagefeed to the printer:

echo -en "\f" > /dev/[I]ttyUSB0

H
[/I]
Here are my results in error_logs:

E [16/Apr/2010:08:25:15 +0200] [Job 11] Unable to open device file "/dev/ttyUSB0
": Permission denied
D [16/Apr/2010:08:25:15 +0200] [Job 11] The following messages were recorded fro
m 08:25:15 to 08:25:15
D [16/Apr/2010:08:25:15 +0200] [Job 11] Adding start banner page "none".
D [16/Apr/2010:08:25:15 +0200] [Job 11] Adding end banner page "none".
D [16/Apr/2010:08:25:15 +0200] [Job 11] File of type application/pdf queued by "
wynns1".
D [16/Apr/2010:08:25:15 +0200] [Job 11] hold_until=0
D [16/Apr/2010:08:25:15 +0200] [Job 11] Queued on "Mobi2" by "wynns1".
D [16/Apr/2010:08:25:15 +0200] [Job 11] Sending job to queue tagged as raw...
D [16/Apr/2010:08:25:15 +0200] [Job 11] job-sheets=none,none
D [16/Apr/2010:08:25:15 +0200] [Job 11] argv[0]="Mobi2"
D [16/Apr/2010:08:25:15 +0200] [Job 11] argv[1]="11"
D [16/Apr/2010:08:25:15 +0200] [Job 11] argv[2]="wynns1"
D [16/Apr/2010:08:25:15 +0200] [Job 11] argv[3]="/tmp/com.google.chrome.SmmHCp"
D [16/Apr/2010:08:25:15 +0200] [Job 11] argv[4]="1"
D [16/Apr/2010:08:25:15 +0200] [Job 11] argv[5]="PageSize=A4 job-uuid=urn:uuid:0
a0ef578-1520-30c2-5527-3397c91a7898 job-originating-host-name=localhost"
D [16/Apr/2010:08:25:15 +0200] [Job 11] argv[6]="/var/spool/cups/d00011-001"
D [16/Apr/2010:08:25:15 +0200] [Job 11] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [16/Apr/2010:08:25:15 +0200] [Job 11] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [16/Apr/2010:08:25:15 +0200] [Job 11] envp[2]="CUPS_DOCROOT=/usr/share/cups/do


When I send subsequent pagefeed to the printer,it works like a charm,the only issue is when I send a file from GUI,it totally doesn't let me.

Thanks again for taking part in this.

Thanks,
Lucas

---

### Post by anglican on 2010-04-16
> **lucaslanga said:**
> Here are my results in error_logs:

E [16/Apr/2010:08:25:15 +0200] [Job 11] Unable to open device file "/dev/ttyUSB0
": Permission denied


I'm a bit puzzled by this, chgrp/chmod should have fixed it.

> **lucaslanga said:**
> 
D [16/Apr/2010:08:25:15 +0200] [Job 11] The following messages were recorded fro
m 08:25:15 to 08:25:15
D [16/Apr/2010:08:25:15 +0200] [Job 11] Adding start banner page "none".
D [16/Apr/2010:08:25:15 +0200] [Job 11] Adding end banner page "none".
D [16/Apr/2010:08:25:15 +0200] [Job 11] File of type application/pdf queued by "
wynns1".
D [16/Apr/2010:08:25:15 +0200] [Job 11] hold_until=0
D [16/Apr/2010:08:25:15 +0200] [Job 11] Queued on "Mobi2" by "wynns1".
D [16/Apr/2010:08:25:15 +0200] [Job 11] Sending job to queue tagged as raw...
D [16/Apr/2010:08:25:15 +0200] [Job 11] job-sheets=none,none
D [16/Apr/2010:08:25:15 +0200] [Job 11] argv[0]="Mobi2"
D [16/Apr/2010:08:25:15 +0200] [Job 11] argv[1]="11"
D [16/Apr/2010:08:25:15 +0200] [Job 11] argv[2]="wynns1"
D [16/Apr/2010:08:25:15 +0200] [Job 11] argv[3]="/tmp/com.google.chrome.SmmHCp"
D [16/Apr/2010:08:25:15 +0200] [Job 11] argv[4]="1"
D [16/Apr/2010:08:25:15 +0200] [Job 11] argv[5]="PageSize=A4 job-uuid=urn:uuid:0
a0ef578-1520-30c2-5527-3397c91a7898 job-originating-host-name=localhost"
D [16/Apr/2010:08:25:15 +0200] [Job 11] argv[6]="/var/spool/cups/d00011-001"
D [16/Apr/2010:08:25:15 +0200] [Job 11] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [16/Apr/2010:08:25:15 +0200] [Job 11] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [16/Apr/2010:08:25:15 +0200] [Job 11] envp[2]="CUPS_DOCROOT=/usr/share/cups/do


The rest looks fine.

> **lucaslanga said:**
> 
When I send subsequent pagefeed to the printer,it works like a charm,the only issue is when I send a file from GUI,it totally doesn't let me.

Thanks again for taking part in this.

Thanks,
Lucas

Isn't there a Printer Option to "SendFF"? Otherwise you could use a script on the lines of:

#!/bin/bash 
shift;shift;shift;shift;shift 
cat $* 
echo -en "\f"

Call it <somefilename> then use:

lpadmin -p Mobi2 -E -i <somefilename> -v serial:/dev/ttyUSB0?baud=11500

You might also want to investigate udev for setting appropriate group and permissions for your USB/serial adapter otherwise it will revert to the defaults every time you plug it in.

H

---

