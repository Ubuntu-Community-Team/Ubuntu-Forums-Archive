---
title: "Epson DX5000 Printer"
date: 2012-02-14
forum: Hardware
---

### Post by Shenarah on 2012-02-14
Hi

How do I view the ink levels on my Epson Stylus DX5000 printer? I could do this in Windows.

Thanks

---

### Post by plucky on 2012-02-14
> **Shenarah said:**
> Hi

How do I view the ink levels on my Epson Stylus DX5000 printer? I could do this in Windows.

Thanks

Open Software Centre and search for Epson and you should find a program called **mtink**.

See if that works for you.

Good Luck

---

### Post by Shenarah on 2012-02-14
I tried that and get the message:

No access to printer device file

Please make sure that mtlink has enough right for accessing the device.

On Denbian based system as Ubuntu you be a member of the group lp

Any suggestions please?

---

### Post by plucky on 2012-02-14
> **Shenarah said:**
> I tried that and get the message:

No access to printer device file

Please make sure that mtlink has enough right for accessing the device.

On Denbian based system as Ubuntu you be a member of the group lp

Any suggestions please?

Open Users & Groups and add yourself to group lp.

Log out and log back in and see if you are now a member of the lp group

From a terminal ```
id
``` will show you what groups your user has.

Good Luck

---

### Post by Shenarah on 2012-02-15
The output of 'id' is this.

uid=1000(stephanie) gid=1000(stephanie) groups=1000(stephanie),4(adm),7(lp),20(dialout),24(cdrom),46(plugdev),116(lpadmin),118(admin),124(sambashare)

Still get the same error from Mtink. :-(

---

### Post by mörgæs on 2012-02-15
Moved to the hardware forum.

---

### Post by cottfcfan on 2012-02-15
Shenarah..
I have the same problem, I use a DX7450 printer.
In previous versions of Ubuntu you just needed to install ink & its dependencies, and then run sudo ink from a terminal.
With 11.10, this doesn't seem to work anymore.
I'd be interested in any solution.

---

