---
title: "Hey !! its exremely urgent..please reply me fast.."
date: 2009-11-29
forum: Hardware
---

### Post by pandeylavakesh on 2009-11-29
Initially I was having Windows XP Professional installed in my lappy. After that I installed Ubuntu 9.04. I upgraded it to Ubuntu 9.10. When XP and Ubuntu were there, while booting there came options to choose which OS to use Ubuntu or XP. But when I formatted my lappy and installed Windows 7 in place of Windows XP there is no option coming for Ubuntu. It is directly booting Windows 7. So how to get rid of this issue. Please help fast.
And when I will re-install Ubuntu with my DVD (Ubuntu 9.04) I will have to upgared it again, and I don't wanna do this **** thing again and again. So please guide me how to manage this without affecting my Windows 7 and Ubuntu 9.10.

Thanks in advance.....

---

### Post by apmcd47 on 2009-11-29
If your ubuntu partitions are still there you should be able to boot with the live disc, mount your ubuntu root partition and run grub to fix the issue. Unfortunately I don't know enough about grub to do this, but grub --help or man grub at the command line should help.

Changing the subject line of this thread to something like "installed Win 7 and lost Ubuntu" might get a better response.

Andrew

---

### Post by FrodeA on 2009-11-29
Hi!

Had a similar problem. Reinstalled several times with Grub (legacy) - but had to do some searching before finding help with Grub2. Maybe this link will help:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Cheers!

---

### Post by FrodeA on 2009-11-29
BTW, this is a good place to learn a bit about Grub2 :)

[http://members.iinet.net/~herman546/p20.html](http://members.iinet.net/~herman546/p20.html)

Hope this is of any help.

---

### Post by pandeylavakesh on 2009-11-29
Huuuuhhhhhhhh......:P
I am done....
that software helped me getting the hell out of there....
Thanks a tonnn......

---

### Post by arvevans on 2009-11-29
When you install Windows, it usually overwrites the boot section of your hard drive (they think they are the only OS that people might want to use).  Then when you try to re-boot and select Linux, you are not given the option of booting anything but Windows.  This is a situation that has been present since the first Windows installers.  There are several ways around this problem:
[LIST=1]
[*]Install the Windows OS first, then the Linux OS by allowing for Windows as a dual-boot option.
[*]Install Linux first, then Windows, but you will have to use a live-CD to re-build and install the dual-boot loader with options to boot both Linux and Windows.
[*]Install Linux, then Windows, then use a partial-install of Linux to re-establish the dual-boot boot loader.
[*]Set up separate hard drives for Windows and Linux, and make the Linux drive the first-boot device.  This involves some BIOS gymnastics to keep Windows installer from stomping on your Linux boot, so it is not recommended for new Linux users.
[*]Make a floppy drive boot disk for your Linux dual-boot and use this as the first boot option in your BIOS settings.
[*]Use a live-CD for booting into either Linux or Windows (it should ask which to bring up at boot time).
[/LIST]

There are other ways around this, but those listed above are the common ways to do it.

Arv
_._

---

