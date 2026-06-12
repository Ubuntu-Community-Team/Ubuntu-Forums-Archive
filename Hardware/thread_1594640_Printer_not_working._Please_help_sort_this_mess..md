---
title: "Printer not working. Please help sort this mess."
date: 2010-10-12
forum: Hardware
---

### Post by rdh61 on 2010-10-12
Hi,

The following is complicated...

Up till today my HP Deskjet F2180 printer was working fine. Now it is not. Here's how...

I had an unrelated bug (sign-in dialogue appears twice after screensaver), so decided to remove all packages that had been updated today, three at a time, and reinstall their earlier versions. The first (and only) three updates removed were:

ghostscript (8.71.dfsg.1-0ubuntu5) to 8.71.dfsg.1-0ubuntu5.2
ghostscript-cups (8.71.dfsg.1-0ubuntu5) to 8.71.dfsg.1-0ubuntu5.2
ghostscript-x (8.71.dfsg.1-0ubuntu5) to 8.71.dfsg.1-0ubuntu5.2

However, I couldn't find a way to roll back to the previous versions, plus when I removed them, other packages were removed as well:

bluez-cups
cups
cups-driver-gutenprint
foo2zjs
foomatic-db
foomatic-db-engine
hplip
openprinting-ppds
pnm2ppa
pxljr
splix
ubuntu-desktop

So I reinstalled them all with Synaptic, but the newly installed versions of the ghostscript packages are even newer than the ones update had given me today. For example:

ghostscript (8.71.dfsg.1-0ubuntu5.3)
ghostscript-cups (8.71.dfsg.1-0ubuntu5.3)
ghostscript-x (8.71.dfsg.1-0ubuntu5.3)

Now when I try to print my printer tells me:

/usr/lib/cups/backend/hp missing
or
/usr/lib/cups/backend/hp failed

I have looked in /usr/cups/backend and I can see the executable named 'hp' is present.

Please, how can I sort out this mess?

Many thanks.

---

### Post by rdh61 on 2010-10-13
Solved after re-booting today.

---

### Post by drpjkurian on 2010-10-13
Hi
Please mark the thread as solved]

---

