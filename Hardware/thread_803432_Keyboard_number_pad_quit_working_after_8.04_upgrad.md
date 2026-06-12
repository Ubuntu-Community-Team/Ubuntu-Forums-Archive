---
title: "Keyboard number pad quit working after 8.04 upgrade"
date: 2008-05-22
forum: Hardware
---

### Post by jeffreydstark on 2008-05-22
Hi, I recently upgraded to 8.04 and my number pad has now quit working on my keyboard.  The only two keys that it recognizes are the numlock and enter keys, the others do nothing. Its just a standard PS2 ergonomic keyboard.  Does anyone have any ideas?

Thanks,
Jeff

---

### Post by toadfrog on 2008-05-23
i am having similar problems and would be grateful for any help.
my number pad has been working fine since upgrading from gutsy to hardy until about 4 hours ago... then it just quit as the OP described.  numlock & ENTER work... but the numbers themselves do not.

---

### Post by troupa on 2008-05-23
Odd, isn't it?  I just had this happen to me on my desktop machine.  So far the laptop's fine.  Only on mine the Num Lock button is the only one that works.

I tried connecting via VNC to the desktop from my laptop and using the numpad on the laptop.  the desktop machine does not respond to numpad keys there either.

---

### Post by toadfrog on 2008-05-23
problem solved:

system>preferences>keyboard
hit the "mouse keys" tab
uncheck the box "allow to control the pointer using keyboard"

hope it works for you too.

what is weird in my case is that everything was running fine for a month and then the number pad apparently changed its preferences all on its own.

---

### Post by jeffreydstark on 2008-05-26
Thanks Toadfrog, solved my problem too!!!

---

### Post by stewballs on 2008-07-02
This solved my issue too - thanks.

Using a  8.04 Hardy Heron on a 2.6.24-19-generic #1 x86_64 GNU/Linux

Rgds,
Stuart

---

### Post by marcantonio on 2008-07-02
Another me too here.  Thanks.

---

### Post by goforlinux on 2008-07-02
same here thanks

---

### Post by santonucci on 2009-09-03
toadfrog u rock!! thnx!!

---

### Post by Sennacherib on 2010-02-01
Adding my own thanks for this one too with the same issue in Karmic on a Acer laptop.  Cheers!

---

### Post by drewster1829 on 2010-10-18
Thanks! Had the same problem on an Acer 5251-1805 laptop with a Lucid Lynx that I cloned from my desktop install.  One day, the numpad just randomly quit working on my laptop, and I've NEVER had problems on my desktop. This setting fixed it. Thanks again. :)

---

