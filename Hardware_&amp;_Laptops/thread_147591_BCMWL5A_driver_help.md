---
title: "BCMWL5A driver help"
date: 2006-03-20
forum: Hardware &amp; Laptops
---

### Post by ShirenuWolf on 2006-03-20
I followed [this guide here]("http://www.ubuntuforums.org/showthread.php?t=25683&highlight=BCMWL5") very closely, yet I get a "Permission Denied" message when I try the following code:

```
for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
```

How do I fix this so it's -not- "permission denied"? :S I can't really use Ubuntu untill I have the internet up, so this is rather vital to my escape from crashville. :P

---

### Post by ShirenuWolf on 2006-03-20
Hate to double post 'n bump, but I really would tremendously appreciate some help with this - I've been stumped on it ever since I tried ubuntu, and I've been trying to solve it for months. =P

---

