---
title: "no wireless interfaces.... ubuntu LIES!!"
date: 2008-11-14
forum: General Help
---

### Post by M!K3_$ on 2008-11-14
```
mike@mike-laptop:/$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

mike@mike-laptop:/$ 

```

Why does ubuntu lie to me....
How can i get ubuntu to see me wireless interface. I'm assuming it would be named ath0.

thanks
-mike

---

### Post by Amarsingh0793 on 2008-11-14
Why do it from the terminalwhen you can do it via an Appliation? Go to System > Preferences > Network Condifguration and follow the instructions it gives you.

---

### Post by binbash on 2008-11-14
What is your wireless card?

---

### Post by M!K3_$ on 2008-11-14
i am running ubuntu server, and it is headless. So that is why no GUI.

I have an D-link DWL-G510 (atheros based). It has worked before using Ubuntu 8.04 Desktop. I dont see why it wouldnt work using 8.04 server.

---

### Post by Zorael on 2008-11-14
Output of the following, please?
```
$ lshw -C network
```

---

### Post by wersdaluv on 2008-11-14
Easy with the title

---

