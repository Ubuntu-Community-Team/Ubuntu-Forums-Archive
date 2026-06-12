---
title: "Urgent help needed !!!"
date: 2009-05-04
forum: Hardware
---

### Post by sheel1234 on 2009-05-04
So I was messing around in Ubuntu 9.04 trying to fix some issues.
And when I booted Ubuntu in Recovery mode, I found nothing wrong.
however when i clicked resume the code said  my fglrx driver failed,
leaving my screen with odd lines on it

I want to know if there is anyway to reinstall frglx driver 

Specs: ATI Radeon graphics card with Dell Insiprion 1501 

Please help I need for my computer to work again

---

### Post by NCLI on 2009-05-04
Start by booting into recovery and running "sudo aticonfig --initial -f".

If that doesn't work, do: "sudo apt-get remove xorg-driver-fglrx && sudo apt-get install xorg-driver-fglrx"

If that also fails, choose to restore the default graphical settings in recovery mode.

---

### Post by sheel1234 on 2009-05-04
Thanks man for some reason it works now:P

---

### Post by NCLI on 2009-05-04
After you followed my suggestion, or just out of nowhere? xD

---

