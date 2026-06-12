---
title: "Ubuntu issues with wirelss and heat temperature"
date: 2010-03-23
forum: Hardware
---

### Post by c00lwaterz on 2010-03-23
Ubuntu is great and I love everything about ubuntu. Comparing ubuntu with windows. All I can say is ubuntu runs faster, simpler, and stable but I have this problem. If can somebody help me with wireless and heat issues. I have searched already many forums, and in google but sadly I can't find any answer. I use my laptop most of the time with windows because of wireless issues and heat issues.

Im using toshiba m900 core 2 duo 2.2ghz with 3gb memory. my Network card is realtek and also the wireless is realtek which I've seen in my windows hardware details. If this issue is solve, then I would love to use my ubuntu as most of the time. I'm afraid my laptop would fry up and burn. When I use ubuntu, the heat in keypad near the palm is really hot. I don't know how high is the temperature but, my hands can't stand it. I tried using fan and cooling pad but no luck and it's like a hot blower.

The wireless setup in ubuntu cannot detect my access point that I don't know if my wireless card is the issue or my access point. I'm using DLink 1150 model. I don't see any networks in the menu. if ubuntu can help me with this problem, then its a big big thanks because I really love ubuntu.

Any tips and help would be appreciated.

Thanks in Advance:popcorn:

---

### Post by Chronon on 2010-03-24
For heat, you might try the frequency scaling applet: 
[http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html](http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html)

I don't have any particular experience with your wireless card.  I didn't find it listed on this page: 
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink)

It might be worth installing compat-wireless drivers.  Try here first:
[http://linuxwireless.org/en/users/Download#Getting_compat-wireless_on_Ubuntu](http://linuxwireless.org/en/users/Download#Getting_compat-wireless_on_Ubuntu)

---

### Post by c00lwaterz on 2010-03-24
I have tried the link for cpu frequency you have given but it did not work.

I'm now trying the compat-wireless you refer.

hoping to solve this issues. 

thanks

---

### Post by c00lwaterz on 2010-03-24
I have tried the compat-wireless but now I can't enter the ubuntu system. I mean, when i restart my laptop then choose ubuntu then it doesn't start on ubuntu. It was in the black with command line and nothing else to choose. if I would remember it's like grub: i forgot. but it did not come to the loading of ubuntu.

---

### Post by Chronon on 2010-03-24
What options do you get at the grub menu?  You can try recovery mode if you're unable to boot a normal session.

What did you do to install the compat-wireless drivers?

---

### Post by c00lwaterz on 2010-03-24
i don't see any option. so now i just uninstall it. Hoping someday the issues will be solve. because I love to use ubuntu than windows. ubuntu is easy to use than other linux distro. ubuntu is faster to load than windows.my loading will only take 20 seconds to 30 seconds on ubuntu. in windows vista it takes 1 minute and 40 seconds then sometimes 2 minutes.

Even i have use compiz fusion in ubuntu, it still faster than windows. so for now maybe I will cool off to ubuntu. I will wait for lucid. =) btw, thanks for the help. this is the only post i got reply. my previous posts are hopeless.

Can I add you to my buddy list?

---

### Post by Chronon on 2010-03-24
It's strange.  I wouldn't expect installing different wireless module to prevent booting (though you didn't describe very clearly what was happening). There are other things you can try, like windows drivers with ndiswrapper.  

However, I can totally understand if you prefer to wait until Lucid is released.  It will/does have improved wireless support in the kernel (compared with vanilla karmic).

(Sorry, I don't really collect friends on here.)

---

### Post by c00lwaterz on 2010-03-24
I have tried the ndiswrapper. But I failed to make it work. anywayz, tnx tnx for the replies hehe. I have post new thread "Ubuntu 10.04 for Toshiba Machines". so I can get many reviews and comments. If that will help me. 

Thanks

---

### Post by c00lwaterz on 2010-04-03
I have tried debian 5.04 on my toshiba m900 core 2 duo 2.2ghz with 3gb memory ram, ati radeon 4500 video card. It still get high temperature. I run Live cd (debian 5.04) then boot then exploring the menus and i did not update any. I did not do anything. then after 3 to 4 minutes it became really hot and the fan really sounds. I don't know why my laptop becomes overheat when using linux. I also use ubuntu 9.1, freebsd 8, linuxmint8, eArOS, and other linux distros but same experience. really hot.

Any help and tips will be appreciated so much.

Thanks

---

### Post by Lucid Lynx on 2010-04-03
You might take your laptop to a service and request a dust-cleaning inside. I had a similar problem with my laptop (Toshiba Satellite A 110-153) a year after I bought it (it was becoming very hot running Windows or Ubuntu, with/without wireles working). A dust-cleaning inside solved the problem, and I am doing that once a year, and it`s working just fine, no heat problem anymore.

---

### Post by c00lwaterz on 2010-04-03
My laptop is new out of the box laptop and in windows no overheat. I just wonder why in linux why it becomes overheat =(

---

### Post by dE_logics on 2010-04-03
> **c00lwaterz said:**
> My laptop is new out of the box laptop and in windows no overheat. I just wonder why in linux why it becomes overheat =(

You are most probably using the 64 bit version of ubuntu, 64 bit OSs is claimed to have generated  more heat but faster.

Another thing can be that you're using the wrong graphs drivers and so the CPU usage of xorg is high.

Open up gnome-system-monitor in system>administration>system monitor.

In the (I think) second tab, tell us what's the CPU usage.

If it's high, you need to determine what process is causing the problem...it's most probably X if you're having an ATI graphics chip.

---

### Post by c00lwaterz on 2010-04-03
I use 32bit only. I also try fresh install without graphics card driver or what-so-ever updates. also try to use live cd ( Not yet install) then I just wait for 2 minutes then start to get high temperature until my fingers cannot stand the heat. =(

I have tried debian 5.04, freebsd 8, ubuntu 9.1, linuxmint 8, and some other linux distro.

same experience with heat. =(

---

### Post by girishadat on 2010-04-03
You can check with the temperature monitoring applet for gnome to see which part (cpu/gpu/hdd/??) is getting overheated. I think for 9.10, it will not come by default with the installation.

Can you try getting the latest drivers for your graphics controller under Ubuntu? I had similar problem for my good old Acer 4520 laptop, with an nVidia 7000m/610m graphics. There were options for nVidia to automatically control the GPU speed so that any heat produced by it can be reduced. I can see that you are a big fan of compiz fusion. Try to use lesser graphic options and check if that helps.

I am so worried with your posts, because I just ordered my Portege M900 D3212 yesterday, and I cannot stop using Ubuntu though it comes with a pre-installed Windows 7. :(

---

### Post by c00lwaterz on 2010-04-04
i have tried to update the driver of video card driver also before but same high temp. even I try fresh install without anything install such as compiz, it still getting hot.

I did try to load in in live cd then wait for 2 to 3 minutes but it is getting hot also. my graphics card is ati radeon 4500. in the ubuntu the graphics of ati don't have setting. i just isaw proprietary hardware driver then i just see ati radeon (nothing else).

eve I don't install graphics driver, it is still hot. I have read that it has something to do with kernel. I dont know much but I am hoping the solution is 10.04.

In windows vista i get 55 degrees celcius up to 75 degrees celcius. the normal stand by is 60 degrees celcius(windows vista). In linux, it is really high and I my fingers cannot stand already. 

my laptop almost burn when i try to wait for 10 minutes while searching in firefox (searching for high temp issues to be fix and wireless issue).

I also use debian 5.04, linuxmint 8 , freebsd 8, etc. but same. Maybe not yet supported in linux (my laptop).

I have tried 15 to 20 times (install and uninstall the linux) to fix linux and laptop.

but when using windows, the toshiba m900 is really good. really fast. no hang and no slow and really smooth in windows.

when using linux it is faster and faster to boot but really hot

---

