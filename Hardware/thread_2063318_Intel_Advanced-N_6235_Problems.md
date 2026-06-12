---
title: "Intel Advanced-N 6235 Problems"
date: 2012-09-26
forum: Hardware
---

### Post by handyguy on 2012-09-26
I recently bough a Sager NP9150 with an Intel wireless card the 6235 to be exact and I get terribly slow speeds. At my University when I'm using windows I can easily get up to 100+ Mbps down, but when running Ubuntu 12.04 I can barely get 1 Mbps and the speeds are terrible for doing anything. I really want to use Ubuntu on my laptop, but with these terrible speeds its not an option. Please help me resolve this issue so I can go back to enjoying my OS of choice!

Thanks in advance.

---

### Post by Mikeb85 on 2012-09-26
> **handyguy said:**
> I recently bough a Sager NP9150 with an Intel wireless card the 6235 to be exact and I get terribly slow speeds. At my University when I'm using windows I can easily get up to 100+ Mbps down, but when running Ubuntu 12.04 I can barely get 1 Mbps and the speeds are terrible for doing anything. I really want to use Ubuntu on my laptop, but with these terrible speeds its not an option. Please help me resolve this issue so I can go back to enjoying my OS of choice!

Thanks in advance.

What kernel are you running?  If the chipset is Ivy Bridge (which would imply a newer modem) then use the newest stable Kernel you can (I believe that's 3.5 for Ubuntu?).  

I have a brand new ThinkPad with Intel Centrino Ultimate wireless and the WiFi is a little screwy on the 3.2-3.4 kernels...

---

### Post by handyguy on 2012-09-26
I'm running on 3.2, and you are correct I'm on Ivy Bridge, so if I updated to 3.5 would my problems be fixed?
Thanks

Edit: I installed the 3.5.1 kernel, but when I tried to connect to the internet, I was unable to actually connect to the internet, I was connected to the network, but could only sporadically connect to the internet and it felt extremely slow.  

> **Mikeb85 said:**
> What kernel are you running?  If the chipset is Ivy Bridge (which would imply a newer modem) then use the newest stable Kernel you can (I believe that's 3.5 for Ubuntu?).  

I have a brand new ThinkPad with Intel Centrino Ultimate wireless and the WiFi is a little screwy on the 3.2-3.4 kernels...

---

### Post by handyguy on 2012-09-27
So I rebooted again back into 3.5.1 and it seems to be working a little better, but performance is still nowhere near to how it is in Windows which is really disappointing, are there any other solutions to this problem?
Thanks

---

### Post by Mikeb85 on 2012-09-27
> **handyguy said:**
> So I rebooted again back into 3.5.1 and it seems to be working a little better, but performance is still nowhere near to how it is in Windows which is really disappointing, are there any other solutions to this problem?
Thanks

Not that I know of.  To the best of my knowledge, all Intel drivers are in the kernel, so you'll just have to wait.

I haven't personally noticed a difference in WiFi performance from the 3.5 kernel (on openSUSE 12.2) to Windows, but then again all broadband in Canada is so slow that the WiFi speed doesn't really matter.

---

### Post by detl_ on 2012-10-01
Hi , 
I installed Ubuntu 12.10 (Beta) today with Kernel 3.5.0 as I faced the same problem on my Dell XPS 14 Laptop. It has got the same Centrino card built-in like yours (6235).
Before I was running Ubuntu 12.04 and I thought I give the new version a try.
 
The performance on wireless is still very bad compared to other OS and compared to other cards on the same wireless network.

Has anybody got that Centrino card running fine on Linux ?

---

### Post by antti64 on 2012-12-26
I faced similar problems with new Samsung mp530-u3c laptop, which has intel centrino Advanced N 6235 WLAN+bt chipset. WLAN performance is terrible slow and it loses 90% packets. The problem occurs with quite old WLAN modem, which doesn't support n-mode. Same problem with Ubuntu and win7. Same hardware. But it works, when I disable n-mode of the WLAN chipset.
Antti

---

