---
title: "libGL.so.1: cannot open shared object file: No Such file or directory"
date: 2007-10-22
forum: Hardware &amp; Laptops
---

### Post by cinematography on 2007-10-22
After following the manual ATI driver install method on [THIS]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.41.7_Driver_Manually") page, I can no longer open most of my graphics programs. I can't even open the screensaver.

[IMG]http://img.photobucket.com/albums/v611/tsharpfilm/de16028a.jpg[/IMG]

If you know of a way I can fix this problem, please let me know. Your help would be greatly appreciated. I don't even know where to begin with this.

---

### Post by cinematography on 2007-10-22
Never mind. I found a solution. Uninstall the stupid ATI drivers.

---

### Post by rev3nant on 2007-12-08
Anyone knows any other solution than installing previous drivers?

---

### Post by Yellow Pasque on 2007-12-08
This is a very common problem.
```
sudo ln -s /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1
```

---

### Post by kitovras on 2008-05-08
> **cinematography said:**
> Never mind. I found a solution. Uninstall the stupid ATI drivers.
could you tell me how to uninstall them ? ( i have the same problem with all the visual applications )

---

