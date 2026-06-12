---
title: "Problems installing Marvell Yukon drivers"
date: 2007-06-24
forum: Hardware &amp; Laptops
---

### Post by stil on 2007-06-24
Hey guys

I've downloaded the latest marvell yukon drivers for my satellite A200. I'm running into a problem with the installer not finding the kernel headers.

I get a message like "Kernel header not found. Please install the linux header files development package or create a symbolic link from the /usr/src/KERNEL_VERSION /usr/scr/linux"

I have since used synaptic to install headers 2.6.15-26-386, and then attemped to create a symbolic link 

ln -s /usr/src/linux-headers-2.6.15-26-386 /usr/src/linux

produces the result

ln: creating symbolic link '/usr/src/linux' to '/usr/src/linux-headers-2.6.15-26-386': File exists

I tried installing again but get the same error about not detecting the headers :(

---

### Post by stil on 2007-06-24
I've looked through synaptic package manager for a header with the format kernel-headers.*.*.* and found version 2.6.11.2-0ubuntu18

I'm confused, these are not the ones I want, right?

uname - r returns 2.6.15-386

---

### Post by stil on 2007-06-25
Serious question, guys. Is it really worth posting here? This thread is only 10 hours old and it has already reached 3rd page oblivion once.

I get the impression there's  alot of luck involved getting at least one response, or did I say something taboo?

---

### Post by mfm3 on 2007-06-29
I'm with you. Seems that there are too many issues for the knowledgeable people who answer questions on this forum to keep up with. I search and search for something like the problem i'm having, and when i find it it is just someone like you who asked a legitimate question and got no response. Not very encouraging to ask questions.
Anyway, did you have any luck with this?

---

### Post by stchman on 2007-06-29
> **stil said:**
> Hey guys

I've downloaded the latest marvell yukon drivers for my satellite A200. I'm running into a problem with the installer not finding the kernel headers.

I get a message like "Kernel header not found. Please install the linux header files development package or create a symbolic link from the /usr/src/KERNEL_VERSION /usr/scr/linux"

I have since used synaptic to install headers 2.6.15-26-386, and then attemped to create a symbolic link 

ln -s /usr/src/linux-headers-2.6.15-26-386 /usr/src/linux

produces the result

ln: creating symbolic link '/usr/src/linux' to '/usr/src/linux-headers-2.6.15-26-386': File exists

I tried installing again but get the same error about not detecting the headers :(

One of my desktop computers has an ASUS motherboard.  That motherboard has a Marvell Yukon gigabit NIC and it worked out of the box with both Feisty and Edgy.

---

### Post by stil on 2007-06-30
> **mfm3 said:**
> I'm with you. Seems that there are too many issues for the knowledgeable people who answer questions on this forum to keep up with. I search and search for something like the problem i'm having, and when i find it it is just someone like you who asked a legitimate question and got no response. Not very encouraging to ask questions.
Anyway, did you have any luck with this?

No luck with it yet. I've decided to stop stressing about it at the moment and gave ubuntu a try on my old AMD-XP 1600 system. Works a charm! Everything installed correctly first time, and I've managed to get 3D acceleration working on the GF4! All I need now is a broadband connection of my own :(

stchman: That's great, but not much help to me.

---

### Post by allies on 2007-12-20
Hey... I just installed Gutsy on my computer last night, and am having the exact same problem as you.  in my /usr/src i have both 2.6.22-14 and 2.6.22-14-generic.  when i try to create a symlink with either and install the Marvell Yukon drivers it says the headers cannot be found :\

---

### Post by stil on 2007-12-20
I don't think I can help, sorry. Gutsy works fine for me!

---

### Post by allies on 2007-12-20
Are you using x64 or 32bit?  I'm trying x64 but I heard 32bit might play nicer with Intel setups...

---

