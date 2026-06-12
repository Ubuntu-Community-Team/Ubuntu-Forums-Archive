---
title: "Unload xhci_hcd at suspend 10.10"
date: 2011-04-19
forum: Hardware
---

### Post by catlover2 on 2011-04-19
Hello,

This is how I fixed xhci_hcd from preventing suspend on my computer.
the solution i found here:[http://ubuntuforums.org/showpost.php?p=9117597&postcount=6](http://ubuntuforums.org/showpost.php?p=9117597&postcount=6)
But i had to change from:```

#!/bin/sh 
# Fix some issues with USB3
  
if [ "$1" = "suspend" ] 
then         
modprobe -r xhci 
fi
  
if [ "$1" = "resume" ] then         
modprobe xhci 
fi

```To:```
[COLOR=Black]
#!/bin/sh 
# Fix some issues with USB3

if [ "$1" = "suspend" ] 
then         
modprobe -r xhci[COLOR=Red]_hcd[/COLOR] 
fi
  
if [ "$1" = "resume" ] 
then         
modprobe xhci[COLOR=Red]_hcd[/COLOR] 
fi[/COLOR]
```
This does not work for hibernate, but it may not take much modification for hibernate.

Hope this helps someone!

Catlover

Asus M4A88T-V EVO/USB3, 
AMD Athlon II X4 640
Samsung Spinpiont F3 1TB HDD
Ubuntu 10.10 X64

---

