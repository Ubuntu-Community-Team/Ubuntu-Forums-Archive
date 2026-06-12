---
title: "Intel graphics driver not found"
date: 2019-01-04
forum: Hardware
---

### Post by sankarsuresh01 on 2019-01-04
Hey guys..
I have a Lenovo Thinkpad L420... with 3 GB ram, and 2.3 Ghz i5 intel processor...
I installed Ubuntu Linux in my laptop recently.... Everything worked out fine, until i started experiencing some lag.... i checked the graphics memory, and it was just 256MB.. I had 1 GB of graphics memory in my laptop. 

The graphics card in my laptop was "Intel HD Graphics 3000" .... with 1 GB graphics, while i was running windows 8.. but now, when i check the graphics card info, it shows "Intel Sandybridge " which is not my integrated one.... Please help.. How to install drivers of the other HD 4000 Intel graphics card? I'm using Ubuntu 18.04

---

### Post by kc1di on 2019-01-04
Hello sankrasuresh01 and Welcome to Ubuntu Forums,  

Intel drivers are normally now part of the kernel and there should be no need to install them separately.  How ever you may benefit from update version by adding the following ppa and doing and update and upgrade. in a terminal to this:
```
sudo add-apt-repository ppa:oibaf/graphics-drivers
``` Then ```
sudo apt update
``` and then ```
sudo apt upgrade
```
good luck.

---

### Post by sankarsuresh01 on 2019-01-04
Dude, 
I tried it, but no luck....

The same motherboard graphics i think, is getting updated... the driver of my integrated graphics card isnt getting installed.
[ATTACH=CONFIG]282095[/ATTACH][ATTACH=CONFIG]282094[/ATTACH]

In these 2 images, my pc settings, and Graphics memory (I have selected that), is shown...
The "Intel Sandybridge mobile" is my motherboard internal graphics, not my internal graphics card's memory..... cuz i currently hav "Intel HD Graphics 3000"....

Please help me! Or else i wud hav to recert back to some other operating system.... 
Thanks...

---

### Post by CatKiller on 2019-01-04
Your integrated graphics are [ HD Graphics 3000](https://ark.intel.com/products/52224/Intel-Core-i5-2410M-Processor-3M-Cache-up-to-2-90-GHz-).

It doesn't have any memory of its own. It claims it from system memory as needed.

---

### Post by sankarsuresh01 on 2019-01-04
Sorry... Got to know its HD Graphics 3000.... yet, it should still be more than 256MB... The Sandybridge graphics is not the one it should be using......

Because, during the days i was using windows, before i installed the graphics driver, it used to show "Intel Sandybridge Mobile"  and 256 MB as memory.... but after installing driver, it used to show "Intel HD Graphics 3000" and memory as 1072MB....

So, isnt there any driver for this in Ubuntu?
Sorry, I am new to ubuntu.. so i am still getting to know things on the way... :) 

Thanks

---

### Post by CatKiller on 2019-01-04
They are the same thing. HD Graphics 3000 is the name of the graphics part of your Sandy Bridge processor, as the link says. Nothing is on the motherboard, it's all inside the processor. 

There is a driver. It's included in the kernel, as kc1di said. There is nothing that you need to install.

---

### Post by sankarsuresh01 on 2019-01-05
Then I aren't I getting 1GB of graphics memory?? and i am i getting only 256MB? I'm experiencing lag issues due to this...

---

### Post by CatKiller on 2019-01-05
> **sankarsuresh01 said:**
> Then I aren't I getting 1GB of graphics memory?? and i am i getting only 256MB? 

Why do you believe that your shared memory is not being allocated correctly? You've shown nothing that would indicate that was the case. 

> I'm experiencing lag issues due to this...

You've given no details whatsoever of the "lag" you're experiencing, no details about which programs you're experiencing it in, nor any reason to believe that it is in any way related to any misallocation of shared memory that you claim to be the case.

You are most likely to get help by starting a new thread detailing the precise symptoms you've experienced and the details of what you do to trigger them. Your confusion about the graphics in your laptop will just muddy the matter.

---

### Post by sankarsuresh01 on 2019-01-05
I told that before ryt? that when i was using windows, i had 1GB graphics, wid the gpu INTEL HD 3000 GRAPHICS
But, in this, it shows 256MB graphics , with gpu INTEL SANDYBRIDGE MOBILE... 
In windows, it used to show INTEL SANDYBRIDGE MOBILE and 256MB, before i installed the drivers of INTEL HD 3000 GRAPHICS... aftr installing that , i got 1GB graphics, under the name INTEL HD 3000 GRAPHICS

And, lag means, while i open any application ,it hangs for a little bit.... nothin works.. and then , suddenly everything works...

---

### Post by CatKiller on 2019-01-05
The names you vaguely remember Windows giving things have no relevance to what your hardware's actually doing. 

> **sankarsuresh01 said:**
> And, lag means, while i open any application ,it hangs for a little bit.... nothin works.. and then , suddenly everything works...

That doesn't sound like a graphics issue in any way. Start a new thread, with specifics.

---

### Post by mikasu on 2019-01-06
your problem for your system hanging is : not enough RAM. You have 2GB - 256MB = 1.8GB~ for the whole system. Your apps hang because the OS takes 1 GB of RAM (roughly) by itself, so about 0.8GB for your apps, way not enough! Everything is running off swap or page file! If you cannot upgrade your system ram, I suggest that you try a light-weight distribution or flavour, like Lubuntu.

---

### Post by sankarsuresh01 on 2019-01-06
I understand... But, one doubt... In windows, i used to run NFS most wanted 2012, fifa, pes, shank2 , and all that games, with 2gb ram, and 1gb graphics....... cuz, when i checked my graphics memory in windows, it showed me I had 1072MB... but then , now, it shows 256MB.... I wanted to know why... ? And, wont that decrease in gpu memory affect my games and stuff in ubuntu which requires it??

---

### Post by CatKiller on 2019-01-06
It doesn't have **any**.

Not 256 MB. Not 1024 MB. None. Really, really, none.

The name is completely and totally irrelevant.

The video RAM is dynamically allocated from system RAM. The more that's allocated to the graphics, the less there is for everything else.

---

### Post by sankarsuresh01 on 2019-01-06
i understand.... thanks :)

---

### Post by Yellow Pasque on 2019-01-06
[https://bbs.archlinux.org/viewtopic.php?id=226537](https://bbs.archlinux.org/viewtopic.php?id=226537)

Modern Intel graphics allocate video memory dynamically (as needed) to avoid wasting RAM. 256MB is what the BIOS initially reserves, but the GPU can request more if needed. That would probably only happen with games though.
You can see the maximum allowable video memory by using the dmesg command as in thread I linked. As for Windows and Intel driver, it may have changed from reporting the initial video memory reservation to reporting the maximum allowed video memory to avoid confusion like yours.

> And, lag means, while i open any application ,it hangs for a little bit.... nothin works.. and then , suddenly everything works... 

If non-games do this, I find it unlikely that has anything to do with lack of video RAM. Replacing the hard disk with an SSD helps a lot with application load times.

---

### Post by mikasu on 2019-01-06
Replacing for an SSD or adding more RAM if possible. Ubuntu is arguably a bit more heavy than Windows depending on what you look at, so your 2GB of ram(of which your iGPU takes some megabytes) might not be enough for regular Ubuntu.

---

