---
title: "Is Intel GMA x4500 compatible with Unity 3D (12.04 x64)"
date: 2012-06-17
forum: Hardware
---

### Post by UranUtan on 2012-06-17
Using Ubuntu 12.04 64 bits. Integrated Intel GMA X4500 GPU in Intel Chipset G41.

Additional Driver reported nothing. So I assume graphic driver is OK. However, it looks like I can only run Unity 2D.

Is the Intel GMA X4500 GPU compatible with Unity3D? Is yes, what should I do to activate it?

BTW, is there an easy way to check win which mode (2D or 3D) Unity is running? Currently I use Ubuntu Tweak and read the Overview section.

Thanks in advance for any help.

---

### Post by N0oki3 on 2012-06-17
[quote="UranUtan"]BTW, is there an easy way to check win which mode (2D or 3D) Unity is running? Currently I use Ubuntu Tweak and read the Overview section.[/quote]
before you log in you can choose session Ubuntu (3d) or ubuntu-2D

in terminal you can type ```
echo $DESKTOP_SESSION
```
to see which unity do you run and with 
```
/usr/lib/nux/unity_support_test -p
```you can check if you can use 3D.

But I'm afraid that you cannot. But also if you want to, you can try to force it. But it might not works as it should:
```
sudo vi /etc/environment
```
go to the bottom, press insert,  and add line 
```
UNITY_FORCE_START=1
```
press ESC and type 
```
:wq
```
to write and quit. 

Reboot PC and try to log in with ubuntu and type again ```
echo $DESKTOP_SESSION
```

---

