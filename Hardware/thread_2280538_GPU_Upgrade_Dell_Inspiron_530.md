---
title: "GPU Upgrade Dell Inspiron 530"
date: 2015-05-31
forum: Hardware
---

### Post by mamamia88 on 2015-05-31
I just got this pc and want to upgrade it to perform better. I already grabbed an e8600 for $20 and was hoping to get something better than the hd3450 in it without upgrading the psu.  Any reccomendations?  I have an intel pcie nic and a xonar sound card so not sure if that factors into the psu consumption much.  It's a 300w psu

---

### Post by Yellow Pasque on 2015-05-31
GTX 750Ti would probably be your best bet (it's very power efficient and doesn't need a 6-pin connector because it draws all its power from the slot). The CPU and GPU are the main things to look at with power consumption. 65W for the CPU under load and 60W for the GPU under load = 125W. The rest of the system might use 25W. You're still well under 300W. The questions I have are:
1. Do you have an Inspiron 530**s**? That will limit your options a lot if you do.
2. Can the PSU actually deliver more than 300W? Dell actually used decent PSU's from what I read and they may even be underrated.
3. Is there enough amperage on the 12V rail? There should be, but you may want to look at the specs.

---

### Post by mamamia88 on 2015-05-31
> **Temüjin said:**
> GTX 750Ti would probably be your best bet (it's very power efficient and doesn't need a 6-pin connector because it draws all its power from the slot). The CPU and GPU are the main things to look at with power consumption. 65W for the CPU under load and 60W for the GPU under load = 125W. The rest of the system might use 25W. You're still well under 300W. The questions I have are:
1. Do you have an Inspiron 530**s**? That will limit your options a lot if you do.
2. Can the PSU actually deliver more than 300W? Dell actually used decent PSU's from what I read and they may even be underrated.
3. Is there enough amperage on the 12V rail? There should be, but you may want to look at the specs.

Just the normal 530.  I doubt it can deliver more than 300w.  I got the entire system for $60 so don't feel like spending more than the cost of the entire system for a gpu so that would pretty much rule out the 750ti unless you can tell me where I can get one cheap?

---

### Post by mamamia88 on 2015-06-01
How about [http://www.newegg.com/Product/Product.aspx?Item=N82E16814125681&ignorebbr=1](http://www.newegg.com/Product/Product.aspx?Item=N82E16814125681&ignorebbr=1) not sure if i can still use the pciex1 slot next to it based on the picture. it looks like fan is relatively thin

---

### Post by Yellow Pasque on 2015-06-01
What are you looking for the graphics card to do? Better 3D? Video acceleration? The GT730 should work well for video playback, but it's still a low-end card like your current HD3450. Yeah, it does have some updated 3D features, like OpenGL 4.x, but if you want to run apps/games that need OpenGL 4.x, chances are that a GT730 wouldn't be much of an "upgrade" over the 3450.

The 3450 may be able to give you video acceleration with recent enough kernel (the 3.19 kernel found in Ubuntu 15.04 should work).
```
sudo apt-get install mesa-vdpau-drivers vdpauinfo
vdpauinfo
```

---

### Post by mamamia88 on 2015-06-02
> **Temüjin said:**
> What are you looking for the graphics card to do? Better 3D? Video acceleration? The GT730 should work well for video playback, but it's still a low-end card like your current HD3450. Yeah, it does have some updated 3D features, like OpenGL 4.x, but if you want to run apps/games that need OpenGL 4.x, chances are that a GT730 wouldn't be much of an "upgrade" over the 3450.

The 3450 may be able to give you video acceleration with recent enough kernel (the 3.19 kernel found in Ubuntu 15.04 should work).
```
sudo apt-get install mesa-vdpau-drivers vdpauinfo
vdpauinfo
```

I would just like to watch video on my 1920x1080 monitor in vlc without any tearing or "graininess"

---

### Post by Yellow Pasque on 2015-06-03
I'm wondering if you have tried other video players, and also what version of Ubuntu you are running?

---

### Post by gordintoronto on 2015-06-04
That's almost completely a CPU issue. If the 8600 doesn't fix it, I don't think a better video card will help.

Let me also suggest Xubuntu 15.04.

> **mamamia88 said:**
> I would just like to watch video on my 1920x1080 monitor in vlc without any tearing or "graininess"

---

### Post by mamamia88 on 2015-06-08
> **gordintoronto said:**
> That's almost completely a CPU issue. If the 8600 doesn't fix it, I don't think a better video card will help.

Let me also suggest Xubuntu 15.04.

Well the e8600 is running now and still get tearing in vlc. didn't notice any in parole but don't have enough time to test fully now.  i am on xubuntu btw.

---

