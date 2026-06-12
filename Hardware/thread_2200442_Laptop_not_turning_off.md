---
title: "Laptop not turning off"
date: 2014-01-19
forum: Hardware
---

### Post by fayorzrz on 2014-01-19
Hello i recently installed ubuntu 13.10 on my laptop (Satellite P75-A7200). It took me some time but i finally did it. Everything works perfect, the only thing is when i turn it off the ubuntu screen just stays there. If i restart de computer it restarts normally. So to turn off i have to press the power button of the laptop. When i turn on the laptop again there is no problem (at least ubuntu doesn't report anything).

I used the command

sudo lshw

to get my laptop details and i am including it as a attachment.

Thanks

---

### Post by egeezer on 2014-01-19
You might try
```
sudo shutdown now -h -P
```

The -h halts all running processes and the -P is for Power Off

---

### Post by MC Fox on 2014-01-19
Thanks, I have that issue also.  Too bad we can't use the OFF button!!!

---

