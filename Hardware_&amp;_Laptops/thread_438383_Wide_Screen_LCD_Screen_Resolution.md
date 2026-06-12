---
title: "Wide Screen LCD Screen Resolution"
date: 2007-05-09
forum: Hardware &amp; Laptops
---

### Post by Mattness on 2007-05-09
Hi, I'm a fairly new user to linux and Ubuntu.  I have a question about wide screen resolution and linux.  I'm finally getting ready to upgrade my old trusty 17" Sony Multiscan CRT and I was wondering if anyone is having trouble getting some of the wide screen resolutions to work in linux (ie 1680X1050, 1440X900, 1920X1200 and the like.)  I currently have an ATI 9600 Pro video card and I'm running Feisty as well.  I'm still not sure if I want a wide screen LCD but it would sure be nice to know if I'm going to run into any problems if I get one.  Thnaks in advance for any info.

Matt

---

### Post by taurus on 2007-05-09
Don't have any problem running 1680x1050 on my machine except I am using nVidia graphic card.  I don't think you would have problem either even though you are using ATI.

---

### Post by redsupra101 on 2007-05-09
Nice to walk in and see this thread!

I'm a new user to Ubuntu and I've _just_ (like literally 30 minutes ago)installed Feisty Fawn on my laptop!

Everythign is working fine, wireless drivers etc are all functioning perfectly, but I can't use my widescreen resolutions so I'm stuck with 3:4 resolutions when I should be runnign at 3:5 or 9:16 even! Imagine how screwed up my wallpaper looks (I'm into the fancy car wallpaper stuff *smirk*)

I don't have (or know how to get to) the option to change the aspect ratio to be used. I'd really like to go back to a 1280x768 resolution (same as i use on Windows on the same laptop) so if anyone can throw a word  by me, it'd be sweet!!

---

### Post by taurus on 2007-05-09
You probably just have to install a driver for your graphic card?  What is your graphic card anyway?

Applications -> Accessories -> Terminal
```
lspci
```

---

### Post by misfitpierce on 2007-05-09
1280X768 here and not a prob

---

### Post by Medieval_Creations on 2007-05-09
I have a 19" LCD and got the 1440x900 working no problem after installing and configureing the newest video drivers for a nVidia 6200.

---

### Post by Mattness on 2007-05-09
I sure appreciate the quick response to this thread.  It sounds like I should be able to have a monitor with just about any resolution and it should work.  Even if it doesn't I can always rely on someone in here to help me out.  Thanks

Matt

---

### Post by redsupra101 on 2007-05-09
> **taurus said:**
> You probably just have to install a driver for your graphic card?  What is your graphic card anyway?

Applications -> Accessories -> Terminal
```
lspci
```

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)


That's what I see for the graphics controller. Any idea where I could get the proper "fully Ubuntu compatible" drivers for this card? Its an HP dv1000 notebook I got.

---

### Post by MajinCline on 2007-05-09
This is an interesting topic for me. I put together a cheap (but fast for the price) computer for my brother. He has an onboard nvidia geforce 6100. After installing Ubuntu I had serious issues getting it up higher than 1024x768 which is a bit surprising being an relatively common graphics card with. After modifying the xorg.conf to the correct resolution, 1440x900, the video had a strange horizontal line pattern where the correct log on screen is displayed but seriously distorted. After trying everything (including windows.....ugh :( ), nothing would   work so I (and I don't know why) tried updating the bios. Everything worked after that and quite well so I have no complaints except for the fact that nobody had any documentation of the issue or any updates so it took a long time to fix. I figure since we're on the topic of larger resolutions (especially widescreen) I'll point out that it doesn't hurt to update the bios.

---

### Post by Bluecircle on 2007-05-09
> **redsupra101 said:**
> 00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)


That's what I see for the graphics controller. Any idea where I could get the proper "fully Ubuntu compatible" drivers for this card? Its an HP dv1000 notebook I got.

Try reconfiguring X

```

dpkg-reconfigure xserver-xorg

```

If the i810 driver doesn't work, select the "intel" driver instead of the one you are using now. If the intel driver is not listed, go to Synaptic Package Manager and install "xserver-xorg-video-intel".

This worked for me, I'm on a Sony Vaio Laptop with the Intel 915GM chipset, with a 1366x768 resolution.

---

### Post by redsupra101 on 2007-05-09
> **Bluecircle said:**
> Try reconfiguring X

```

dpkg-reconfigure xserver-xorg

```

If the i810 driver doesn't work, select the "intel" driver instead of the one you are using now. If the intel driver is not listed, go to Synaptic Package Manager and install "xserver-xorg-video-intel".

This worked for me, I'm on a Sony Vaio Laptop with the Intel 915GM chipset, with a 1366x768 resolution.

remember i am a complete ubunto n00b so out of everything you said i heard... :confused: :confused: 

i can at least get to the terminal though! in the terminal when i type what you put there for me, 


```

dpkg-reconfigure xserver-xorg

```

it tells me "dpkg-reconfigure must be run as root"

---

### Post by WNDS1701 on 2007-05-09
Hey guys, 

this seems to be the right thread to ask for my problem, too.

I have a widescreen on my laptop (1280x800), but sometimes it flashes in some area for a quick moment and then everything is OK. Does someone else experience the same problem?

Thanks in advance!

---

### Post by Shinoda on 2007-05-09
> **redsupra101 said:**
> it tells me "dpkg-reconfigure must be run as root"Bluecircle meant```
sudo dpkg-reconfigure xserver-xorg
```Then enter your password as prompted.

---

### Post by redsupra101 on 2007-05-09
> **Shinoda said:**
> He meant```
sudo dpkg-reconfigure xserver-xorg
```Then enter your password as prompted.

I dont get prompted for a password...

after it says /usr/sbin/dpkg-reconfigure must be run as root, it goes to the next line for text input with the user@Ubuntu:~$ prompt.

---

### Post by Shinoda on 2007-05-09
I mean you must use```
sudo dpkg-reconfigure xserver-xorg
```instead of```
dpkg-reconfigure xserver-xorg
```

---

### Post by redsupra101 on 2007-05-09
> **Shinoda said:**
> I mean you must use```
sudo dpkg-reconfigure xserver-xorg
```instead of```
dpkg-reconfigure xserver-xorg
```

Cool.. thanks.. did that.. probably screwed it up cus now i cant boot into the GUI and gotta 'fix' it via CLI which i know nothing of...


Soo... I booted back into Windows and I''m going to start over with this install... Partition deleted formatted now. Sigh.

---

### Post by Syke on 2007-05-10
redsupra101,

When you get a running system again, here's something to try to get the right resolution.

Background: Try installing this tool called 915resolution. It is used to tweak the resolution. Further details at [this site]("http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html").

Here's the short version. Open a terminal and type these lines, one by one (and enter your password when it prompts).

```

wget http://www.geocities.com/lostlinkpr/ubuntu/auto915Resolution.tar.gz
tar xvf auto915Resolution.tar.gz
sudo -i
cd /home/user/auto915Resolution
./auto915resolution.sh

```

Follow the prompts and pick the right resolution, and answer yes to "create the startup script?". Then restart your system.

---

