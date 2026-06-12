---
title: "X server and nvidia 9600GT"
date: 2009-05-20
forum: Hardware
---

### Post by vmicovic on 2009-05-20
Hello,

Last night i upgrade ubuntu to 9.4ver. x64 and now my graphic card don`t want work ...
I can`t start X with nvidia driver, i try ubuntu driver and official nvidia driver from nvidia.com
I search over internet this problem but didn`t have succes.
Can anybody help me a little.


Thank you.

---

### Post by skymera on 2009-05-20
Hi

I suggest using EnvyNG to install the driver.
I have done for years and it's always worked.

```
 sudo apt-get install enyng-gtk 
```

You can start Envy by:
Applications > System Tools > Envy

or Terminal:
```
 sudo envyng -t 
```

It's fairly simple :)

---

### Post by vmicovic on 2009-05-20
all right, i succes install after 2x unistalling the old drivers...
Now, i can`t enable desktop efect, i try:
> 
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
but nothing..
Can i get some advice and here?


btw: great aplication for installing nvidia/ati graphic cards... THANK YOU!!


update: glxgears say this:
> 
Error: couldn't get an RGB, Double-buffered visual


---

### Post by vmicovic on 2009-05-22
well? :s

---

