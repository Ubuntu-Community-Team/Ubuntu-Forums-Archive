---
title: "AMD unsupported hardware on ATI HD 6470M"
date: 2011-03-04
forum: Hardware
---

### Post by ellrywych on 2011-03-04
I install ubuntu 10.10 i386 on my computer with intel core i5 and ATI HD 6470M.
Then I found there's no drivers for 6470 card on ATI's support sites,and I install ATI/AMD driver FGLRX.
Everything shows ok only there is a watermark on right corner of "AMD unsupported hardware".
I have google it and have viewed some topics in forum which has the same problem with me, and I tried with what they said but failed.
I'm new to ubuntu and linux ,any help will be apprecriate.

---

### Post by puller on 2011-03-04
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)

You can get it if from this page [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx) you chose:

step1: notebook graphics
step2: radeon hd series
step3: radeon hd 6xxxm series
step4: linux x86 (or x86_64, you should know it)

---

### Post by king EZi on 2011-03-08
> **puller said:**
> [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)

You can get it if from this page [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx) you chose:

step1: notebook graphics
step2: radeon hd series
step3: radeon hd 6xxxm series
step4: linux x86 (or x86_64, you should know it)

Hey i have an ATI HD 6470M on Kubuntu 10.10 i installed this driver but it didnt work then later i installed the one provided in the link and ended up with the "AMD unsupported hardware" watermark, how do i get rid of it?

---

### Post by ak47suk1 on 2011-03-12
Same here [king EZi]("http://ubuntuforums.org/member.php?u=568927"). Already tried both watermark.sh and /etc/ati/{control,signature} trick.

---

### Post by Yellow Pasque on 2011-03-12
Hopefully, Catalyst 11-3 will resolve the watermark..

---

### Post by king EZi on 2011-03-17
> **ak47suk1 said:**
> Same here [king EZi]("http://ubuntuforums.org/member.php?u=568927"). Already tried both watermark.sh and /etc/ati/{control,signature} trick.

So do you still have the watermark??? :(

---

### Post by king EZi on 2011-03-17
> **Temüjin said:**
> Hopefully, Catalyst 11-3 will resolve the watermark..

Does anyone know when Catalyst 11-3 will be released?? And is it confirmed that radeon HD 6470M will be supported??

---

### Post by ak47suk1 on 2011-03-18
> **king EZi said:**
> So do you still have the watermark??? :(

still have the watermark. Hope next Catalyst driver release fix it.

---

### Post by olsman037 on 2011-03-31
Hi,

I'm interested by the new vostro 3550 with i5 2410M (maybe I will chose the i7 2620...) and AMD Radeon HD 6470... Did the new catalyst driver (11.3 available since the 29th of march) solved your problem ? Can you switch between the intel integrated graphics (embeded in  new generation intel processors) and the AMD graphic card ? I know that there is some problem with nvidia optimus but I don't know how ubuntu manage with AMD radeon + integrated intel graphic...

How ubuntu react in general with these new processors and this graphic card ?

Thanks...

---

### Post by king EZi on 2011-03-31
I downloaded the new Catalyst 11.3 drivers today and installed it on mint 10 and after a reboot, i still had sucky resolution and no composition.
I rad aticonfig and got an error "no adapter detected" error.

Card is still radeon HD 6470M, anyone else facing this problem?

I'll go back to the drivers available on the repos, although im stuck with the watermark. Arrrrgghh!!!!

---

### Post by puller on 2011-04-01
> **olsman037 said:**
> Hi,

I'm interested by the new vostro 3550 with i5 2410M (maybe I will chose the i7 2620...) and AMD Radeon HD 6470... Did the new catalyst driver (11.3 available since the 29th of march) solved your problem ? Can you switch between the intel integrated graphics (embeded in  new generation intel processors) and the AMD graphic card ? I know that there is some problem with nvidia optimus but I don't know how ubuntu manage with AMD radeon + integrated intel graphic...

How ubuntu react in general with these new processors and this graphic card ?

Thanks...

I have a sony VAIO with Intel integrated graphics and ATI HD 6470M. As far as I know, the support for Intel Sandy Bridge graphics is currently provided only with 11.04, and Catalyst drivers didn't work for my HD 6470 with 10.10.

The only solution I had to have a working system has been to install (K)ubuntu 11.04 and use it with the Intel integrated graphic, which is supported, but still has some problems (see how the right-click menu is rendered in the attached picture).

11.04 is shipped with switcheroo kernel module which lets you activate/switchoff the two graphic cards. I have added two lines to my ```
/etc/rc.local
``` file in order to deactivate (switch off) the discrete graphic card at boot (ATI) and use only the integrated one (intel) with which composition works very well (also HD video). I guess you won't need the discrete video card unless you want to play some heavy-duty games, the integrated one works very well and has the power-consumption advantage.

However I am looking forward to have also the ATI card working (i.e., proper catalyst driver support). Currently if I try to activate it, I am not able to activate the x server.

The two lines I added to my /etc/rc.local are:
```
chown puller /sys/kernel/debug/vgaswitcheroo/switch
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
```

Have a look at this two sites:
[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)
[http://asusm51ta-with-linux.blogspot.com/](http://asusm51ta-with-linux.blogspot.com/)

---

### Post by Yellow Pasque on 2011-04-01
vga_switcheroo is only for open-source drivers. AMD just added PowerXpress support for hybrid switching with Catalyst, though I've seen mixed reports on its stability. See: [http://www.phoronix.com/scan.php?page=news_item&px=OTI3Mg](http://www.phoronix.com/scan.php?page=news_item&px=OTI3Mg)

---

### Post by deere on 2011-06-08
Take a look at this solution: [http://askubuntu.com/questions/46976/ati-catalyst-control-center-gives-error-natty-64bit-radeon-hd-6470m](http://askubuntu.com/questions/46976/ati-catalyst-control-center-gives-error-natty-64bit-radeon-hd-6470m)

---

