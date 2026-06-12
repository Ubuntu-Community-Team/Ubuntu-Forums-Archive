---
title: "Dapper, VMware Server and the parallel port"
date: 2006-08-08
forum: Hardware &amp; Laptops
---

### Post by fjm03 on 2006-08-08
A Dapper host must have its **lp module** removed to utilize the LTP1 port on a virtual, Window's machine created by VMware Server 1.0 ```
 sudo rmmod lp
```

Dapper loads the lp module at boot and a configuration file needs to be edited if you want to prevent this default occurance. 

In the file **/etc/modules**:```
 Comment out the line that contains "lp" with a hash mark (#) at the beginning of that line
```

---

