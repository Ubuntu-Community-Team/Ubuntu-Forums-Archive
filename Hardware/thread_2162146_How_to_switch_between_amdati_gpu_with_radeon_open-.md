---
title: "How to switch between amd/ati gpu with radeon open-source driver under ubuntu 13.04"
date: 2013-07-13
forum: Hardware
---

### Post by Glebushka777 on 2013-07-13
Hi folks!

I'm happy AMD hardware user as north-korean people are happy of their leader. But straight to business.

My hardware is HP laptop Pavilion dv6 which has so calles switchable graphics. 

So laptop has: 

```
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS880M [Mobility Radeon HD 4225/4250]
02:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Whistler [Radeon HD 6630M/6650M/6750M/7670M/7690M]
```

What I want to do is to use that AMD HD 6600 instead of RS880M.

I know that I can use AMD legacy drivers until Ubuntu 12.04.1, but they are still very buggy and they don't give good overall performance including watching videos.

What I have done so far - is that I installed edgers ppa from:  [HTML]https://launchpad.net/~xorg-edgers/+archive/ppa[/HTML].
That edgers ppa provided me with mesa 9.2 and also I can use R600_DEBUG=sb enivornment which also gives good boost.

But I still don't know how to switch between these two gpu if it is even possible right now.

Anybody have any clue how to solve this?

---

### Post by TheFu on 2013-07-13
I would expect ATI to have a control center app that let you control it. Are those GPUs part of different driver software?  My laptop has Intel graphics on-board - used when on battery - and a "discrete" ATI GPU when plugged in. When I boot up while plugged into power, the ATI GPU is used and I think it remains used until the next reboot.  It is easier to see because either intel or ATI drivers are loaded for the system.

Worst case, you'd need to edit the /etc/X11/xorg.conf file manually and the drivers in /etc/modprobe.conf to enable the specific GPU and disable the other as you liked. I think a restart of X/Windows will be needed and an OS restart might be necessary depending on how crappy the ATI drivers used are.

BTW, I don't have any issues playing back any videos with either graphics - VLC or mplayer just work.

Sorry that I'm not really helping. Hopefully, someone who KNOWS will post.

---

### Post by Yellow Pasque on 2013-07-13
> I would expect ATI to have a control center app that let you control it
Sadly, no. Only the proprietary driver has Catalyst control center (ccc).

Google vgaswitcheroo,. Here's a basic page: [https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

---

### Post by TheFu on 2013-07-13
> **Temüjin said:**
> Sadly, no. Only the proprietary driver has Catalyst control center (ccc).

Google vgaswitcheroo,. Here's a basic page: [https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

**Catalyst** is what I meant.  I've run it on my E350, so I know it is/was available in the last 8 months. It was installed through the Ubuntu proprietary drivers repo.  OTOH, I don't use non-LTS releases, so I have no idea what is available for 13.xx.

---

### Post by Yellow Pasque on 2013-07-13
> Catalyst is what I meant.
That's not going to work on an RS880.

---

### Post by Glebushka777 on 2013-07-16
> **Temüjin said:**
> Sadly, no. Only the proprietary driver has Catalyst control center (ccc).

Google vgaswitcheroo,. Here's a basic page: [https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

Do you know anything step-by-step instructions as my knowledge about Ubuntu/Linux is not so great?

Here is what I did and what happened:

I did

```
grep -i switcheroo /boot/config-*
```

I got

```
/boot/config-3.8.0-27-generic:CONFIG_VGA_SWITCHEROO=y

```

I did

```

sudo ls -l /sys/kernel/debug/vgaswitcheroo/switch
```

I got

```
-rw-r--r-- 1 root root 0 heinä 16 09:37 /sys/kernel/debug/vgaswitcheroo/switch
```

I also did

```
gksudo gedit /etc/default/grub
```

and **added**

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **modeset=1 hybridopts=ON,IGD,OFF**"
```

Then

```
sudo update-grub
```

Well that hybridopts come for using "integrated graphics", 'cos after few tries I could not switch to discrete so I leaved config for integrated gpu.

Well from command

```
sudo cat /sys/kernel/debug/vgaswitcheroo/switch
```

I get

```
0:IGD:+:Pwr:0000:01:05.0
1:DIS: :Pwr:0000:02:00.0
```

So even I do different kinds echo commands they either don't work or just freeze the system.

After 

```
sudo -s
```

I can give commands without getting "Permission Denied". But what is right place to use this commands? I think outside X? When I did them in virtualterminal (ctrl+alt+F1-F6) I got message that "integrated gpu refused to switch" So after all tries I'm still on very begining with this. Any help?

In that basic page there was also script and instruction to put in after exit 0 on /etc/init.d/rc.local file. But that "exit 0 didn't exist.
```
chown USERNAME /sys/kernel/debug/vgaswitcheroo/switch
```

Well I still did rest of the script in hope something would help, but no.

Thank you anyway for that link.
Maybe the fastest way to solve graphical problems is not to buy AMD products at all. I think that is not even difficult decission as Intel processors are better and Nvidia cards have better drivers and better support for old cards too.

---

### Post by 00b00nt00 on 2013-07-16
> **Glebushka777 said:**
> Maybe the fastest way to solve graphical problems is not to buy AMD products at all. I think that is not even difficult decission as Intel processors are better and Nvidia cards have better drivers and better support for old cards too.

I really feel your pain. I, too, have an AMD system.

The hardware really isn't all that bad, but the whole "offload the donkey work to the GPU" philosophy is only as good as the driver implementation.

And, frankly speaking, AMD drivers on Linux are a steaming pile of Bulldozer.

---

### Post by Glebushka777 on 2013-07-16
> **00b00nt00 said:**
> I really feel your pain. I, too, have an AMD system.

The hardware really isn't all that bad, but the whole "offload the donkey work to the GPU" philosophy is only as good as the driver implementation.

And, frankly speaking, AMD drivers on Linux are a steaming pile of Bulldozer.

I agree with that.

I would also add to my previus posts that I think I got changed to another gpu. After giving command:
```
echo "DDIS" > /sys/kernel/debug/vgaswitcheroo/switch
``` 
Then to get this "better" gpu to work I need restart X. So when I logout there is **black screen and that's it**. Nothing works and only solution is to shutdown laptop by pressing and holding power-button down. So even If I can change gpu I actually can't. I just don't get it why AMD support for it's open-source driver is that bad. Maybe they just think that linux users are just below 2 % of all operation system users so they does not need to care so much of us...

---

### Post by Yellow Pasque on 2013-07-16
> Maybe they just think that linux users are just below 2 % of all operation system users so they does not need to care so much of us... 
AMD has made large strides lately with their open-source driver, but hybrid graphics are a sore spot on Linux no matter which GPU vendor it is.

---

### Post by Glebushka777 on 2013-07-16
> **Temüjin said:**
> AMD has made large strides lately with their open-source driver, but hybrid graphics are a sore spot on Linux no matter which GPU vendor it is.

And for that reason I just installed Ubuntu 13.10 with mainline kernel.
```
uname -a
3.11.0-031100rc1-generic #201307141935 SMP Sun Jul 14 23:36:57 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

Without forgetting latest xorg-edgers for Saucy Salamander.

I will see how things change, once I download benchmark software.

---

