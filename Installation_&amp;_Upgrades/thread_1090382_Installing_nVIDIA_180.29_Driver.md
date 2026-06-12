---
title: "Installing nVIDIA 180.29 Driver"
date: 2009-03-08
forum: Installation &amp; Upgrades
---

### Post by VarthDader on 2009-03-08
Hi all. I'm new to Ubuntu. I installed 8.04 today and I can't get my nVIDIA drivers installed on it. I've tried 
```
sudo sh NVIDIA-Linux-x86-180.29-pkg1.run
```
When I try this, I get an error saying that the file can't be opened. I also tried this in the command line after stopping GNOME. 

Any help would be appreciated

---

### Post by anilcr on 2009-03-08
try this
```

chmod u+x NVIDIA-Linux-x86-180.29-pkg1.run
sudo sh NVIDIA-Linux-x86-180.29-pkg1.run

```

---

### Post by VarthDader on 2009-03-08
It says file not found when I use

```
chmod u+x NVIDIA-Linux-x86-180.29-pkg1.run
```

The file is on the desktop. Should I have put it elsewhere?

---

### Post by anilcr on 2009-03-08
why dont you try this:
1.right click on the file -> properties.
2.go to permissions tab and then click on Allow executing file as program
3.then try sudo sh NVida-...

---

### Post by Speed Demon on 2009-03-08
You can use Ubuntu's binary drivers, which are pretty well point-click-type-go for the install. Just use System->Administration->Hardware Drivers ((I THINK, may be other name)) and go from there!

---

### Post by VarthDader on 2009-03-08
I tried the chmod after checking the allow file as program and still same issue.

And when I tried the Harware drivers, it just shows a blank page. :(

---

### Post by Therion on 2009-03-08
Open the Terminal and before you do anything else you need to go to your Desktop directory where you've stored the file: ```
cd ~/Desktop
``` 

NOW try using sudo sh NVIDIA-Linux-x86-180.29-pkg1.run

Also, note it's a CAPITAL "D" in Desktop.  :)

---

### Post by anilcr on 2009-03-08
got the same problem here too I installed an hardy on my desktop today same problem on that can't install from hardware drivers. I also installed nvidia-glx-new and new-dev from the repos. didn't seem to work. I'm using amd64

---

### Post by VarthDader on 2009-03-08
> **Therion said:**
> Open the Terminal and before you do anything else you need to go to your Desktop directory where you've stored the file: ```
cd ~/Desktop
``` 

NOW try using sudo sh NVIDIA-Linux-x86-180.29-pkg1.run

Also, note it's a CAPITAL "D" in Desktop.  :)

I figured that out just before you posted this. Well, now it says that I'm running X and need to exit it. How do I do that?

---

### Post by anilcr on 2009-03-08
```
sudo telinit 1
```

---

### Post by anilcr on 2009-03-08
better ctr-alt-F1

---

### Post by VarthDader on 2009-03-08
Thanks. I managed to install the drivers by stopping GNOME. The drivers are installed, but I can't seem to increase my screen resolution, neither my refresh rate

---

### Post by VarthDader on 2009-03-08
Anyone?

---

### Post by cviorel on 2009-03-09
Hi!
Try running ```
sudo nvidia-xconfig
``` in the console. This will modify your xorg.conf file and tell it to use the driver.

---

### Post by Crafty Kisses on 2009-03-09
Once you have downloaded the NVIDIA driver you need to stop your X server, so press Cntrl-Alt-F2. Once you have done that you need to run the following:
```
sudo /etc/init.d/gdm stop
```
Then once you've done that you need to run the following, remember I'm just guessing the file is called NVIDIA-Linux and it's saved to your desktop, so remember substitute your information:
```
cd ~/Desktop
chmod +x NVIDIA-Linux.run
sudo ./NVIDIA-Linux.run
```
Once the installation is done, restart the X server with:
```
sudo /etc/init.d/gdm start
```

---

### Post by tad1073 on 2009-03-09
make sure to disable the nvidia driver that you are currently using.

then 

ctrl+alt+f2

```
 cd ~/Desktop
``````
sudo /etc/init.d/gdm stop
```

```
sudo sh ./NVIDIA-Linux-x86-180.29-pkg1.run
```follow all the prompts

```
sudo /etc/init.d/gdm start
```

---

### Post by VarthDader on 2009-03-09
Thanks. I'll try this.

---

### Post by mjr2k on 2009-03-09
I've got a problem related to this thread.

I had roughly the same problem; I installed the Nvidia drivers and now I'm trying to get back into X.

I started the GDM with the code in the 2nd-to-last message.  When I attempt to restart X with the 'startx' command, I get 
"Fatal Error"
"No Screens Found"

Also, I've seen mention of editing /etc/inittab to specify which init mode to boot into.  Apparently Intrepid doesn't use inittab, but rather Up-something.  Can anyone shed light on this?

Also when I do 'sudo telinit 5' from a command prompt, I get "Starting Gnome Display Manager" and then it freezes.

---

