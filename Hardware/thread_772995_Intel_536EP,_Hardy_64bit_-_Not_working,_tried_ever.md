---
title: "Intel 536EP, Hardy 64bit - Not working, tried everything I can think of"
date: 2008-04-28
forum: Hardware
---

### Post by Drakelet on 2008-04-28
Just installed Hardy 64bit and trying to get the Intel 536EP dial up modem working.  But, I can't.

I did "suo adduser james dip" and "suo adduser james dialout", both said already done.

I did "lspci | grep 536EP", and it said I had it.

The Administrator\Hardware Manager (something like that) found a non-installed nVidia-new, but nothing else.

I tried simply using the Network dialog thing, but it wouldn't connect, whatever port I used.

I tried pppconfig, set it up, nothing worked. ("pon" and "pon comcast")

I did "sudo wvdialconf /etc/wvdial.conf", and it said I had no modems installed, and mentioned something to do with setserial.

I downloaded "intel-536EP-2.56.76.0_23_02_2007.tgz".  When I tried "tar -xzf intel-526EP" (I renamed it), it came up with various error messages.  I tried different -* things, and one worked, some came up with errors.
Example error:
    tar: intel-536EP.tgz: Cannot open: No such file or directory
    tar: Error is not recoverable: exiting now
The one which worked, I tried to cd to it ("cd intel-536EP"), and it said it didn't exist.  I tried renaming it and moving it, but each time it claimed it didn't exist.
When I deleted it, and tried to repeat it with the same code, it didn't seem to work.  Same error message iirc.

I'm stuck, and annoyed.  Help?

Is the 536EP 64bit compatible?

---

### Post by Drakelet on 2008-04-29
Aww cmon, someone?  Anyone?

---

