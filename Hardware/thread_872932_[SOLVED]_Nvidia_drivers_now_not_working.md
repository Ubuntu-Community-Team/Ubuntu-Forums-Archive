---
title: "[SOLVED] Nvidia drivers now not working"
date: 2008-07-28
forum: Hardware
---

### Post by sumpm1 on 2008-07-28
Hi. Running 8.04.1. I have onboard Nvidia graphics, and they were working with the "proprietary drivers" just fine, including all effects compiz. I am trying to install Wine and a recording app Reaper and am following this guide: [http://forum.cockos.com/showthread.php?t=16786](http://forum.cockos.com/showthread.php?t=16786)

After installing everything on the Linux side, I restarted for the changes to take effect. When I restarted, the graphics are back to 800x600, and the Nvidia drivers do not appear in the "Hardware Drivers" section. Can anyone tell me what the problem is?

Thanks

---

### Post by ajgreeny on 2008-07-28
Have you also updated your system with a new kernel?  The last one I had was on 15 July, but if you do not update regularly it might have arrived with you later than that.  If this is the case, you will need to reinstall the nvidia driver again.  It is needed every time there is a kernel update/upgrade, I'm afraid.

---

### Post by sumpm1 on 2008-07-28
Well, I just installed 8.04.1 like two days ago, does that change anything?

Also, would any of the changes in the guide I am using affect graphics perhaps? How do I upgrade the kernel? (will search)

And how do I REINSTALL the nvidia driver when it does not appear in the Hardware drivers list?

Thanks again

---

### Post by tuxxy on 2008-07-28
You could try and install it in Envy

---

### Post by phidia on 2008-07-28
> **sumpm1 said:**
> Well, I just installed 8.04.1 like two days ago, does that change anything?

Also, would any of the changes in the guide I am using affect graphics perhaps? How do I upgrade the kernel? (will search)

And how do I REINSTALL the nvidia driver when it does not appear in the Hardware drivers list?

Thanks again

Take a look at the Ubuntu video card setup guide [here]("https://help.ubuntu.com/community/Video") and make note of the changes (and links) with hardy and xorg 7.3.

---

### Post by knightcoder on 2008-07-28
Yeah. EnvyNG is simple and convenient. I'd really suggest you to use it to save the hassle of installing the drivers yourself.

The link is here...
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by hotweiss on 2008-07-28
> **sumpm1 said:**
> Well, I just installed 8.04.1 like two days ago, does that change anything?

Also, would any of the changes in the guide I am using affect graphics perhaps? How do I upgrade the kernel? (will search)

And how do I REINSTALL the nvidia driver when it does not appear in the Hardware drivers list?

Thanks again

1. sudo apt-get remove nvidia* (will also remove any other restricted modules (e.g.-madwifi), so watch out)
2. sudo apt-get install envyng-gtk
3. enable the proposed repositories
4. sudo apt-get update
5. sudo envyng -g
6. Select Nvidia on the left side, now click on Install the Nvidia driver (Manual Selection of the Driver), select 173, and finally click Apply.
7. Once the installation is completed, reboot and you will once again have a crisp screen.

---

### Post by sumpm1 on 2008-07-28
I installed envyng in the synaptic package manager. I ran it and just had it detect my hardware. I am now stuck in 640x480. I am a total newb to Linux.

I want to know why the Nvidia "restricted drivers" don't appear in the  "hardware drivers" list anymore? How can I get those drivers back, cause I can't hardly see the sreen at 640x480 lol!

---

### Post by knightcoder on 2008-07-28
Did you select the Nvidia driver or the ATI driver in Envy ?

---

### Post by sumpm1 on 2008-07-28
Of course I selected the Nvidia driver! I tried Envy 3 times and still was stuck at 640x480. I used Envy to remove the Nvidia drivers just to get back to 800x600 so I could see! Like I said, I am newb, and know very little about kernels and such. I belive the tutorial I did updated the kernel to realtime kernel, could this be the problem? And how can I check my kernel? How do I know if there is a Nvidia driver for that kernel?

Thanks

---

### Post by mufn8r on 2008-07-28
I have the same problem. Envy messed up my nVidia driver and I can't fix it!

---

### Post by sumpm1 on 2008-07-29
UPDATE: Well I was able to get the restricted drivers to appear in "Hardware Drivers" by installing the linux restricted modules for my version. These are the steps I followed:

1. Uninstall envyng from synaptic
2. type 'uname -a' in the terminal to determine the kernel
3. install the linux restricted module for your specific kernel in synaptic

But I am still limited to a max resolution of 640x480!!! I am not sure what to do now, I will do alot of searching.

---

### Post by hotweiss on 2008-07-30
> **sumpm1 said:**
> UPDATE: Well I was able to get the restricted drivers to appear in "Hardware Drivers" by installing the linux restricted modules for my version. These are the steps I followed:

1. Uninstall envyng from synaptic
2. type 'uname -a' in the terminal to determine the kernel
3. install the linux restricted module for your specific kernel in synaptic

But I am still limited to a max resolution of 640x480!!! I am not sure what to do now, I will do alot of searching.

Did my previous instructions fail?

---

### Post by sumpm1 on 2008-07-30
> **hotweiss said:**
> Did my previous instructions fail?

Actually, I was still stuck at 640x480 after that, and I had no way to go change that setting, the max in the nvidia settings panel was 640, so envng DID install a driver for the card, but to get the original setup working (restricted drivers) to appear in Ubuntu and all, I just had to install the linux restricted module for my new kernel. The real problem was that I changed my kernel and didn't know that all of these issues came with that. For now on I will change kernels with hesitance.

Thanks everybody.

---

