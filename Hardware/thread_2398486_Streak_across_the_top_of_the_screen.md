---
title: "Streak across the top of the screen"
date: 2018-08-13
forum: Hardware
---

### Post by meiselstein on 2018-08-13
Hello everyone,

I am a long time Apple guy, but my wife stole my Macbook. So, I bought a cheap laptop (Asus X407MA) that I could just leave at the office. After using Windows 10 for a few minutes, I was quickly reminded that I absolutely hate the OS (they STILL have not fixed the battery compliance driver problem...unreal). So, I downloaded and tried both CloudReady and Ubuntu. I decided to stick with Ubuntu because of the support and features.

Everything is great except for one tiny problem: whenever the laptop begins to "process" something, a streak will go across the top of the screen. Sometimes it's white and sometimes it's different colors. I'm linking two pictures to show you. It does not do this in Windows 10, but it does it with CloudReady. 

Any idea how I can fix this? It's not a huge deal to me, but it is distracting when I am doing work. 

Thanks in advance for any help that you can provide.

[https://imgur.com/wNybW73](https://imgur.com/wNybW73)

[URL="https://imgur.com/TkiI7qT"]https://imgur.com/TkiI7qT
[/URL]
Edit: I switched to Firefox and I noticed that the streaks happen a lot less. I wonder if it has something to do with processing (sorry, not a very computer technical person).

---

### Post by kc1di on 2018-08-13
Hello meiselstein and welcome to Ubuntu,

What we need to know is what video card is in that machine. and which driver is being used.
Please bring up a terminal and copy and past this command and post the output here.```
lspci -vnn | grep VGA -A 12
```

---

### Post by meiselstein on 2018-08-13
> **kc1di said:**
> Hello meiselstein and welcome to Ubuntu,

What we need to know is what video card is in that machine. and which driver is being used.
Please bring up a terminal and copy and past this command and post the output here.```
lspci -vnn | grep VGA -A 12
```

Hello kc1di!

Thanks for the reply. I did as you asked and this is what comes up:

00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:3185] (rev 03) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device [1043:1ee0]
    Flags: bus master, fast devsel, latency 0, IRQ 123
    Memory at 81000000 (64-bit, non-prefetchable) [size=16M]
    Memory at 90000000 (64-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=64]
    [virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:0e.0 Audio device [0403]: Intel Corporation Device [8086:3198] (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1ee0]

---

### Post by meiselstein on 2018-08-13
Just wanted to add that I am currently trying a live version of Debian Xfce and the streaks are not occurring.

---

### Post by Autodave on 2018-08-13
I googled that machine and found out that it *could *have up to 8 gig RAM.  It could have a LOT less.

Understand that Ubuntu and Xubuntu have the same kernel: the same operating system. The ONLY difference is the look of the desktop and what programs are pre-installed.  Since Xubuntu seems to be working OK form the boot device, why not try installing it?

Ubuntu is a quite heavy (memory usage) desktop. You will probably find that Xubuntu will run a little faster.

---

### Post by meiselstein on 2018-08-13
> **Autodave said:**
> I googled that machine and found out that it *could *have up to 8 gig RAM.  It could have a LOT less.

Understand that Ubuntu and Xubuntu have the same kernel: the same operating system. The ONLY difference is the look of the desktop and what programs are pre-installed.  Since Xubuntu seems to be working OK form the boot device, why not try installing it?

Ubuntu is a quite heavy (memory usage) desktop. You will probably find that Xubuntu will run a little faster.

Thanks for the help Autodave. 

My laptop has 4GB of memory. I was trying a live version of Debian, which worked fine. However, when I installed it, it would only let me have a display of 800x600. Google searches to fix it showed that I have no idea how to use Debian (I heard that it was for advanced users). So, I reinstalled Ubuntu. 

Do you think it's a memory issue? I thought 4GB was enough.

---

### Post by kc1di on 2018-08-13
4 GB should be plenty.  But xfce may be a better choice so I would try xubuntu if gnome is not working well for you.
I know there were some problems with kernel 4.15.x with some intel cards but it's working fine on my xubuntu install. 

Intel graphics have been pretty good for a while so not sure what's causing the problems on your machine.  Maybe someone who has one similar might chime in. 
good luck.

---

### Post by meiselstein on 2018-08-13
> **kc1di said:**
> 4 GB should be plenty.  But xfce may be a better choice so I would try xubuntu if gnome is not working well for you.
I know there were some problems with kernel 4.15.x with some intel cards but it's working fine on my xubuntu install. 

Intel graphics have been pretty good for a while so not sure what's causing the problems on your machine.  Maybe someone who has one similar might chime in. 
good luck.

Thank you, kc1di. I will try a live version and report back here.

---

### Post by meiselstein on 2018-08-13
> **meiselstein said:**
> Thank you, kc1di. I will try a live version and report back here.

Thank you for the recommendation, kc1di. I tried Xubuntu and everything worked out. So, I installed it and everything is working really well. I love the fact that I can enjoy a distro that is heavily supported and not have to worry about the graphics problems.

---

### Post by kc1di on 2018-08-14
Glad it worked out for you, Enjoy :)

---

### Post by meiselstein on 2018-08-19
Hi everyone,

So, I wanted to give an update because I actually solved the screen flickering problem.

While I was enjoying Xubuntu, it bothered me that I did not try to fix Ubuntu. So, I did some research and found that Autodave was on to something about the memory. I found some videos and learned about swappiness and how the default Ubuntu levels are pretty low. The following video helped me fix the swappiness levels and now I have not had one screen flicker. 

The YouTube video can be found here: [https://youtu.be/BLVtxpm5c2A?t=11m1s]("http://youtu.be/BLVtxpm5c2A?t=11m1s")

---

