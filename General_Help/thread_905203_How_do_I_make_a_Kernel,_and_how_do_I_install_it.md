---
title: "How do I make a Kernel, and how do I install it?"
date: 2008-08-30
forum: General Help
---

### Post by Raghallac on 2008-08-30
i just got a new notebook (nVidia GeForce 9800M GTS; Intel Centrino 2 Duo Mobile 98400 2.26GHZ; 4GB DDR3 Dual Channel; INTEL WI-FI 5100agn Draft-N; Gateway FX Laptop) and I am trying to figure out how to write the Kernel's for the 5100agn Wireless. 

I have no idea how to even begin creating Kernels or following along with the boards on alot of what they have put down. 

I'm obviously a n00b, however, I need someone to give me a Link to a guide, step-by-step preferably, or something to understanding Kernels or else I fear I will be doomed to ignorance and Vista. 

Any help would be great.

---

### Post by gmxgeek on 2008-08-30
Well, if you are new to the world of linux 'writing' a kernel is probably not what you want to do, nor would be compiling one from souce. You are wanting to install ubuntu for the first time yes?

---

### Post by Raghallac on 2008-08-30
I've already installed it. I can't get my damn drivers to all be compatible

---

### Post by gmxgeek on 2008-08-30
Which drivers specifially? Audio, video, or network?

---

### Post by Raghallac on 2008-08-30
Intel Wireless Wi-Fi Link 5100agn 802.11a/b/g/Draft-N

---

### Post by gmxgeek on 2008-08-30
Have you tried downloading the drivers from theirs website and compiling the drivers themselves from source?

---

### Post by Raghallac on 2008-08-30
What I found was this:
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=879134](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=879134)
Four pages of how to make the program work. 
But, I'm so green at Ubuntu I'm getting lost way too easily.

---

### Post by gmxgeek on 2008-08-30
Do you have linux source drivers, or are you using an ndiswrapper?

---

### Post by Raghallac on 2008-08-30
I'm not using either. I don't really know where to begin.

---

### Post by Raghallac on 2008-08-30
From what I gathered, from the link, and my googling and web-browsing is Intel came out with a Driver, but I need to edit it somehow.

---

### Post by Raghallac on 2008-08-30
I might (and very well likley) be making this issue harder than it really is, but, I have no definitions to go off of. 
So, any help would be great. Or even a step in the right direction.

---

### Post by gmxgeek on 2008-08-30
What you would like to find, is a linux source package, usually in a X.tar.gz file, that contains the driver source code. You can then compile that into your system. I can help you with that, but first we need the source :P so look around a bit and see if you can find some.

---

### Post by Raghallac on 2008-08-30
I keep bumping into Kernel>=2.6.24 and Kernel>=2.6.26

Also, Compat-Wireless Project. 

This page has some of the stuff I was mentioning on it:
[http://ubuntuforums.org/showthread.php?p=5650315](http://ubuntuforums.org/showthread.php?p=5650315)

Post: #16

---

### Post by gmxgeek on 2008-08-30
can you copy output of
```

uname -a

```

---

### Post by Raghallac on 2008-08-30
I'm not sure what you're asking. 
Can I copy "uname -a" where?

---

### Post by gmxgeek on 2008-08-30
into a terminal sorry

---

### Post by Raghallac on 2008-08-30
No need to apologize. 
Where is there terminal at? The startup terminal? Cause right now I am running the Live CD, until i can install all my Hardware.

Or is there something I can type to get to the terminal, while running ubuntu?

---

### Post by Raghallac on 2008-08-30
nevermind. I figured it out. Ill type it in, brb.

---

### Post by gmxgeek on 2008-08-30
Applications, Accessories, Terminal

---

### Post by Raghallac on 2008-08-30
It came up with:

Linux ubuntu 2.6.24.19-generic #1 SMP Wed June 18 14:15:37 UTC 2008 x86_64 GNU/Linux

---

### Post by Raghallac on 2008-08-30
I've got to go get ready for work. So, I will check the forums, when I get back around 1pm Central-US American Time Zone.

---

### Post by gmxgeek on 2008-08-30
okay, so you will want to look for drivers that work with kernel version 2.6.24.19

sorry, but i must go to sleep now as it is 5:00 AM :P

but i wish you the best of luck!

---

