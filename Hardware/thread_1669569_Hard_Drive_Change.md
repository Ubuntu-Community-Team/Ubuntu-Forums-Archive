---
title: "Hard Drive Change"
date: 2011-01-17
forum: Hardware
---

### Post by hawk01eye on 2011-01-17
I know this is a newbie question. However my friends primary hard drive just crashed.

She has a second one in the machine with another linux system already on it. What I am not sure of is how to make the secondary hard drive primary. Can anyone help with this?

If I understand correctly is that it has something to do with the pin setup on the back of the hard drive.

Thanks

---

### Post by damphoud on 2011-01-18
> **hawk01eye said:**
> I know this is a newbie question. However my friends primary hard drive just crashed.

She has a second one in the machine with another linux system already on it. What I am not sure of is how to make the secondary hard drive primary. Can anyone help with this?

If I understand correctly is that it has something to do with the pin setup on the back of the hard drive.

Thanks


You're probably referring to the jumper settings on the hard drive. Follow the link below for the position of the pin to place the drive as the master:

[http://www.recovery-soft.com/resource/images/install-ide-hard-drive-jumper.gif](http://www.recovery-soft.com/resource/images/install-ide-hard-drive-jumper.gif)

**Your drive may not match the link above--either try to find some documentation online (manufacturer website) or just simply look on the drive to see if the jumper settings are outlined on it...


In addition, if the drive is the only one connected to the mobo, and the bios is already set to boot from HDD, the system will just simply boot off of the drive you have installed (assuming you only have the good drive installed).


If the drive makes it past POST, but fails to load a linux distro, you may need to reinstall GRUB. A fairly easy how-to is below:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by hawk01eye on 2011-01-18
Thanks for the info. I will try it out tomorrow and report back.
 

> **damphoud said:**
> You're probably referring to the jumper settings on the hard drive. Follow the link below for the position of the pin to place the drive as the master:

[http://www.recovery-soft.com/resource/images/install-ide-hard-drive-jumper.gif](http://www.recovery-soft.com/resource/images/install-ide-hard-drive-jumper.gif)

**Your drive may not match the link above--either try to find some documentation online (manufacturer website) or just simply look on the drive to see if the jumper settings are outlined on it...


In addition, if the drive is the only one connected to the mobo, and the bios is already set to boot from HDD, the system will just simply boot off of the drive you have installed (assuming you only have the good drive installed).


If the drive makes it past POST, but fails to load a linux distro, you may need to reinstall GRUB. A fairly easy how-to is below:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

