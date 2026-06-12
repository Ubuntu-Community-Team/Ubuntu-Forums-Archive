---
title: "Printer Sharing"
date: 2005-12-26
forum: Hardware &amp; Laptops
---

### Post by dbassett on 2005-12-26
I was happy to see Ubuntu recognize my printer (USB).
I haven't found any way to share this printer yet.

I have been sharing it when booted from OSX. Now my wife wants to print something from her powerbook but I don't want to reboot in to OSX yet. Still playing with Ubuntu.

---

### Post by emperor on 2005-12-26
The Samba Server will allow you to share a printer much like Windose!

It may be a struggle the first time to get samba configured correctly (smb.conf), but after that it works great!
My wife runs Windows about 10% of the time, the rest of us run Linux only!

[http://www.tldp.org/HOWTO/Debian-and-Windows-Shared-Printing/sharing_with_windows.html]("http://www.tldp.org/HOWTO/Debian-and-Windows-Shared-Printing/sharing_with_windows.html")

my /etc/samba/smb.conf file's printer entry:

[printers]
        path = /var/spool/samba
        guest account = smbuser
        guest ok = yes
        printable = yes

NFS may also work on OSX, see this thread:
[http://www.ubuntuforums.org/showthread.php?t=62034&highlight=printer+sharing]("http://www.ubuntuforums.org/showthread.php?t=62034&highlight=printer+sharing")

---

### Post by fishfillet on 2006-01-01
here is my how-to on printer sharing: [http://gerona.gov.ph/davidjr/?p=57](http://gerona.gov.ph/davidjr/?p=57)

i hope it helps!

---

