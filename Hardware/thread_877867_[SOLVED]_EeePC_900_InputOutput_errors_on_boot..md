---
title: "[SOLVED] EeePC 900 Input/Output errors on boot."
date: 2008-08-02
forum: Hardware
---

### Post by atomp on 2008-08-02
I believe that this is the correct forum area for this particular problem. I am running the latest standard Eeebuntu (i am aware that this is not standard Ubuntu, but it is a very closely linked distribution and i believe this problem is an Ubuntu issue rather than an Eeebuntu specific issue, i may however be mistaken), on an Asus EeePC 900.

It recently started failing to boot. With the boot screen disappearing and the text based display showing an issue with "*Starting system log daemon" as well as "*Starting kernel log daemon". These problems have listed beneath them various Input/Output errors relating mostly to /var/log (i think, i cannot say for sure right now, as it has run out of battery and i haven't got my charger).

I can start up Ubuntu into text-based mode by using "dmesg". But i cannot do a great deal when in this text based mode, as practically every command returns an input/output error and fails.

If this is an Eeebuntu specific issue then i am quite happy to take it to their forum rather than here.

Cheers for your time.

---

### Post by kazacy on 2008-08-02
Maybe your SSD its faulty. Try to boot from a USB stick with a mini linux on him ( personally i use this: 
[http://www.tux.org/pub/people/kent-robotti/looplinux/rip/]("http://www.tux.org/pub/people/kent-robotti/looplinux/rip/")
or this:
[http://sysresccd.org/Main_Page]("http://sysresccd.org/Main_Page")
), mount the internal SSD and try to write on him some data. Most of the time if your SSD its bad you will see alot of errors when you write.

---

### Post by atomp on 2008-08-02
Ok, cheers for the response. I used a live USB and took a look at the drive, turns out Ubuntu had used the available space.

I think it was down to the fact that the Eee 900 uses a 4gb SSD and a 16gb SSD and by default it likes to install to the 4gb. Ubuntu filled that space, thus the Input/Output error (I assume, this is because it could no longer write to the drive).

Either way, a fresh install of Ubuntu (Eeebuntu) to the larger drive seems to have done the trick.

I'd also like to take the opertunity to thank both the developers and the community for thier hard work on Ubuntu, maintaining Ubuntu and helping users, you're doing a great job and really opened my eyes to what using a computer should be about.

---

