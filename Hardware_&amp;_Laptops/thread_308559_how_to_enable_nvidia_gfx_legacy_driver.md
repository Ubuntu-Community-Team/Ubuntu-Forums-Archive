---
title: "how to enable nvidia gfx legacy driver"
date: 2006-11-28
forum: Hardware &amp; Laptops
---

### Post by holylucifer on 2006-11-28
okay this is my screen,

[http://img89.imageshack.us/img89/3760/screenshot2vr8.png](http://img89.imageshack.us/img89/3760/screenshot2vr8.png) , 

I am a newbie,so how do i change this nv to nvidia, when i put in the sudo command it basicly is doing something or not...

please help , as you see in manager it is installed.

---

### Post by holylucifer on 2006-11-28
And i am not on edgy , ubuntu , the dapper drake one.

---

### Post by halfvolle melk on 2006-11-28
> **holylucifer said:**
> so how do i change this nv to nvidia
```
sudo gedit /etc/X11/xorg.conf
```
And find the Device section. It will say 'Driver "nv"'. Change it and save the file. The changes will take effect when you start a new X-session. You may want to back up your current xorg.conf first.

---

### Post by kelxso on 2006-11-28
i suffer from the same problem only after i change nv to nvidia, it still wants me to change nv to nvidia and gives me his^ error message](*,)

---

### Post by holylucifer on 2006-11-28
i have got mine to work, just change nv to nvidia all in lower case, save and then reboot, and then you will see the nvidia logo,

---

### Post by kelxso on 2006-11-28
Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

thats what ive got now, ive restarted twice and its still not going for it

---

### Post by kelxso on 2006-11-28
i saw the nvidia at start up but i still got the error message to change from nv to nvidia

---

### Post by halfvolle melk on 2006-11-28
The legacy driver won't work for a FX5200. You'll wan't to install the 'normal' one.
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by halfvolle melk on 2006-11-28
> **kelxso said:**
> i saw the nvidia at start up
K, so maybe it's working. Check with
```
glxinfo | grep direct
```

---

### Post by DapperMe17 on 2006-12-01
When changing "nv" to nvidia", how do you actually save the change?

---

### Post by halfvolle melk on 2006-12-01
Depends on the editor you use. For one thing you'll need to edit the file with root privileges. As for editors here's how to use Nano:
[https://help.ubuntu.com/community/NanoHowto](https://help.ubuntu.com/community/NanoHowto)
Personally I don't like it and generally prefer Vim:
[https://help.ubuntu.com/community/VimHowto](https://help.ubuntu.com/community/VimHowto)
Then there's Gedit which works much like Notepad and such.

---

