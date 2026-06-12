---
title: "Samba Printer sharing between Ubuntu"
date: 2005-06-19
forum: Hardware &amp; Laptops
---

### Post by dan1928 on 2005-06-19
I have a home network setup with Samba running. I had two printers shared from a Windows 2000 box, but recently moved a printer (parallel canon bjc printer) to one of my ubuntu boxes. My problem is that I can't seem to figure out how to share and access that printer via my networked computers. I am listing the relevent (?) sections of my smb.conf below:

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
;   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
;   printer admin = @ntadmin

###This part below is in the "Share Definitions" section###
[printers]
   comment = All Printers
   browseable = yes
   path = /tmp
   printable = yes
   public = yes
   writable = yes
   create mode = 0700
   guest ok = yes

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = yes


Anyway, I can't get my other Ubuntu box or my mac (OS X) to see/connect to this "shared" printer. There's something I'm not doing right, obviously, but I can't firgure out what. I'd appreciate any help. Thanks.

---

### Post by netrattler on 2005-06-19
See Wylfing post he gives complete instructions.

[http://ubuntuforums.org/showthread.php?t=20384](http://ubuntuforums.org/showthread.php?t=20384)

Hope this helps,
Joe

---

### Post by dan1928 on 2005-06-19
Thanks Joe, Not exactly sure what it was, but I changed my smb.conf to resemble the changes in that thread and things are working fine. I searched through earlier threads, but I guess I missed that one. Thanks again!
-Dan

---

