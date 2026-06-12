---
title: "Trying to install 13.04 on an Asus 1008HA"
date: 2013-07-31
forum: Hardware
---

### Post by sbutton on 2013-07-31
Right now I'm not having a lot of luck trying to install 13.03 desktop i386 onto an old Asus netbook. Right now it's running 10.10 just fine, but I can't get the USB drive to boot. 

Should this work? Am I doing something really dumb? (yes, hard to answer that).

I've disabled fastboot, and told it to look for the removable drive for boot. The drive appears to light up for a while, and it looks like it's going to boot (with the flashing _ at the top of the screen) and then it just boots into maverick as usual. 

Have not used this machine for a while, but can't see any reason it won't work. Any ideas?

Thanks,

---

### Post by sudodus on 2013-07-31
I think Lubuntu or Xubuntu should work well. And Ubuntu should boot for even if it might be very slow. I have not tried that particular model of Asus netbook, but other (even older ones).

- Have you checked with md5sum that the downloaded iso file was good?

- How did you make the boot USB drive?

- Have you tried to boot another computer with the boot USB drive?

---

### Post by sbutton on 2013-07-31
> **sudodus said:**
> I think Lubuntu or Xubuntu should work well. And Ubuntu should boot for even if it might be very slow. I have not tried that particular model of Asus netbook, but other (even older ones).

- Have you checked with md5sum that the downloaded iso file was good?

No, good point. Just trying to find the source md5.

- How did you make the boot USB drive?

netbootin

- Have you tried to boot another computer with the boot USB drive?

Aha! Yes, tried and it does exactly the same. Cheers. I'm downloading again.

---

### Post by Yellow Pasque on 2013-07-31
For a system like that, Xubuntu would probably run better.

---

### Post by angryfirelord on 2013-07-31
That sounds like the bootloader on the USB drive wasn't set up correctly. What utility did you use to write the ISO to the drive?

---

### Post by sudodus on 2013-08-01
> **sbutton said:**
> Aha! Yes, tried and it does exactly the same. Cheers. I'm downloading again.

Did you use Unetbootin? It usually works for me.

There could also be something wrong with the USB pendrive. 'All of them' work as mass storage, and most of them work as boot drives (but not all, because they are not completely standardized).

What brand and model is it?

See this link for more details [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

