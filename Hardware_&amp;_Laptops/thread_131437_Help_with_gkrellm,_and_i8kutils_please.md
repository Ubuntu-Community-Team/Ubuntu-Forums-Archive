---
title: "Help with gkrellm, and i8kutils please"
date: 2006-02-16
forum: Hardware &amp; Laptops
---

### Post by RichGags on 2006-02-16
Hi, I have a Dell Inspiron 8100.  I installed gkrellm and the i8k plugin for the fan control through the Synaptic package manager.  I also installed the i8kutils.  I am getting an error through gkrellm that says "missing proc file". 

Ive been reading the forums for help and it seems that the solution of putting the line options i8k force=1 in my etc/modules is not working for me.

Check out what happens when I do this:
```
root@ubuntu:/usr/bin# i8kctl
can't open /proc/i8k: No such file or directory
root@ubuntu:/usr/bin# i8kfan
can't open /proc/i8k: No such file or directory
root@ubuntu:/usr/bin#

```

Its seems I dont even have a proc/i8k

Any help would be greatly appreciated.  I used to have gkrellm and the Dell i8k plugin working in Fc4, but I just came over to Ubuntu and I cant seem to get it working.  

Thanks!
Rich

---

### Post by RichGags on 2006-02-16
I was able to get the gkrellm plugin to work and display and control the fans by type this at a root prompt:
```

/sbin/modprobe i8k force=1
```

Where can I put this so that is run when the computer starts?  In FC3 it was in /etc/rc.local...  Where does it go in Ubuntu?  

Thanks!
Rich

---

### Post by toorima on 2006-02-16
/etc/modules

i8k force=1

---

### Post by RichGags on 2006-02-16
Cool.  Got it.  Thanks!

---

