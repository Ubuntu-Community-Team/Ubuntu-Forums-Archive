---
title: "Graphics problems with laptop"
date: 2012-01-06
forum: Hardware
---

### Post by SlasherIT on 2012-01-06
Hi,

I have a HP Pavilion zd7060ea, 1.25GB RAM, NVIDIA GeForce FX Go 5600, Intel Pentium 4 3.06GHz.

(In Windows 7, everything used to work fine and I had no problems). 

I am facing some graphics problems with Ubuntu 11.10. I am using NVIDIA Driver version 96, although I have used 173 too and encounter the same problems.

The problems are:

When starting up, instead of seeing the purple background and Ubuntu logo with the dots signalling it is loading, I just see large black and white lines, although it does boot up to the desktop properly. Ditto this when shutting down, I encounter these black and white lines again, although it does shut off properly.

Random crashing, when using the computer, especially watching Youtube videos or playing Minecraft, it randomly freezes and can not be fixed without force shutting down the laptop.

Suspend problems, when trying to resume the computer from Suspend, it fails to wake up the display, so I cannot see anything at all until I shutdown and restart the computer (force, using the button). Same thing happens when trying to resume the display after it turns off the display after a period of time (5 minutes), cannot see the display until shutting down and restarting.

So those are my problems, and I would greatly appreciate some help, thank you.

---

### Post by SlasherIT on 2012-01-07
Bump, sorry.

---

### Post by SlasherIT on 2012-01-10
Anyone?

---

### Post by SlasherIT on 2012-01-19
Bump.

---

### Post by madvinegar on 2012-01-19
First of all I can see from this link that the driver for your card is the 173.14.xx.

[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

So I suppose you should stick with that.


On the other hand, how did you load the drivers?

Normally you should find the **recommended** 173 driver on the repositories plus another one (experemental) for the 3D effects.
Both should work.
Go to **"additional drivers"** and it should be there.

Otherwise, go to Synaptics and install the following packages:

nvidia-glx-173
nvidia-glx-173-dev
nvidia-173-kernel-source
nvidia-173
nvidia-173-dev

Install all above and reboot and see what happens.


_Note: No need to say that you must also uninstall all drivers relating to the driver version 96._

---

### Post by SlasherIT on 2012-01-19
Hi, I installed the NVIDIA drivers when checking for Additional Drivers, I first selected 173 recommended, but was getting the issues I noted above, so I tried the 96 driver, yet it has the same issues. Right now I haven't switched back to the 173, am still on 96...

So what steps should I take to fix this? Thanks, and please note that I'm a Linux newbie :(.

---

### Post by madvinegar on 2012-01-20
Try this.
De-activate both of the drivers (173 and 96) from "additional drivers" and then go to synaptics and install the packages I have written to you above.

---

### Post by SlasherIT on 2012-01-22
Hi,

I deactivated the drivers from Additional Driver. In Synaptics, I checked and it says that nvidia-173 is already installed, and I can't find all the other packages on Synaptics you mentioned except nvidia-173-dev. What should I do?

---

### Post by madvinegar on 2012-01-23
Probably you have to update the packages.

I suppose that you have internet connection on the laptop?

Open synaptic package manager and click on "reload".

Then click on "mark all upgrages" and then "apply".

---

### Post by SlasherIT on 2012-01-23
And what about the other packages you listed that I can't find on Synaptics?

---

### Post by madvinegar on 2012-01-23
I hope that after you update Synaptic manager, you will be able to find the other packages as well.

If you follow the procedure I explain above you will update all the packages in synaptic.

---

### Post by SlasherIT on 2012-02-17
Hi,

Sorry I haven't replied in a while, I have been very busy lately. Anyways, I upgraded all packages in Synaptics, but I still can't find the other NVIDIA packages you mentioned. What should I do now? Thanks.

---

### Post by Yellow Pasque on 2012-02-17
> When starting up, instead of seeing the purple background and Ubuntu logo with the dots signalling it is loading, I just see large black and white lines, although it does boot up to the desktop properly. Ditto this when shutting down, I encounter these black and white lines again, although it does shut off properly.
That's extremely common for the nvidia (and ati) binary drivers since they don't support KMS. Google for solutions.

> Random crashing, when using the computer, especially watching Youtube videos or playing Minecraft, it randomly freezes and can not be fixed without force shutting down the laptop.
I suspect overheating, especially with a 3GHz P4 crammed inside a laptop. Monitor your temps carefully when doing something CPU-intensive.

---

### Post by SlasherIT on 2012-02-17
How can I enable KMS?

This didn't happen under Windows, but I'll check the temps anyways.

---

### Post by Yellow Pasque on 2012-02-17
> **SlasherIT said:**
> How can I enable KMS?

This didn't happen under Windows, but I'll check the temps anyways.
You can't enable KMS with the nvidia binary driver. Some workarounds: [http://askubuntu.com/questions/6033/enabling-nvidia-driver-messes-up-splash-screen](http://askubuntu.com/questions/6033/enabling-nvidia-driver-messes-up-splash-screen)

---

### Post by SlasherIT on 2012-02-17
Hi,

Thanks, that worked, I now see the Ubuntu screen when Starting or Shutting the computer.

Although I still can't resume from Suspend and Hibernate or when the screen shuts off to save power, know how to fix that? Thanks.

---

### Post by SlasherIT on 2012-03-05
Hello? Anyone?

---

### Post by SlasherIT on 2012-03-29
Bump, guys please, I still need help, I still can't resume from Suspend and Hibernate or when the screen shuts off to save power. :(.

---

### Post by SlasherIT on 2012-04-03
:(, is there no-one that can help?

---

### Post by SlasherIT on 2012-04-06
Hello??

---

### Post by SlasherIT on 2012-04-18
Hello why doesn't anyone help me, instead of ignoring my thread???

---

