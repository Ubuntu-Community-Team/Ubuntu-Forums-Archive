---
title: "Cannot boot Ubuntu: Kernel problem."
date: 2008-08-13
forum: General Help
---

### Post by Raphial on 2008-08-13
I select "Ubuntu" on the boot menu, and this is what I get:

"kernel Normal mode

Error 1: Filename must be either an absolute pathname or blocklist

Press any key to continue..._"


And of course, after continuing, everything else lists this as well. I used Wubi on a Windows XP system and installed Ubuntu on my drive G:\ instead of drive C:\.

Not sure what's going on here...any ideas?

---

### Post by spike.robinson on 2008-08-14
I think you want to install on drive C, or upgrade to Wubi 8.04.1

---

### Post by Raphial on 2008-08-14
> **spike.robinson said:**
> I think you want to install on drive C, or upgrade to Wubi 8.04.1

That's the one I used.

---

### Post by spike.robinson on 2008-08-14
Is the drive G: that you are installing on a real physical drive? And with a normal ATA or SCSI type of interface?

It might be worth installing on drive C: even a really small install, just to see if that's the problem.

---

### Post by t-timmy on 2008-10-31
I'm having the same problem with 8.10's wubi.
My system is on drive G: and I tried installing on F: and J:, same problem.
I don't want to install on G: as it's my system and if something gets screwed up I'm losing a lot of data.

Attached is a screenshot of my disks layout.

Please assist.

---

### Post by ago on 2008-10-31
The drive you install on does not matter provided it is not a raid or encrypted. If you have errors, press esc and try the other options, if you still have errors try to access /casper.log to get more info

---

### Post by t-timmy on 2008-10-31
> **ago said:**
> The drive you install on does not matter provided it is not a raid or encrypted. If you have errors, press esc and try the other options, if you still have errors try to access /casper.log to get more info

Hi,

I went ahead an installed on my system drive anyway, and it installed fine.
After your post I uninstalled it and tried to install it again on the problematic drives, but the boot went fine and the previous bug wasn't reproduced.
So I can't reproduce it again...

Anyway, works now, too bad I couldn't reproduce it.

Thanks

---

