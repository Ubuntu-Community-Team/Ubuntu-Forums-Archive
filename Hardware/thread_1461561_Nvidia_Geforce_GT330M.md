---
title: "Nvidia Geforce GT330M"
date: 2010-04-24
forum: Hardware
---

### Post by flipflipsen on 2010-04-24
Hi,

I have a Sony Vaio F-series Laptop computer.
Originally windows 7 is installed.

I have made a double boot for Ubuntu 10.04.
Until now, all I can choose from is between a display from 640x480 or 800x600.
I know there were some problems with the new Nvidia drivers.

My question is: Are there any drivers available so i can get more options for the display.

I installed ubuntu 10.04 from the beginning and I updated every day when possible.


with regards,  Flip

---

### Post by shaka_zulu on 2010-04-24
Did you install video drivers? If yes which version?

---

### Post by flipflipsen on 2010-04-25
I do not know what you mean. I just installed ubuntu 10.04 and every day i updated until now.

When I want to adjust the display, i get the message that i have to use the drivers of the manufacturer. But they are not installed.

I troublesuited and if i use the hardware drivers, then after a restart, my screen starts white, then flashing, and then it starts to become black.It starts from the right side and going to become more and more black from the right to the left.

Then I have to restart into the safe graphics mode. Afterwards, everything works okay again, but only in 640x480 or 800x600.

with regards.

---

### Post by shaka_zulu on 2010-04-25
[http://www.ubuntu-how-to.com/2010/04/how-to-install-nvidia-driver-ubutnu.html](http://www.ubuntu-how-to.com/2010/04/how-to-install-nvidia-driver-ubutnu.html)

check here for solution.

---

### Post by flipflipsen on 2010-04-25
Hi, 

I've been there on the site, but the problem is, there is no driver available for Linux.

---

### Post by jrife0 on 2010-04-25
Does anybody know when Nvidia will release Linux drivers for the Nvidia Geforce 300m series, which includes the 330m? I was looking at their site and after a quick search found no results for a linux driver for this series of graphics cards. I didn't even find a beta version.

---

### Post by shaka_zulu on 2010-04-25
Do you have some driver recommended for your video card in Hardware drivers? Very strange that there are drivers for all other video cards but for 300M series there are no any of them.

---

### Post by jrife0 on 2010-04-25
The restricted drivers don't work for this series. The recommended driver causes you to boot into a black screen.

---

### Post by shaka_zulu on 2010-04-25
Just incredible. Try with googling a little bit. I hope you will find something.

---

### Post by jrife0 on 2010-04-25
I did find a workaround: [http://www.backtrack-linux.org/forums/backtrack-howtos/2714-installing-nvidia-330m-driver.html]("http://www.backtrack-linux.org/forums/backtrack-howtos/2714-installing-nvidia-330m-driver.html")

However, I am still hoping for a driver specifically for Linux as there seem to be some problems with the workaround such as brightness issues. I hope this helps though.

---

### Post by shaka_zulu on 2010-04-25
Well i believe they will make it fast because that is really embarrassing.

---

### Post by jrife0 on 2010-04-25
Hopefully in the next couple of months they will have a driver. I was looking forward to having Ubuntu on my new Vaio Z but then found out there is no driver support for my graphics card. Such a disappointment...
I guess I have to stick with Windows 7 until then :(

---

### Post by shaka_zulu on 2010-04-25
I believe that is more matter of days rather than months. Usually they are acting fast but i can understand your disappointment. I would be too.

---

### Post by jrife0 on 2010-04-25
After downloading the 190.53 nvidia driver directly from their site and installing it my 330m card seems to work. It doesn't say that 300m is supported but 200m is so I thought it was worth a try. Now my graphics are a nice 1600x900 on ubuntu :)

Link: [ftp://download.nvidia.com/XFree86/Linux-x86/190.53](ftp://download.nvidia.com/XFree86/Linux-x86/190.53)

Download: NVIDIA-Linux-x86-190.53-pkg0.run
Exit x Server
Navigate to where you downloaded NVIDIA-Linux-x86-190.53-pkg0.run and execute it as root. After rebooting it should work :)

---

### Post by flipflipsen on 2010-04-26
Hi, 

How do you exit x Server

And what is the command to execute the *NVIDIA-Linux-x86-190.53-pkg0.run* file?

with regards,

Flip

---

### Post by shaka_zulu on 2010-04-26
> **flipflipsen said:**
> Hi, 

How do you exit x Server

And what is the command to execute the *NVIDIA-Linux-x86-190.53-pkg0.run* file?

with regards,

Flip

You have complete tutorial here. 

[http://www.ubuntu-how-to.com/2010/04/how-to-install-nvidia-driver-ubutnu.html](http://www.ubuntu-how-to.com/2010/04/how-to-install-nvidia-driver-ubutnu.html)

---

### Post by flipflipsen on 2010-04-26
Hi,

I printed the whole tutorial and did exactly what it said.

Everything works as was written down.

But at the last reboot al I got was a black screen.

So I think I have to wait a little longer for a solution.

With regards, Flip

---

### Post by shaka_zulu on 2010-04-26
What graphic card do you have?

---

### Post by gianluca.pettinello on 2010-04-26
I'm a owner of Vaio F11 series too. Try to search in google vaio f11 linux. You will find a site with all the tricks to make ubuntu work fine

---

### Post by jrife0 on 2010-04-27
@flipflipsen: exit x server by typing 
sudo /etc/init.d/gdm stop
into a terminal. This will cause you to have just text on your screen. Log in again( you are prompted to do this). Then navigate to where you saved the driver NVIDIA-Linux-x86-190.53-pkg0.run file using the cd command. You don't need a command to execute the file. just type in the file name like so: ./NVIDIA-Linux-x86-190.53-pkg0.run. Also, if you are running 64 bit ubuntu you may want to try the drivers found here:
[ftp://download.nvidia.com/XFree86/Linux-x86_64/195.36.24/]("ftp://download.nvidia.com/XFree86/Linux-x86_64/195.36.24/")
instead of the one I previously mentioned.

---

### Post by flipflipsen on 2010-04-27
[SIZE=2][shaka_zulu,]("http://ubuntuforums.org/member.php?u=637072")[/SIZE]

My laptop is the Sony Vaio F series

My graphic card is the [B]Nvidia Geforce GT330M.

[/B]I started this thread.

with regards

Flip

---

### Post by flipflipsen on 2010-04-27
Hi,

I started with **sudo /etc/init.d/gdm stop**

Then I got the following message:

[I]rather than invoking init scripts through /etc/init.d, use the service( 8 ) utility, e.g. service gdm stop.

Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the stop( 8 ) utility, e.&#501;. stop gdm gdm stop/waiting.
[/I]
I think ever that the command worked, so i did the next command 
[B]
nvidia-uninstall[/B]

I got the message that nvidia is uninstalled, so this also worked.

Then for the next command **sudo sh ./NVIDIA-Linux-x86-190.53-pkg0.run**

It seems to be okay. The NVIDIA Installation program starts.

Now I got a message: *the distribution - provided pre-install script failed. Continue installation anyway.*

I can answer with yes or no. I choose yes.

Now the install program runs. When the installation is finished. I give the next command

**sudo reboot**

The computer restarts. and the result is a black screen.

I tried this several times, to be asure that i didn't make a failure, but the result is always the same.

with regards, Flip

---

### Post by guerillero on 2010-06-22
Hi,
this is the solution I am using since a while. It is a limited solution, though. 
 
[http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup](http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup)

---

