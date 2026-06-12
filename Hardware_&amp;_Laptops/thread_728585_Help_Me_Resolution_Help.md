---
title: "Help Me Resolution Help?"
date: 2008-03-19
forum: Hardware &amp; Laptops
---

### Post by ravindukelum on 2008-03-19
**[SIZE="4"][COLOR="Blue"]I have hp compaq v3614au 14.1 inch lap top ,how ever it's default resolution is 1280x800 and i set to it but when i see that in xp(dual boot) it's ok , but in ubuntu i can see it is not the optimal resolution and i have no adequet space on the desktop to retain the windows, please help me to set the proper resolution and screen type ,size(tell me the optimum configuration on this problem) .[/COLOR][/SIZE]**

---

### Post by Rocket2DMn on 2008-03-19
Try following this guide: [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)
If you still can't get it to work, post the outputs of
```
lspci | grep VGA
cat /etc/X11/xorg.conf
```

---

