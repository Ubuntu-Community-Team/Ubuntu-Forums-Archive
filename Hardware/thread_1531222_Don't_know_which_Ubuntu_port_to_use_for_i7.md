---
title: "Don't know which Ubuntu port to use for i7"
date: 2010-07-14
forum: Hardware
---

### Post by PandaChan on 2010-07-14
Hello, I know that this isn't the best place to post this, but this place is a mess, any way.. I just got a TOSHIBA with Intel i7 Quad core.. and I was happy until I needed to install Linux I normally use Ubuntu on my computers but this one is 64bits..
SO I went to the download section in the ubuntu web page and I just can see the AMD64 nothing for Intel, in xubuntu they recommend x86for Intel 64 which any one knows that is just untrue.. so Which flavor of ubuntu should i get that gives me the best of my intel i7.? Any help will be highly appreciated.

BTW: English is not my main language, so, sorry about my writing.

---

### Post by howefield on 2010-07-14
> **PandaChan said:**
> SO I went to the download section in the ubuntu web page and I just can see the AMD64

That's the one you need.

---

### Post by PandaChan on 2010-07-14
> **howefield said:**
> That's the one you need.

Ok, Then I will try it tonite and see how it it ends.!! 

Why if its meant for Intel says AMD??

---

### Post by efflandt on 2010-07-14
AMD came out with an x86-64 chip that could also run x86 32-bit code before Intel did, so the AMD64  name stuck for regular 64-bit regardless.  Anything Intel 64-bit specific is likely for Intel Itanium processors (IA-64) that cannot run x86 code.  [http://en.wikipedia.org/wiki/64-bit](http://en.wikipedia.org/wiki/64-bit)

I did not realize that my dual core laptop from 2006 could run 64-bit until I saw it mentioned, and 64-bit Ubuntu worked.  It also works great on my new desktop with Intel i5 cpu.

---

### Post by PandaChan on 2010-07-15
> **efflandt said:**
> AMD came out with an x86-64 chip that could also run x86 32-bit code before Intel did, so the AMD64  name stuck for regular 64-bit regardless.  Anything Intel 64-bit specific is likely for Intel Itanium processors (IA-64) that cannot run x86 code.  [http://en.wikipedia.org/wiki/64-bit](http://en.wikipedia.org/wiki/64-bit)

I did not realize that my dual core laptop from 2006 could run 64-bit until I saw it mentioned, and 64-bit Ubuntu worked.  It also works great on my new desktop with Intel i5 cpu.
Cool, is good toknow, I'm still trying to find some time to install the linux, today seems to be the day.. yesterday worked late. so.. :( I will let you guys know tonite as soon i get my system running .. thanks you all for the answers.

---

### Post by PandaChan on 2010-07-20
Hello Guys, I have tryed Both ubuntu and Xubuntu AMD64, Both CD's boot up, show me the first menu where I select the language English then it shows me the second menu where I select the install option, then after one minute or so, the CD stops reading and the screen is all blac with the cursosr blinking on the upper left corner... it stays there forever.. any Ideas.?

---

### Post by TBABill on 2010-07-20
Does your machine use the Intel HD video chip? If it has an ATI card then you should probably have no issues because of video specifically, but if it uses the integrated Intel chip you may need a distro that uses the 2.6.33 or later kernel. I have the i3 in my laptop and same type issues with Ubuntu and Mint. Tried PCLinuxOS 2010.7 and it uses the 2.6.33 kernel and works fine. 
 
Google your CPU and linux to see if it could be a video driver issue due to kernel version if you suspect that could be the problem. If it is, you can go to [www.distrowatch.com]("http://www.distrowatch.com") and search for distros with the kernel version you may require for your processor and GPU.

---

### Post by PandaChan on 2010-07-20
Hi, No This Laptop cames with a fancy Nvidia card with 1G of Video RAM, Google does not shows any result on this toshiba the CPU is supossed to be very wellsuported since last year even here at ubuntu forums, I tryed a Ubuntu intall CD for 32-bit CPU and runs fine (but didn't install it).

I think it might be something with the AMD64 version of the distro.. I will try the one you mention, and Debian as well.. I will keep you guy informed.

---

### Post by PandaChan on 2010-07-26
> **PandaChan said:**
> Hi, No This Laptop cames with a fancy Nvidia card with 1G of Video RAM, Google does not shows any result on this toshiba the CPU is supossed to be very wellsuported since last year even here at ubuntu forums, I tryed a Ubuntu intall CD for 32-bit CPU and runs fine (but didn't install it).

I think it might be something with the AMD64 version of the distro.. I will try the one you mention, and Debian as well.. I will keep you guy informed.

Hello, Well I finally decide and used Debian.. I have to say I'm really surprised how well it went.. Last time I tried a Debian distro was back in 1998, But last week I tried Lenny and went really smooth and easy.. I got the NViDIA working and the wireless as well.

Now, I'm only struggling with the sound driver.. I got the proper source code and compile it.. it compiles no errors and no warnings... I got the Beep out of the speakers.. no other sound.. I know that this may be something related with modprobe.d file or something.. or may be this is isn't  the right thread to ask about this.. any way.. any help will be highly appreciated.

---

### Post by brokenromeo on 2010-07-26
Which model laptop do you have?

---

### Post by PandaChan on 2010-07-26
> **brokenromeo said:**
> Which model laptop do you have?

Toshiba satellite A505

---

### Post by PandaChan on 2010-07-28
> **PandaChan said:**
> Toshiba satellite A505

Hello Everyone.. I found the right Drivers.. for amd64...
just by google them... 

I download them compile them install them setup the modprobe.d file.

I just notice that some of the interface were mute by default but nothing that ALSA mixer couldn't fix...

Before closing this thread definitively I will like to post the 
name of the drivers and the simple steps to install them..

I'm not in the same place as the computer is I will be in about 4 hours.. so please hold the thread a little bit longer before closing it as solved...

I will like to thank to all the guy

---

