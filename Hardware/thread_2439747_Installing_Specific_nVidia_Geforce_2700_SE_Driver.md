---
title: "Installing Specific nVidia Geforce 2700 SE Driver"
date: 2020-03-31
forum: Hardware
---

### Post by jacwight on 2020-03-31
Hello,

I am having issues installing a driver compatible with my nVidia Geforce 2700 SE graphics card. There are a few instructions I have followed online with no success. My issues are general corruption, and the screen often displays at something similar to 800 x 600 making it quite difficult to navigate anything. Any advice on how to install the proper driver would be greatly appreciated.

---

### Post by Autodave on 2020-03-31
What driver are you trying to install and where did you get it from?

---

### Post by Yellow Pasque on 2020-04-01
> **jacwight said:**
> nVidia Geforce 2700 SE

I've never heard of it and don't see it in the list. Did you typo and mean RTX 2070?
[https://en.wikipedia.org/wiki/List_of_Nvidia_graphics_processing_units](https://en.wikipedia.org/wiki/List_of_Nvidia_graphics_processing_units)

---

### Post by Autodave on 2020-04-01
Also, what version of 'buntu are you running?

---

### Post by jacwight on 2020-04-01
> [COLOR=#000000]What driver are you trying to install and where did you get it from?[/COLOR]

I have lost the instructions I was following, but my understanding was that I was grabbing a ppa which would allow me to install the driver nvidia says I need. There is a good chance this was the wrong driver - I apologize, as I am having trouble finding it now. My system became impossible to navigate as I mentioned above so I reinstalled. 

> [COLOR=#000000]I've never heard of it and don't see it in the list. Did you typo and mean RTX 2070?[/COLOR]
[https://en.wikipedia.org/wiki/List_o...ocessing_units]("https://en.wikipedia.org/wiki/List_of_Nvidia_graphics_processing_units")

It looks like I read this wrong, ahaha. I should be going with G72, right? I mixed up [GeForce 7200 GS / 7300 SE].
product: G72 [GeForce 7200 GS / 7300 SE]
 vendor: NVIDIA Corporation

> [COLOR=#000000]Also, what version of 'buntu are you running?[/COLOR]
I am running 18.04.4 with the Budgie desktop environment.

---

### Post by Yellow Pasque on 2020-04-01
The open source nouveau driver (included "out of the box") is the only option here. The last Nvidia proprietary driver to support this GPU is 304.137, and it was dropped from Ubuntu 18.04.x because the kernel version is too new: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-304/+bug/1763648](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-304/+bug/1763648)

If you read the bug report, you'll see that there are some patches out there that might allow 304.137 to work on Ubuntu 18.04**.1**
I wouldn't recommend trying that unless one is comfortable with command line, recovering a broken system, reinstalling, etc.

---

### Post by TheFu on 2020-04-01
I had to replace my 7200 about a year ago when I moved off 14.04 to get the resolution support I wanted. Bought a 1030.
The F/LOSS driver was stuck at 1080 resolutions though the card had been running at 1920x1200 for a very long time.  No proprietary nvidia driver works on 16.04 or later releases for that GPU.

---

### Post by Yellow Pasque on 2020-04-01
> **TheFu said:**
> No proprietary nvidia driver works on 16.04 or later releases for that GPU.

The 304.xx driver is included in the 16.04 repo and should work if you stick to the 4.4 kernel series included with 16.04(.1).
Also, you can probably hack/patch the driver to work with Ubuntu 16.04.5/6 just like you can with 18.04.1

---

### Post by TheFu on 2020-04-01
> might allow
means wasting 4 hrs. What happens when a new kernel happens? What about new releases?  This problem will be forever with us. 

$65 for a new GPU makes this problem go away, now, today, for the next 7-10 yrs. How much is your time worth?

That was my thought process, though I didn't want to spend any more money. 1080 resolution was just too frustrating to me. Couldn't imagine being stuck at 800x600.

---

### Post by Yellow Pasque on 2020-04-01
I feel like we're blowing off course here. 

> **TheFu said:**
> means wasting 4 hrs. What happens when a new kernel happens?
If dkms is working properly, then it should be no problem. Unless you're talking about installing HWE packages, which is a no-no in this case.

> What about new releases? 
What about them? If, for some reason, nouveau can't work, at least installing Nvidia 304.xx will take you to 2023 if you're willing to use an LTS release for 5 years.

> $65 for a new GPU makes this problem go away
True, but not everyone has money to spend on a GPU, especially in the middle of a pandemic.

So it's up to the OP to decide whether to try the 304 hack or look at troubleshooting nouveau (or buy a new GPU).
If troubleshooting nouveau, let's have a look at /var/log/Xorg.0.log from a good boot and one where it goes to 800x600.

---

### Post by jacwight on 2020-04-01
I don't especially mind rolling back to an older release of Ubuntu (assuming I could still receive security updates?). Right now, I cannot replace my GPU, which would be the easiest solution (and hey, new GPU!). I'm fine with 1080 graphics, and I am mostly trying to get by with what I have available.

> [COLOR=#000000]So it's up to the OP to decide whether to try the 304 hack or look at troubleshooting nouveau (or buy a new GPU).[/COLOR]
[COLOR=#000000]If troubleshooting nouveau, let's have a look at /var/log/Xorg.0.log from a good boot and one where it goes to 800x600.[/COLOR]

I am not sure on how to do this. Currently, I can use the system. I get the 800x600 resolution when I attempt to "fix" my GPU driver issue, or upon installation (not sure why it does or does not upon install).

---

### Post by TheFu on 2020-04-01
16.04 is the oldest release still supported for free.

---

### Post by Yellow Pasque on 2020-04-01
Nvm. Just me being paranoid

---

### Post by jacwight on 2020-04-01
> 16.04 is the oldest release still supported for free.

I rolled back to 16.04 with software/security updates, and have encountered zero issues! It's kind of nostalgic to my first experience with Linux (naturally Ubuntu) back in high school. This will definitely work until I can update my GPU. I seriously appreciate the advice everyone has given me.

> Based on the name and date of the OP's account, I guess this is an  April's Fool thread. HA HA. You got me LULZ, etc. Let's move on..

It was March 31st (Central time, USA) when I created my account. I'm guessing the website is hosted in the U.K. Anyway, not that I have to explain myself, but my username is out of laziness - the initials of my first three names (I'm Oklahoman), and a pun on my last name. 

Anyway, thanks everyone, and stay safe.

---

### Post by Yellow Pasque on 2020-04-01
I love a happy ending. Please mark the thread SOLVED (thread tools menu above first post)

---

