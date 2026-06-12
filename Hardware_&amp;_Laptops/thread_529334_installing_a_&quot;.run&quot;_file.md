---
title: "installing a &quot;.run&quot; file"
date: 2007-08-19
forum: Hardware &amp; Laptops
---

### Post by blufade on 2007-08-19
hi
i am a complete noob when it come to linux, i've just instaled ubuntu desktop edtion(X86) ...also i've downloaded the drivers for my AGP card from its website.....its a file with "run" externsion. Now, my question is, how do i install the package ?

---

### Post by tseliot on 2007-08-19
Is it an Nvidia card? If so, you can use the driver which is included in Ubuntu's repositories

---

### Post by blufade on 2007-08-19
oh yes, its  nvidia alright, msi personal cinema fx5200 excalty..
and do please direct me to this ubuntu repositories ,,,,is it some online database here in this forum ??

---

### Post by tseliot on 2007-08-19
Try method one of this guide:
[http://ubuntuforums.org/showthread.php?t=301499](http://ubuntuforums.org/showthread.php?t=301499)

---

### Post by pbcartwright on 2007-08-19
basically you open a terminal ( konsole) window and cd to the folder where the .run file is.

then:
chmod +x *.run
to execute it you do this:
sh FILE_NAME.run

---

