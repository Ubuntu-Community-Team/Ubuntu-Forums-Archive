---
title: "Black sreen after I install ATI/AMD"
date: 2011-12-07
forum: Hardware
---

### Post by hoang04ct1 on 2011-12-07
Hi!

I install ATI/AMD. Then I restart, black sreen ask me login. I don't know stype commanline in ubuntu 10.10.

I install 11.10 and 10.10. That case is like.

Can you help me?

Thanks!

---

### Post by lukeiamyourfather on 2011-12-07
Did you install the graphics drivers using the utility in Ubuntu or did you download them from the AMD website?

---

### Post by Mark Phelps on 2011-12-08
Unless you are using Ubuntu to play graphics-intensive games, you do not NEED the ATI/AMD drivers in recent Ubuntu versions.

Ubuntu 11.10 has improved the open-source AMD drivers such that now, without the restricted drivers, I can get full resolution (1920x1200) as well as multi-monitor support.

Suggest you refrain from installing the AMD drivers and just use the default open-source drivers -- which are installed automatically for you.

---

### Post by MoreOrLess on 2011-12-08
This frequently happens on hybrid graphics systems. Post output of:
```
lspci | grep -i vga
```

---

### Post by hoang04ct1 on 2011-12-09
Hi Mark Phelps!

I'd like to use compiz but I don't enable desktop effect .So I think I need to install ATI/AMD! 

I used ubuntu 11.10 and ubuntu 10.10 but didn't enable desktop effect. 

[B]Now, my computer asked me login (console). I login OK but I can't go graphic ubuntu. I don't know commandine well.

How can I login in graphic ubuntu as beginning?
[/B] 
Can you help me to how enable compiz?

Thanks!

---

### Post by mastablasta on 2011-12-09
see the post form MoreOrLess. you need to first tell us the graphics card you use (so we can help further) and this command will throw it out.
 
follow these instructions to remove the AMD driver and install the opensource ones back:
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch")
 
check under: Problem: Need to fully remove -fglrx and reinstall -ati from scratch
 
fglrx is ATI/AMD linux driver.

---

### Post by hoang04ct1 on 2011-12-10
I use AMD Radeon HD 6370M.

---

### Post by MoreOrLess on 2011-12-10
> **hoang04ct1 said:**
> I use AMD Radeon HD 6370M.
You could still (and probably do) have two GPU's in a hybrid setup.
**Post lscpi output...**

---

### Post by hoang04ct1 on 2011-12-12
I followed
[https://wiki.ubuntu.com/X/Troublesho...from%20scratch]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch")

but I don't finish

I begin  to try dpkg -l '*fglrx*' and locate fglrx -> OK
then:
sudo apt-get remove --purge xorg-driver-fglrx fglrx* but I receive message: sudo dpkg --configure -a
I did it
then I have message: "configuring ttf-mscorefonis-installer"

I can't OK all other compline, for examples:

sudo apt-get remove --purge xorg-driver-fglrx fglrx*   sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri fglrx-modaliases   sudo dpkg-reconfigure xserver-xorg

Can you help me!

---

