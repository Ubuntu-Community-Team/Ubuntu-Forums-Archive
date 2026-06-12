---
title: "Checking temperature acer aspire one"
date: 2009-04-14
forum: Hardware
---

### Post by tron101 on 2009-04-14
Hi

I've just reinstalled Intrepid on my aspire one and installed acerhdf to control the fan. I used to have a one line command that I ran in the terminal to check the temperature on my previous install.

I can't remember what the line was and despite trawling all over the internet, I still can't find it...

So apologies if it is blindingly obvious but can anyone point me in the right direction please?

Thanks

---

### Post by tron101 on 2009-04-16
Found it! If it's useful to others:

$ cat /sys/class/thermal/thermal_zone0/temp

---

### Post by mshumer on 2011-02-20
comes back with "command not found" for me.
any recommendations?

I have acer aspire one running 10.04

---

