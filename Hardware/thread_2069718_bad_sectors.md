---
title: "bad sectors"
date: 2012-10-11
forum: Hardware
---

### Post by eslam elbyaly on 2012-10-11
how to remove bad sectors , is not there a utility like chkdsk in windows?

---

### Post by keksior on 2012-10-11
The tool like chkdsk under linux is calles fsck. Read man to it maybe you'll find something usefull. 

Edit: 
You can also check tool called badclocks. There are a lots of articles about it.

---

### Post by drpjkurian on 2012-10-11
You can open the programme known as 'disk utility' from applications and you can check for disk health

---

### Post by ahallubuntu on 2012-10-11
FYI, Windows chkdsk doesn't "remove bad sectors."  It checks and fixes problems in the filesystem, when possible.  Chkdsk can attempt recovery of files that have bad sectors in them, but if sectors on the hard drive have physically failed, those files are going to be corrupt and gone for ever.

Any hard drive that develops "bad sectors" should be tested carefully and potentially discarded if it is failing.  But it depends what "bad sectors" means.  Hard drive firmware detects failed sectors and marks them "do not use" and replaces them with spare sectors on the drive ("reallocated sectors").  The operating system isn't involved this this directly.

---

