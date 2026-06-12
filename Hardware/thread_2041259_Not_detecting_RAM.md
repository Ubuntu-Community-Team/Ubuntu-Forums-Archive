---
title: "Not detecting RAM"
date: 2012-08-12
forum: Hardware
---

### Post by Linuxpal on 2012-08-12
Hello! I placed a 8GB SO-DIMM in my Asus Zenbook laptop, but Ubuntu just seem to register the integrated 2GB memory when it should be 10GB in total. I am using the 64-bit version. Please help me out.

---

### Post by sanderj on 2012-08-12
If you run the below commands, you will get all info on memory found and used:


```
wget http://www.appelboor.com/dump/check-my-memory.py
python check-my-memory.py 
sudo python check-my-memory.py 
```



HTH

---

