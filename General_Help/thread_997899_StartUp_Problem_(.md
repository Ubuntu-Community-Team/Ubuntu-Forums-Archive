---
title: "StartUp Problem :("
date: 2008-11-30
forum: General Help
---

### Post by banago on 2008-11-30
Hi guys,

I have a startup problem with Ubuntu 8.10. Everything was fine in Ubuntu 8.04. After I upgraded to 8.10 the computer does not start automatically. The load bar stops at a certain place and if I do not keep a key pushed on the keyboard, it won't start at all.

Can anyone help?

Thanks very much!

---

### Post by linux_tech on 2008-11-30
What video card do you have?
```
lspci | grep VGA
```
Also pls attach your xorg.conf 
```
cat /etc/X11/xorg.conf
```
Any messages?
```
dmesg
``` (attach txt)

---

### Post by KeyserSoze93 on 2008-11-30
press ctrl-alt-f1 when you get the loading screen, and post at which part it stops (what it says on the text console).

---

### Post by banago on 2008-11-30
> **linux_tech said:**
> What video card do you have?
```
lspci | grep VGA
```

Gave me:
```
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7000M (rev a2) (rev a2)

```

Also pls attach your xorg.conf 
```
cat /etc/X11/xorg.conf
```

Pease find attached the file for the above command.

Any messages?

```
dmesg
``` (attach txt)

Please follow this link to see the messages that came from the third command as it was to big and the forum did not allow it (10 kb bigger)

The link: [www.wplancer.com/command3.txt]("http://www.wplancer.com/command3.txt")

Thanks very much for your help

---

