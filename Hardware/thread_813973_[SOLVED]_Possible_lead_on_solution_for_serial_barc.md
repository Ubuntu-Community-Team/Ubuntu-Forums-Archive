---
title: "[SOLVED] Possible lead on solution for serial barcode scanner users"
date: 2008-05-31
forum: Hardware
---

### Post by Fazz Munkle on 2008-05-31
What I did was install the scanner wedge (under WINE) I got with my Collectorz barcode scanner. A scanner that turns out to be a very generic type serial scanner (looks like the same one on this page I'm linking to). The scanner wedge was made by Microvision, Inc. Ok, looking them up on Google I found their website and then I searched their site for any mention of Linux. Voila:

[http://microvision.com/barcode/solutions/products/linux.html](http://microvision.com/barcode/solutions/products/linux.html)

Now, I have yet to look through it, but it seems to be very specific to getting scanners, especially serial scanners, working under Linux.

Going through a search of barcode scanners on the forums here I see a lot of people frustrated with not finding a solution for their serial (non-PS/2) scanners. This may lead to something good.

Reason why I suddenly got interested in looking this information up is because I downloaded and installed Tellico for my comic book collection and I just so happened to have an old Collectorz barcode scanner that I got some time ago. It came with a USB to serial adapter (essentially creating a new 3rd serial port on my computer). Neither plugging it into the physical serial port and the adapted serial port does anything.

Enjoy. :D

[edit: Reason why I think it might be useful is because it could be a clue. They offer a SDK for Windows and Blackberry, but maybe something for Linux can come from that. Maybe an OSS dev can call them up and ask if they can provide info on how to develop a scanner wedge for Linux. I dunno. Just thought it would be useful. If it isn't, I apologize. They mention Linux every once in a while on their site, but I can't find any mention of how that works]

---

### Post by Fazz Munkle on 2008-05-31
Found a possible solution, but it requires buying additional hardware:

[http://www.microvision.com/store/USB-Cable-Straight-p-7.html](http://www.microvision.com/store/USB-Cable-Straight-p-7.html)

Might be compatible for the Collectorz scanners. I'll buy one and let you guys know.

---

### Post by Fazz Munkle on 2008-06-09
Yup, the cable works. In the manual that comes with the cable you have to use the Flic Control Bar Codes instead of the Rov Control Bar Codes (like you'd think) to reset the Collectorz scanner to the factory settings. When you get the cable first select the keyboard function then go to the back couple pages of the manual, scan the Flic clear bar codes from memory option, scan the return to factory defaults bar code, scan the STX is false bar code and scan the 0 ms delay bar code.

This both clears your scanner and turns it into a true keyboard with return carriage. So you can use this with Google without the focus of the cursor going to the bookmarks side pane search box. You can also use it like this for such programs as Tellico and any program in a virtual machine environment since it's just seen as a keyboard. I'm currently rocking it in Tellico for my comic book collection.

---

### Post by montgoj on 2008-06-17
FAZZ Munkle,
Are you able to use the memory of the scanner (When you scan disconnected it should remember something like 500 barcodes) or are you just able to use it when attached by the cable?  I currently have the scanner, and am ordering the cable. I'm hoping to use it with alexandria for cataloging books.  
Jim

---

### Post by deadcyclo on 2008-07-31
Seing as there wasn't any Linux software that supported this scanner using Bluetooth and only one non open source, non free software wedge that supported cabled connections I wrote my own in Perl. My software supports both cabled and Bluetooth connection, works with the supplied R232 cable or the supplied R232 cable through a R232->USB adapter, supports both server mode where scans are put into a FIFO queue and retrieved with a keyboard shortcut and non-server mode where scans are immediately processed, supports the use of the scanners memory (disconnect the scanner, scan lots of codes, reconnect the scanner and all codes are transfered), allows automatically adding a simulated press of the <Enter> key after processing a code, and is licensed under GPL.

Download and instructions: [FlicServ 1.0](http://www.gsmblog.net/lang-en/linux-howtos/85-linux-wedge-driver-for-microvision-flic-barcode-scanner.html)

---

### Post by mazingaz on 2012-04-11
Thank you for the "FlicServ" Now I can scan using the ROV BT scanner, but Where do I create BT autoconnect script to?
I am very new at this and not very sure place to create /bin/bash (BT autoconne) script

---

### Post by deadcyclo on 2012-04-11
I haven't tested the script my self, but it's just a simple wrapper script. Just pop it in the top FlicServ folder and run it instead of the FlicServ script.

---

### Post by mazingaz on 2012-04-11
can you explain the process in detail? i am very  new and not sure i can follow your answer?
do you want me to create the some type of a file?  or can i just create /bin/bash in /FlicFile folder?
I am really new with the ubuntu and need step by step procedure.

I really appreciate the help in advance and sorry for the such ignorance.

---

