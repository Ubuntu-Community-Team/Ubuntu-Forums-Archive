---
title: "Ubuntu flashing caps lock key suspend 11.04"
date: 2011-07-26
forum: Hardware
---

### Post by joseph2153 on 2011-07-26
My laptop:
HP dv51108ax
Amd Turion x64 x2
4gb ram
Ubuntu x86 11.04 with pae
Ati Raedon mobility 3450

The problem: I try to put my laptop into suspend, however the caps lock button will just keep flashing forever. eventually I just hold down the power button to turn it off, Does anyone know of a fix for this? I haven't had this problem in 10.04 or 10.10.

---

### Post by kerry_s on 2011-07-27
Flashing caps lock is a kernel crash, what ati driver you running?

---

### Post by joseph2153 on 2011-07-27
ati propietary FGLRX driver

---

### Post by miesogeno on 2011-08-01
in my case it was the new virtualbox 4.1 modules, disable them from starting up (with bum or rcconf) and try to suspend again.

---

### Post by wujastyk on 2011-08-03
> **miesogeno said:**
> in my case it was the new virtualbox 4.1 modules, disable them from starting up (with bum or rcconf) and try to suspend again.

Thinkpad T500, Natty:
2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:05:14 UTC 2011 i686 i686 i386 GNU/Linux


Thank you!  This was the problem for me too. I used bum as you suggested, and got a good suspend.  So now I've fallen back from Virtualbox 4.1 to 4.0, and all is well.  I'll try 4.1 again in a few months.

Many thanks!  

Dominik

---

### Post by kaoul on 2011-09-03
I had the same problem with my toshiba. But I didn't want to go back to virtualbox 4.0. So I created this file as a solution :

```
root@tshb:/usr/lib/pm-utils/sleep.d# cat 54virtualhook 
#!/bin/sh
# Unload vboxdrv for a bug workaround on suspend on ubuntu 11.04

. "${PM_FUNCTIONS}"

suspend_vb()
{
    service vboxdrv stop
}

resume_vb()
{
    service vboxdrv start
}

case "$1" in
    hibernate|suspend)
        suspend_vb
        ;;
    thaw|resume)
        resume_vb
        ;;
    *) exit $NA
        ;;
esac

```

After a chmod +x on this file, when I suspend from the menu it works.

But ubuntu 11.04 has a weird bug, I just need to move my mouse to prompt the "locked screen" just before it suspends to get the resume right. If I don't move de mouse at suspend, resume is just a black screen.

---

