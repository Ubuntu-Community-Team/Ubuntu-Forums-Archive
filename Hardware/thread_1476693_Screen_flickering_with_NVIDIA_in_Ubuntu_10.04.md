---
title: "Screen flickering with NVIDIA in Ubuntu 10.04"
date: 2010-05-08
forum: Hardware
---

### Post by ddreamer on 2010-05-08
On my previous installation of Ubuntu 9.04 using "NVIDIA-Linux-x86_64-185.18.36-pkg2.run" downloaded from official website of NVIDIA, everything worked fine. I ran Ubuntu with Gnome desktop on a Laptop (ASUS M51SN) equipped with GeForce 9500M GS card.

        After installation of Ubuntu 10.04 Lucid Lynx, I have tried [COLOR=Red]NVIDIA 173 driver[/COLOR] as well as "[COLOR=Red]current[/COLOR]" driver (after installation, I know it was 195.16.15). I also tried "[COLOR=Red]NVIDIA-Linux-x86_64-195.36.24-pkg2.run[/COLOR]" downloaded from official site. The three drivers all make my screen flickering, though not very obvious but still perceivable. If flickering is defined as consisting of bright period and dark period, then the dark period only lasted a fraction of a second. The frequency is quite variable, sometimes you just don't perceive any flickering but in another moment, it flickered at least 5 times a second. The flickering is most evident in all-white background.

         I even doubted if the screen itself or the video card or my eyes went wrong. The former two could be excluded by normal appearance when booting up into Ubuntu 9.04 or FailSafe Mode of Ubuntu 10.04. The last one could be excluded by the same perception of my family member who doesn't use my Ubuntu computer regularly.

Do you guys face similar or the same problem?

I googled and found an article similar, where PowerMizer is damned for changing performance level and caused screen flickering. However, I didn't find any performance level change in "nvidia-settings" program. When the performance level was forced at the maximum, it still flickered. Therefore, PowerMizer seemed unlikely to be the problem in my case. The frequency and severity of flickering aren't associated with any application use. In other words, I haven't found a way to promote or suppress the flickering. It just happened randomly as I could perceive. I use Compiz but when I turned it off by System/Preferences/Appearance/Visual Effect/None. It persisted in flickering... ...

---

### Post by dino99 on 2010-05-08
add this ppa to your sources.list (synaptic - repo tab):

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

read how to do on this page, then update and upgrade

---

### Post by ddreamer on 2010-05-10
Thanks a lot. The flickering improved somewhat but it still existed. Such a bug is really difficult to describe and find solutions for.

---

### Post by kenweill on 2010-05-10
As of now, dowloading and installing nvidia driver from the nvidia's website is not recommended.

> 
Incompatibility with nVidia upstream driver installer

Ubuntu 10.04 LTS includes improved integration for nVidia binary driver packages. Unfortunately, this comes at the expense of compatibility with the installer provided upstream on the nVidia website. Users who wish to use the nVidia binary video drivers with 10.04 LTS should install them using the Ubuntu packages, as made available under System -> Administration -> Hardware Drivers. 


From: [http://www.ubuntu.com/getubuntu/releasenotes/1004](http://www.ubuntu.com/getubuntu/releasenotes/1004)

Try disabling the proprietary driver, going back to nouveau, if it flickers with it.

---

### Post by gleu on 2010-05-14
I have the same issues here with a quadro fx 1700. The problem is related to the powersave function of the nvidia driver. Every time when the clock frequency of the device changes, the screen flickers.

Setting powermizer in nvidia-setting to "Prefer Maximum Performance" worked to disable flickering. According to [1] power saving can be disabled permanent by adding ... **edit** did not work ....


I suppose it is a X problem and not the problem of the driver.

gruss,
georg


[1] [http://www.nvnews.net/vbulletin/showthread.php?t=113105]("http://www.nvnews.net/vbulletin/showthread.php?t=113105")

---

### Post by wecucho on 2010-06-04
i have the same problem, anyone find a solution for this ?

---

### Post by witeshark17 on 2010-06-05
It's not just nvidia:

A [ Launchpad thread](https://bugs.launchpad.net/ubuntu/+bug/587935)

---

### Post by metjay on 2010-06-07
> **gleu said:**
> I have the same issues here with a quadro fx 1700. The problem is related to the powersave function of the nvidia driver. Every time when the clock frequency of the device changes, the screen flickers.

Setting powermizer in **nvidia-settings** to "Prefer Maximum Performance" worked to disable flickering. 


I've the quadro fx 1700 as well and this worked for me, thx. 
Anybody to make this permanent?

---

### Post by RationalGaze on 2010-06-21
Also had this problem, on a Toshiba A200 laptop with nvidia 7300go. Dino99's solution worked (after reboot).

---

### Post by phr0ze on 2010-06-21
> **dino99 said:**
> add this ppa to your sources.list (synaptic - repo tab):

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

read how to do on this page, then update and upgrade

Would this help with my Radeon speed problems too?

---

### Post by nexus9k on 2010-06-30
I've noticed this flickering only in the past week.  Perhaps it might be due to the following 6/24 upgrades:

```
[UPGRADE] xserver-common 2:1.7.6-2ubuntu7.1 -> 2:1.7.6-2ubuntu7.2
[UPGRADE] xserver-xorg-core 2:1.7.6-2ubuntu7.1 -> 2:1.7.6-2ubuntu7.2
```

---

### Post by UltraZone on 2010-07-07
This is a fairly long-running topic.  

Follow these instructions to the tee and you will be golden:

[http://ubuntuforums.org/showthread.php?t=828369&highlight=powermizer](http://ubuntuforums.org/showthread.php?t=828369&highlight=powermizer)

---

### Post by calebrey on 2010-07-07
Here is something odd, my nvidia driver works, and compiz works, but when rotating or doing compiz effects you can notice it flickers like a lin e in the middle, now if I just start nvidia settings and then quit it without changing anything, and reloading windows manager compiz, then it displays better, not more flickering, but when I restart the system it goes back the way it was and I have to do everything again.  If someone could have any idea why is this happening please be my guest, before ubuntu 10.04 on Karmic, compiz and nvidia worked perfectly..  Thanks

---

### Post by Michaelsheldon on 2010-08-15
Hi all. I had the same flickering problem on my acer 7730z running an nvidia card. It was getting really bad with the screen flickering so much it turned white at times.

I tried this solution

[http://jimmod.com/blog/2010/06/solving-fixing-ubuntu-10-04-lucid-screen-flickerdistortion/](http://jimmod.com/blog/2010/06/solving-fixing-ubuntu-10-04-lucid-screen-flickerdistortion/)

So far (4 days at the time of writing) my screen has not flickered once.

Hope this is of some use. Its the best I have tried so far.

---

### Post by mydoom5 on 2010-08-29
> **Michaelsheldon said:**
> Hi all. I had the same flickering problem on my acer 7730z running an nvidia card. It was getting really bad with the screen flickering so much it turned white at times.

I tried this solution

[http://jimmod.com/blog/2010/06/solving-fixing-ubuntu-10-04-lucid-screen-flickerdistortion/](http://jimmod.com/blog/2010/06/solving-fixing-ubuntu-10-04-lucid-screen-flickerdistortion/)

So far (4 days at the time of writing) my screen has not flickered once.

Hope this is of some use. Its the best I have tried so far.

Didn't work for me. I still have this issue.
I just wonder how come this hasn't been solved yet, since there are reports of this problem from two or more years ago.

---

### Post by ahrar25 on 2012-09-14
i am using Dell optiplex 740 with Nvidia 6150... my graphics drivers are already installed automatically... and there are even no updates for my drivers... so i am pretty sure that G.Driver is perfectly installed.. and still when i drag some thing and do any other thing my screen flickers... and its perfect in my WIN7... so no problem with my moniter and graphics... any clues?

---

