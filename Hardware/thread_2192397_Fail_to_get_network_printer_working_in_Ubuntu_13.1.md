---
title: "Fail to get network printer working in Ubuntu 13.10"
date: 2013-12-07
forum: Hardware
---

### Post by siabost on 2013-12-07
Hi,

Having moved from Ubuntu 13.04 64bit to 13.10 64bit I can't get my networked (of a PrintServer) to work.

It works on 13.04 (I still have a 13.04 laptop connected to my network) and I'm using the same settings and driver.
The printer is an Epson DX5000.
Oddly enough, it used to work on openSuse 12.3 also but refuses to comply now that I've moved that machine to 13.1!
It seems to be the same symptoms - I try and print a test page, it says it's spooling, gets to 4% or 8% and then stops. The printer loads a page and maybe prints the first few lines of  the document before stopping.

Running the Printer Setup utility from the Terminal and attempting to print a test page, I get the following:
```
kenny@kenny-Laptop:~$ system-config-printer
PASSTHRU
''
ps
''
lp
'\x00'
Caught non-fatal exception.  Traceback:
File "/usr/share/system-config-printer/probe_printer.py", line 412, in _probe_smb
    smbc_auth.failed (e)
File "/usr/share/system-config-printer/pysmb.py", line 180, in failed
    raise exc
NoEntryError: (2, 'No such file or directory')
Continuing anyway..
PASSTHRU
''
ps
''
lp
'\x00'
No ID match for device lpd://192.168.1.150/lp:
MFG:;MDL:;
No ID match for device lpd://192.168.1.150/lp:
MFG:;MDL:;
Unknown value for media-col: (unknown IPP value tag 0x34)
Choices: [u'media-bottom-margin', u'media-left-margin', u'media-right-margin', u'media-size', u'media-source', u'media-top-margin', u'media-type']
Selecting from choices: media-bottom-margin
Unknown value for media-col: (unknown IPP value tag 0x34)
Choices: [u'media-bottom-margin', u'media-left-margin', u'media-right-margin', u'media-size', u'media-source', u'media-top-margin', u'media-type']
Selecting from choices: media-bottom-margin
```

Any help appreciated.

Thanks.

---

### Post by pilot4fun on 2013-12-09
Hi,

I also moved from Ubuntu 13.04 64bit to 13.10 64bit and I, too, can't get my networked printer (Lexmark Optra E310) to work with much the same failing symptoms and result.  Sadly I am too much of a newbie to run a diagnostic process without instructions, but am happy to give it a shot if someone has a suggestion.  I, too, have other working systems (Ubuntu 12.10 and Windows 7) that continue to print just fine.

Recommendations welcome....

thanks!

---

### Post by siabost on 2013-12-20
*Bump* Anyone...?

---

### Post by pilot4fun on 2013-12-20
Sadly, I end up forwarding things to my Windows laptop for printing.  **embarassing**

---

