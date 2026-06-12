---
title: "Canon 200 Lide"
date: 2011-12-27
forum: Hardware
---

### Post by shvman on 2011-12-27
I recently installed Ubuntu 11.10 (32 bit) after living on the "dark side" for many years.  Everything went fine until I tried to scan.  My Canon 200 Lide will not scan.

Tracing threads in this form, I saw several people get Canon scanners working after making some inquiries of the OS from the terminal.  So far, I've done the following and received the following output:

If I enter 'lsub', I get:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 006 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 006: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 003 Device 007: ID 0a5c:4503 Broadcom Corp. Mouse (Boot Interface Subclass)
Bus 002 Device 003: ID 04a9:1905 Canon, Inc. CanoScan LiDE 200

If I invoke 'scanimage -L', I get:

device `genesys:libusb:002:003' is a Canon LiDE 200 flatbed scanner


I'm at a loss at what to do next.  I have been to the sane site and I have seen a hypertexted 'genesys' next to the Canon 200 Lide entry.  

How do I proceed from here?

Thanks in advance...

---

### Post by wolfen69 on 2011-12-27
What app are you using to scan?

EDIT:And [this]("http://ubuntuforums.org/showpost.php?p=9462314&postcount=6") post may shed some light on it.

---

### Post by shvman on 2011-12-27
Thanks for the info.  

I was actually considering using something like Gscan2pdf, or some other application that would result in pdf files.  It sure would be convenient to have pdf files available for sending club notices etc.  via email.  I did see the Simple Scan application that is included in Ubuntu and think that's a bit too basic for my needs.  On the other hand, if that's my only choice, I'll live with it.  

I did see either the step by step post that you referred me to, or one similar to it.  Not knowing what's actually done in each step, I wondered which steps were applicable to my situation, given the results of my 'lsusb' and 'scan -L' output, or whether I should do them all exactly as specified?  I assume I would substitute 200 Lide for 100 Lide in the information, if that's important.  Also, I wonder if any of the numbers would change in that final line, and if so, how I could find out what to change them to?  

Meanwhile, I'm reading a book on Ubuntu and trying to figure out what all of this stuff means.  It's fun though....thanks.

---

### Post by wolfen69 on 2011-12-27
> **shvman said:**
> [SIZE=3]I assume I would substitute 200 Lide for 100 Lide in the information, if that's important.

[/SIZE]

No need to change that line, as any line starting with "#" gets ignored in linux.

---

