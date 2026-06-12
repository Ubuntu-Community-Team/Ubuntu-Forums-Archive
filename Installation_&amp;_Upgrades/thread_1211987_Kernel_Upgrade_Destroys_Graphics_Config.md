---
title: "Kernel Upgrade Destroys Graphics Config"
date: 2009-07-13
forum: Installation &amp; Upgrades
---

### Post by Makatozi on 2009-07-13
Hi All,
 
I need some help here. I did a upgrade on my kernel from .15 to .17. All works well but it now boots into low graphics mode.
 
I did a re-config of the graphics section but it continues to boot into low graphics mode.
 
1. Why does this happen?
2. What is the fix.
 
I am using Ubuntu 9.04.
 
Regards and thanks for the replys and help.

---

### Post by stretch427 on 2009-07-13
Well the reason this happens is because when you configure your graphics, you compiling it for that specific kernel, In your case .15, but when you upgrade, it is not compiled for .17. I had some of the same issues and I posted them here. Every time I would upgrade my kernel would break.

[http://ubuntuforums.org/showthread.php?t=1029029](http://ubuntuforums.org/showthread.php?t=1029029) 

Check it out... see if it helps.

Cheers!

---

### Post by master_kernel on 2009-07-13
You would need to reconfigure using: sudo dpkg-reconfigure -phigh xserver-xorg

I'm not sure if this was the method you used.

---

### Post by Makatozi on 2009-07-14
Thanks guys, I will continue until I get it right.

---

