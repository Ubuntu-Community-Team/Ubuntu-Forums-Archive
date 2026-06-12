---
title: "How do I copy scanner firmware to firmware folder?"
date: 2008-08-28
forum: General Help
---

### Post by welshmike on 2008-08-28
I've a BearPaw 1200CS scanner and am running Ubuntu 8.04. It does not work. I believe I need to copy firmware file A1fw.usb to folder /lib/firmware.
I installed Ubuntu using Wubi. I do not have write privilege to /lib/firmware and terminal does not allow me to become superuser.
Help please.

---

### Post by Stemp on 2008-08-28
> terminal does not allow me to become superuser.

Why ? aren't you the first user ? sudo doesn't work ?

---

### Post by timcredible on 2008-08-28
if you need to copy a file into a directory that you don't have permissions for, put 'sudo' in front of the copy command.  the password it asks you for is your password.

---

### Post by welshmike on 2008-08-28
Thanks Stemp & timcredible.
Sorry to be such a newb.

---

### Post by welshmike on 2008-08-28
Follow up:
I found out what to do elsewhere in these forums.
 sudo cp /home/mike/Desktop/A1fw.usb /usr/share/sane/gt68xx/
 sudo chmod a+r /usr/share/sane/gt68xx/A1fw.usb

Xsane now starts up my scanner.

What a wonderful helpful community here.

---

### Post by RomanIvanov on 2010-12-28
Works for me!!
Ubuntu 10.04.

I get A1fw.usb file from driver disk.
copy it and chmod it like welshmike say.

Download A1fw.usb file you can here: [http://www.meier-geinitz.de/sane/gt68xx-backend/](http://www.meier-geinitz.de/sane/gt68xx-backend/)

thanks to everybody!!

---

