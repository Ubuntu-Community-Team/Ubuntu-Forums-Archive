---
title: "Cdrecord and kernel2.6 conflict"
date: 2005-12-03
forum: General Help
---

### Post by dirkspeaksdutch on 2005-12-03
Hi. I just setup scsi emulation for my plextor cdrw (on x86 Breezy with 2.6 kernel)  and whenever I pass the command 'cdrecord -scanbus' I get errors galore.  The exact text is as follows.

cdrecord: Warning: Running on Linux-2.6.10-5-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: No such file or directory. Cannot open '/dev/pg*'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup . 

     The first thing I notice (which also throws me) is that is states try the command 'cdrecord -scanbus'. The other things that also bother me are that it's telling me that '/dev/pg*' (which I have no clue as to what it may be) won't open and also that the SCSI driver wont load. I've been looking all night for a solution unfortunately with no luck whatsoever. All help would be greatly appreciated!

---

### Post by wargames on 2005-12-03
I'm having a similar problem too. cdrecord does not seem to see my cd burner and I've been searching the forum and it appears that others have this problem too. I'm still looking for a solution.

---

### Post by micder on 2005-12-03
Just installed Ubuntu-5.10
Read your post and installed Gnomebaker, to see what I could do.
Well I burned a CD-image, no problems whatsoever.
However, cdrecord -scanbus gives the same message you had.

dirkspeaksdutch said:
> Hi. I just setup scsi emulation for my plextor cdrw

AFAIK scsi emulation is not needed anymore with a 2.6 kernel.

---

### Post by austin on 2006-01-31
I get the warning as well - from Gnomebaker - nevertheless it seems to work (haven't burned that much though)

---

