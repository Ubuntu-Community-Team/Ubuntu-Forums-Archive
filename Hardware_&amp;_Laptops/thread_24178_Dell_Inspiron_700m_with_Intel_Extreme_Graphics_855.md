---
title: "Dell Inspiron 700m with Intel Extreme Graphics 855 GM"
date: 2005-04-05
forum: Hardware &amp; Laptops
---

### Post by mrm on 2005-04-05
Greetings,

I have a Dell Inspiron 700m with the Intel Extreme Graphics 855 GM card built in. For some reason my Ubuntu install can't recognize the proper resolution for the screen. It's one of those wide-screen laptops.

The proper resolution should be 1280x800

Any ideas on how to fix this would be greatly appreciated.

---

### Post by Charles Halliday on 2005-04-05
This guide helped me on my 700m warty installation.

[http://www.celifornia.com/documents/dell700m.html#3._855resolution](http://www.celifornia.com/documents/dell700m.html#3._855resolution) 

The one thing that the guide doesn't mention is that you usually need to change the permissions of "startupscript" for rcconf to be able to run it.

Try, 

     # chmod a+x startupscript

while in folder /etc/init.d/

---

