---
title: "Problem with foomatic-rip - printing failed"
date: 2010-05-24
forum: Hardware
---

### Post by trifaux on 2010-05-24
Hi everybody. I have a problem with cups and foomatic, basically i am not able to print. I specify that i was able to print in the past, then I started getting the "foomatic-rip failed" error.

The printer is HL-2030
The driver is the hl1250
The printer is shared on my network
Version of foomatic-filters: 4.0.0-0ubuntu9
Version of cups: 1.3.9-17ubuntu1

I was able to determine what causes the error, enabling log in /tmp/foomatic-rip.log, reported below. It misses a ' when invoking gs.
I still can't figure out how to make it work... Can anyone help me, please?

```

foomatic-rip version 4.0.0.195 running...
called with arguments: '765', 'trifaux', 'scheda-semplificata', '1', 'InputSlot=auto job-$
Getting input from file
Parsing PPD file ...
Added option PageSize
Added option ImageableArea
Added option PaperDimension
Added option EconoMode
Added option InputSlot
Added option Resolution
Added option MediaType
Added option HalftoningAlgorithm
Added option Font

Parameter Summary
-----------------

Parameter Summary
-----------------

Spooler: cups
Printer: HL-2030
Shell: /bin/bash
PPD file: /etc/cups/ppd/HL-2030.ppd
ATTR file:
Printer model: Brother HL-2030 Foomatic/hl1250 (recommended)
Options:  InputSlot=auto job-uuid=urn:uuid:8af0e382-3ae2-37ea-47dd-393d4d3d0414 lease-dur$
Job title: scheda-semplificata
File(s) to be printed:
<STDIN>

Ghostscript extra search path ('GS_LIB'): /usr/share/cups/fonts
Printing system options:
Pondering option 'job-uuid=urn:uuid:8af0e382-3ae2-37ea-47dd-393d4d3d0414'
Unknown option job-uuid=urn:uuid:8af0e382-3ae2-37ea-47dd-393d4d3d0414.
Pondering option 'lease-duration=300'
Unknown option lease-duration=300.
Options from the PPD file:
Pondering option 'InputSlot=auto'
Pondering option 'PageSize=A4'
Starting process "reset-file" (generation 1)
reset-file exited with status 0

================================================

File: <STDIN>

================================================

Filetype: PDF
Storing temporary files in /var/spool/cups/tmp
File contains 1 pages
Starting renderer with command: gs -dFirstPage=1  -q -dBATCH -dPARANOIDSAFER
-dNOPAUSE -sDEVICE=hl1250 -dEconoMode=0 -dDEVICEWIDTHPOINTS=595
-dDEVICEHEIGHTPOINTS=842 -r600x600 -dSourceTray=0 -dPaperType=0 -sOutputFile=-  -c '/Default << /SpotFunction { 180 mul cos exch 180 mul cos add 2 div }   bind /HalftoneType 1 /AccurateScreens true /Frequency 137 /Angle 37 /HalftoneName (Round Dot Screen) >> /Halftone defineresource sethalftone  << /HalftoneMode 1 /UseWTS false /Accura -f   /var/spool/cups/tmp/foomatic-DbSQoP

Starting process "kid3" (generation 1)
Starting process "kid4" (generation 2)
JCL: ^[%-12345X@PJL
<job data>

Starting process "renderer" (generation 2)
/bin/bash: -c: line 0: unexpected EOF during search of "'"
/bin/bash: -c: line 1: syntax error: unexpected EOF
renderer exited with status 2
Kid3 exit status: 1

```

---

### Post by buellman on 2010-05-24
You could open a Bugreport over at [launchpad.net]("https://help.ubuntu.com/community/ReportingBugs").

Greets. Buellman

---

### Post by trifaux on 2010-05-24
Thank you, I submitted a new [bug #584863]("https://bugs.launchpad.net/ubuntu/+source/foomatic-filters/+bug/584863"). I will post again for updates ;)

---

### Post by dino99 on 2010-05-24
your problem is there:  /bin/bash: -c: line 1: syntax error: unexpected EOF

you might try: remove/purge foomatic packages then reinstall

in case try installing a more recent foomatic packages 

[http://www.linuxfoundation.org/collaborate/workgroups/openprinting/database/foomatic](http://www.linuxfoundation.org/collaborate/workgroups/openprinting/database/foomatic)

---

### Post by trifaux on 2010-05-24
> **dino99 said:**
> your problem is there:  /bin/bash: -c: line 1: syntax error: unexpected EOF

you might try: remove/purge foomatic packages then reinstall

in case try installing a more recent foomatic packages 

[http://www.linuxfoundation.org/collaborate/workgroups/openprinting/database/foomatic](http://www.linuxfoundation.org/collaborate/workgroups/openprinting/database/foomatic)

i installed 4.0.4 , same as before.

---

