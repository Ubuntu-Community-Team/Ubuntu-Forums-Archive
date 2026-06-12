---
title: "problems with cpu freq on socket 754 K8V"
date: 2007-08-17
forum: Hardware &amp; Laptops
---

### Post by nalleballe on 2007-08-17
Hi! Hope someone can help me. I have so much problems to read the cpu temp and freqs within the Xubuntu OS. It say that it cant read it. The thing is that within window$ it finds the lot directly. So it must be drivers that fail. Is there anybody who have some driverlinks for K8 kernel AMD sempron 3100 754 socket? I must see the temp cause i author a lot of dvds and i get hickups... 

THE FACTS: K8TEMP IS NOT SUPPORTED BY XSENSORS. What to do??

---

### Post by dcstar on 2007-08-23
> **nalleballe said:**
> Hi! Hope someone can help me. I have so much problems to read the cpu temp and freqs within the Xubuntu OS. It say that it cant read it. The thing is that within window$ it finds the lot directly. So it must be drivers that fail. Is there anybody who have some driverlinks for K8 kernel AMD sempron 3100 754 socket? I must see the temp cause i author a lot of dvds and i get hickups... 

THE FACTS: K8TEMP IS NOT SUPPORTED BY XSENSORS. What to do??

I have the same thing on my new M/B with a Sempron 3400+, on Gkrellm I get a "THRM" field which seems to be the CPU temp.

If you run the command "sensors", you should see the same value returned.

Install the Gkrellm package and you should be able to get an on-screen display (I also have disk temp reported).

---

### Post by Gourgi on 2007-12-10
> **nalleballe said:**
> 
THE FACTS: K8TEMP IS NOT SUPPORTED BY XSENSORS. What to do??

now is supported
[changelog here !!! ]("http://www.linuxhardware.org/article.pl?sid=07/10/09/1854255")
i just downloaded the package and installed it
> 
./configure
make
sudo checkinstall

you may need to install the sensors library 
```

sudo apt-get install libsensors-dev
sudo apt-get install checkinstall

```
and the checkinstall (it is used to make .deb packages and installs them ! :))

_run  _ :
>   /usr/local/bin/xsensors 

_unistall_ : 
if you used checkinstall then unistall it through synaptic

---

