---
title: "Graphics driver"
date: 2015-07-07
forum: Hardware
---

### Post by lizard2014 on 2015-07-07
Hello. I have a new laptop which has NVIDIA GeForce 820M  (2GB dedicated DDR3) graphics card but it is not detected in Ubuntu 15.04. I initially downloaded the Linux 64-bit driver from the NVIDIA website for India which ruined things up (I was unable to log in). The same problem occurred when I downloaded Linux 64-bit driver for Linux from NVIDIA site for USA. This was the problem which occurred both times:
 
First, to execute the .run file, I typed the following commands (after going to Downloads directory where the driver was saved):
```
chmod +x driver_file.run
```
```
./driver_file.run
```
After a while, I got an error message that you are using an X-server (and the installation failed). Then, I rebooted the machine. After grub loaded, I selected the Ubuntu recovery mode and selected the option "Drop to root shell". Then I went to the directory where the driver was downloaded and typed the above two commands and this time the X-server error was not there (as expected). I then got multiple error messages and the installation was complete (may not be proper). But after that, whenever I tried to log in to my user account, I was again thrown back to the login prompt. This happened every time I tried to log in. I then pressed CTRL+ALT+F1  and then logged in but when I typed startx, still the same problem occurred.... I was completely unable to log in. Also, I am not sure whether the driver was properly installed or not. What should I do?

---

### Post by dino99 on 2015-07-08
From the root shell, run:
> apt-get purge nvidia*
> apt-get install nvidia-346

that is, always use packages found into the ubuntu archive

---

### Post by lizard2014 on 2015-07-10
But when I run that command in Ubuntu 14.04.2 LTS, I get "Unable to locate package nvidia-346".

---

### Post by Bucky Ball on 2015-07-10
Do an update. Open Additional Drivers. You should see something in there.

Do you have the 'Proprietary drivers for devices' ticked in your Software and Updates?

---

### Post by lizard2014 on 2015-07-10
> **Bucky Ball said:**
> Do an update. Open Additional Drivers. You should see something in there.
I had already updated, but saw nothing in the Additional Drivers.
> **Bucky Ball said:**
> Do you have the 'Proprietary drivers for devices' ticked in your Software and Updates?
Yes. Still I get the same output from the terminal: "E: Unable to locate package nvidia-346"

---

### Post by mc4man on 2015-07-10
In post 1 you say - "but it is not detected in Ubuntu 15.04." Now it's - "But when I run that command in Ubuntu 14.04.2 LTS"
So which one are you using?

---

### Post by lizard2014 on 2015-07-10
> **mc4man said:**
> In post 1 you say - "but it is not detected in Ubuntu 15.04." Now it's - "But when I run that command in Ubuntu 14.04.2 LTS"
So which one are you using?

I was using 15.04 when I started the thread, and by the commands given by **dino99**, graphics driver was installed successfully. Before installing the driver, the screen used to flicker a lot and used to turn off after sometime (whenever I used to log out or switch user). The same problem existed even after installing the graphics driver, indicating that it wasn't a driver problem. Since the screen was irritating a lot, I formatted 15.04 and installed 14.04.2 LTS and that screen-flickering problem is not there anymore. However, 14.04.2 indicates that there is no package named as nvidia-346 (system is fully up to date).

---

### Post by Bucky Ball on 2015-07-10
So, you have fixed your graphics problem by installing 14.04 LTS? Please mark the thread as solved (see second link in my signature). This won't close the thread, but it will help others. Thanks.

If you have issues with anything else, please post a new thread with a descriptive title.

PS: BTW, you would want [this]("http://www.nvidia.com/download/driverResults.aspx/86390/en-us") driver anyhow, according to nvidia. Unsure why the other was suggested. If the system is working fine with the open-source driver, I wouldn't bother with either. Forget about looking for the one suggested previously, in the kernel or anywhere else. :)

---

### Post by mc4man on 2015-07-10
The latest nvidia in 14.04 is 331 - so 
```
sudo apt-get install nvidia-331-updates
```
(though make sure you are not using the 3.19 kernel, you shouldn't be as it is for 14.04.3 (vivid-lts) & currently in trusty -proposed

---

### Post by lizard2014 on 2015-07-10
> **Bucky Ball said:**
> So, you have fixed your graphics problem by installing 14.04 LTS? Please mark the thread as solved (see second link in my signature). This won't close the thread, but it will help others. Thanks.

If you have issues with anything else, please post a new thread with a descriptive title.

I only fixed the screen flickering problem by installing 14.04. The main problem, i.e., the driver for the graphics card (Nvidia GeForce 820M) is not installed and so, the thread is not solved.

---

### Post by Bucky Ball on 2015-07-10
Read my last post where you quoted from. It's been edited. That is the wrong driver you are looking for and if the open-source driver is working fine, I wouldn't bother.

Basically, if you can avoid third-party drivers, the smoother your ride will be. They are needed for some functionality on some cards though, like 3D.

---

### Post by mc4man on 2015-07-10
Just to add - 
your 820m can use either nvidia or intel gpu's, after installing nvidia & rebooting you'll be using nvidia. After that you can switch between the 2 in nvidia-settings (prime profiles) & a log out in
All recent nvidia mobile gpu's will have no vsync in a compositing  env. & h tearing will be prevalent in a ubuntu session

---

### Post by lizard2014 on 2015-07-10
> **Bucky Ball said:**
> If the system is working fine with the open-source driver, I wouldn't bother with either. Forget about looking for the one suggested previously, in the kernel or anywhere else. :)
There is no driver installed by default (only intel HD graphics 5500 is detected).

Installing driver from the nvidia's website screws up the system (as mentioned in the first post).

---

### Post by lizard2014 on 2015-07-10
> **mc4man said:**
> Just to add - 
your 820m can use either nvidia or intel gpu's, after installing nvidia & rebooting you'll be using nvidia. After that you can switch between the 2 in nvidia-settings (prime profiles) & a log out in
All recent nvidia mobile gpu's will have no vsync in a compositing  env. & h tearing will be prevalent in a ubuntu session

But how do I install the card? sudo apt-get install nvidia-346 doesn't install the driver in 14.04 but it installed the driver in 15.04 but in 15.04 screen was flickering. What should I do? In system details, only Intel HD graphics 5500 is detected.

---

### Post by mc4man on 2015-07-10
> **lizard2014 said:**
> But how do I install the card? sudo apt-get install nvidia-346 doesn't install the driver in 14.04 but it installed the driver in 15.04 but in 15.04 screen was flickering. What should I do? In system details, only Intel HD graphics 5500 is detected.

see [http://ubuntuforums.org/showthread.php?t=2285696&p=13318758&viewfull=1#post13318758](http://ubuntuforums.org/showthread.php?t=2285696&p=13318758&viewfull=1#post13318758)

---

### Post by mc4man on 2015-07-11
> **mc4man said:**
> 
All recent nvidia mobile gpu's will have no vsync in a compositing  env. & h tearing will be prevalent in a ubuntu session

will take that back - for mobile nvidia it may be up to the  manufacturer as to whether optimus is used.  A laptop I just got here with a gtx 970m is nvidia only, vsync enabled & no tearing...

---

### Post by lizard2014 on 2015-07-11
After running sudo apt-get install nvidia-331-updates, graphics card is now detected.

---

### Post by lizard2014 on 2015-08-10
After the third point release of 14.04, I ran **sudo apt-get install nvidia-346**. It got installed correctly, but whenever I take the cursor to the top, the cursor disappears (tough still active). For example, if I want to power off the machine, I need to click the Power button on the top right. How will I figure out where is the pointer at that time if I can't see it? Should I install nvidia-331-updates again? I am using kernel 3.19  (Ubuntu 14.04.3)

---

### Post by Bucky Ball on 2015-08-11
Try changing the resolution in Display. Sounds like you might have the wrong resolution set.

---

### Post by lizard2014 on 2015-08-11
The default resolution is 1366x768. In Windows also, the same resolution is observed but without this problem. I have tried all resolutions available in Displays but still the problem exists (cursor hides at the top edge of the screen).

---

