---
title: "Printer ink level"
date: 2011-02-13
forum: Hardware
---

### Post by JFekete9076 on 2011-02-13
Hello.

I'm using Epson Stylus SX105 inkjet printer-scanner-photocopier, and escputil which queries the ink level of this printer. Unfortunately, the percentage of the black ink didn't change according to the program after printing a B&W image with best quality.
Could you suggest me a better program for tracking ink level?

Thanks in advance.

---

### Post by demonipuch on 2011-02-13
Hello

You can install and try mtink :
```
 sudo apt-get install mtink
```You'd probably need to add your user to lp group :
```
sudo adduser your_login lp
```

---

### Post by JFekete9076 on 2011-02-13
I tried the program, but there were two problem:
1. There is not my printer available in the selectable devices.
2. Selecting 'other printers', the program failed to show the ink levels. The program said that either the device was blocked, or out of paper sheet or ink.

I'm sorry for the typing mistake.

---

