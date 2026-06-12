---
title: "CUPS/Foomatic generic postscript level 1 printer. Unknown device: pswrite"
date: 2015-04-22
forum: Hardware
---

### Post by dipen.p on 2015-04-22
Hi everyone,

I'm having some trouble printing on Ubuntu 14.04 Trusty Tahr. I configured the Konica Minolta MFD printing at my university with a Generic brand and "Generic PostScript Level 1 Printer Foomatic/PostScript1 (recommended) (en)". This worked absolutely perfectly for a while, however a few weeks later (and updating via the software manager when needed) it's stopped working. Now, printing anything, even a simple line of text from gedit produces the following output:

[TABLE="width: 358"]
[TR]
[TD="class: x_descs"]Unknown device: pswrite
  
Unrecoverable error: undefined in .uninstallpagedevice
  
Operand stack:
  
        &#8203;defaultdevice[/TD]
[/TR]
[/TABLE]

I've done some research, and it looks like some sort of deprecated command in GhostScript but I'm not sure what I should do about this I haven't seen any fixes online. I've tried deleting and re-adding the printer(s) to no avail. 

Any help would be much appreciated, cheers.

EDIT: Additional information from the system administrator:

[TABLE="width: 734"]
[TR]
[TD="class: x_descs"]The Colour queue is a Konica Minolta C360SeriesPCL.  The B+W queue is a Konica Minolta 423SeriesPS.
 
Both of these queues require a username to be sent, but not a password.  This username can be sent in the traditional way, e.g. in cups lpd://username@hostname/queue[/TD]
[/TR]
[/TABLE]

---

### Post by dino99 on 2015-04-22
Seems you also hit that bug  [https://bugs.launchpad.net/ubuntu/+source/psutils/+bug/1378104](https://bugs.launchpad.net/ubuntu/+source/psutils/+bug/1378104)

---

### Post by dipen.p on 2015-04-23
> **dino99 said:**
> Seems you also hit that bug  [https://bugs.launchpad.net/ubuntu/+source/psutils/+bug/1378104](https://bugs.launchpad.net/ubuntu/+source/psutils/+bug/1378104)

Hi dino, thanks for your reply. Is there a fix for this? Looks simple enough from that thread. Should I be reporting this or something?

Edit: I've reported that I'm also effected by the bug, although I'm not sure whether I am exactly. I don't appear to have 'psutils' installed on my system. Could installing that package fix this problem?

---

