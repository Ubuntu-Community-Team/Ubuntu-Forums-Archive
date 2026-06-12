---
title: "laptop, screen, turns off, still get sound,wubi"
date: 2008-02-16
forum: Hardware &amp; Laptops
---

### Post by chuckmanbob on 2008-02-16
i have a sony vaio fziis and i desperatley want ubuntu to run on it. i have tried installing wubi several times but each time after finishing installation i see  the logo as it loads up and then the screen goes black. i can still hear sound but i cannot see anything i really want it to work can anyone help me please, or at least direct me to someone who can help me.
thank you 
my email is [email]chuckmanbob@hotmail.co.uk[/email]

---

### Post by roofninja on 2008-02-16
I am not sure if this will fix what your problem with wubi but I have been through something very similer to it.  Give it a try and see if it works for you.

1. Bring up a Terminal.
2. Run "sudo gedit /boot/grub/menu.lst"
3. delete "quiet" twice and "splash".
4. save and reboot to see if it works.

---

### Post by chuckmanbob on 2008-02-22
thanks for the help i'll give that a go
:)

---

### Post by chuckmanbob on 2008-02-22
i tried that, it goes says it is opening display manager but the screen still goes off. i think i might need a different driver for my video card. if so how can i download that.
thank you for your help

---

