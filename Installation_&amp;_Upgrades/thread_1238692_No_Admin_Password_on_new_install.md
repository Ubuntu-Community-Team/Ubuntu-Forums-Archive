---
title: "No Admin Password on new install"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by yash8421 on 2009-08-12
Hello,

I just installed ubutu 9.04 (desktop) on usb drive. During install it never asked me for admin password. Now when I try "su" it gives me authentication failure. What is the best way forword? Do I reinstall ?

Thanks

Yash

---

### Post by pizza-is-good on 2009-08-12
I would try to reinstall yeah.
 
If you are running Ubuntu from the USB, then I beleive that it is the same as with a LiveCD: You are root, and dont't need authentication for anything.
 
However. I just tried it with my VBox Ubuntu (I use it for testing, so it is a clean install of Jaunty). 'su' didn't work either, not even with the correct password. My guess is that you are just going to sudo everything. Does that work? (sudo in front of all commands)

---

### Post by nerdzero on 2009-08-12
Hi yash,

The root account is disabled on Ubuntu by default.  You can use "sudo -i" instead.

---

### Post by yash8421 on 2009-08-12
Thanks. whoami gave me ubutu. So I assume I am root.

Yash

---

