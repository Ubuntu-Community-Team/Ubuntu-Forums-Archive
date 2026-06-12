---
title: "Screen resolution issue...nvidia"
date: 2008-12-20
forum: Hardware
---

### Post by hunges on 2008-12-20
First off I am a complete nube with any and all Linux OS

In order to even post this I had to deactivate nvidia. The most resolution it will allow is 640x480. After deactivation i can get a max of 800x600 which is not acceptable.How do I get this working properly?????

---

### Post by taurus on 2008-12-20
What kind of nVidia card do you have?  Look in System -> Administration -> Hardware Drivers to see if your card is on the list.  You can install a driver from there.

---

### Post by hunges on 2008-12-20
"No proprietory driver are in use on this system
.........
.........
nvidia accelerated graphics driver (version 96)"

I activate driver,it downloads. I reboot and the resolution gets even worse-- 640x480

---

### Post by hunges on 2008-12-20
I believe i have NVIDIA GeForce 200 series

---

### Post by hunges on 2008-12-20
I downloaded driver from NVIDIA

NVIDIA-Linux-x86-177.82-pkg1.run

It downloads to desktop.I then go to terminal and type(per directions)

sh NVIDIA-Linux-x86-177.82-pkg1.run

and i get this

Can't open NVIDIA-Linux-x86-177.82-pkg1.run

Sorry... I am a complete newb

---

### Post by taurus on 2008-12-20
Make sure that is the right driver for your graphic card or it could crash your X server.  Otherwise, you can install it with

```
cd ~/Desktop
chmod 755 NVIDIA-Linux-x86-177.82-pkg1.run
sudo ./NVIDIA-Linux-x86-177.82-pkg1.run
```

---

### Post by hunges on 2008-12-20
>  ERROR: Installation has failed.  Please see the file
         '/var/log/nvidia-installer.log' for details.  You may find         
         suggestions on fixing installation problems in the README          
         available on the Linux driver download page at [www.nvidia.com](www.nvidia.com). 

???

---

### Post by taurus on 2008-12-20
What does it say in the log?

```
more /var/log/nvidia-installer.log
```
Hit the space bar for the next 24 lines.

---

### Post by hunges on 2008-12-20
back to your previous post. I enter code as you decribe. I enter password. I then get:

  > WARNING: You do not appear to have an NVIDIA GPU supported by the 177.82     
           NVIDIA Linux graphics driver installed in this system.  For further 
           details, please see the appendix SUPPORTED NVIDIA GRAPHICS CHIPS in 
           the README available on the Linux driver download page at           
           [www.nvidia.com](www.nvidia.com).


I then get:

> ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at [www.nvidia.com](www.nvidia.com).

Then I get the error from my previous post

---

### Post by taurus on 2008-12-20
> 
WARNING: You do not appear to have an NVIDIA GPU supported by the 177.82
NVIDIA Linux graphics driver installed in this system. For further
details, please see the appendix SUPPORTED NVIDIA GRAPHICS CHIPS in
the README available on the Linux driver download page at
[www.nvidia.com](www.nvidia.com). 

It means that the driver that you try to install doesn't support your nVidia card.

```
lspci | grep VGA
```

---

### Post by holy_reds on 2008-12-20
> WARNING: You do not appear to have an NVIDIA GPU supported by the 177.82 
NVIDIA Linux graphics driver installed in this system. For further 
details, please see the appendix SUPPORTED NVIDIA GRAPHICS CHIPS in 
the README available on the Linux driver download page at 
[www.nvidia.com](www.nvidia.com).
Are u sure downloading the right driver?

> ERROR: You appear to be running an X server; please exit X before 
installing. For further details, please see the section INSTALLING 
THE NVIDIA DRIVER in the README available on the Linux driver 
download page at [www.nvidia.com](www.nvidia.com)
Here is the manual installation guide if those are the right driver:

1.After downloading, place the package in /home

2.Disable X server by typing (write no.3,4,5 in a note first):
  ```
sudo /etc/init.d/gdm stop
```

3.Press Alt+F2(or any of your terminal shortcut) in those black screen then enter username&password

4.Install the driver by typing:
  ```
sudo sh NVIDIA-Linux-x86-177.82-pkg1.run
```
  Select yes to every selection if you are not sure

5.Enable X server by typing:
  ```
sudo /etc/init.d/gdm start
```

---

### Post by hunges on 2008-12-20
> ryan@ryan-desktop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev a2)
ryan@ryan-desktop:~$ 

Now what?

Thanks for helping. I will be able to learn a lot of this stuff on my own if I could get this fixed and be able to read web pages. 640x480 sucks

---

### Post by hunges on 2008-12-20
so it appears i have GeForce4 MX series

I downloaded the correct driver from nvidia and followed there install:

> ryan@ryan-desktop:~$ sh NVIDIA-Linux-x86-96.43.07-pkg1.run
sh: Can't open NVIDIA-Linux-x86-96.43.07-pkg1.run
ryan@ryan-desktop:~$

---

### Post by taurus on 2008-12-20
You have to be in the same directory where you saved the file.  Press <Ctrl><Alt>F2 and log in with your username and password.  Then, stop gdm GUI login screen with

```
sudo /etc/init.d/gdm stop
cd ~/Desktop
chmod +x NVIDIA-Linux-x86-96.43.07-pkg1.run
sudo ./NVIDIA-Linux-x86-96.43.07-pkg1.run
startx
```
Does X start when you run the last command?

---

### Post by hunges on 2008-12-20
I diabled X server per holy reds

followed his instructions to step 4 when i got an error

so i then used  

sudo /etc/init.d/gdm start

When it came back to log in it was working!!!!!!

Running at 1280x1024

I am afraid to reboot.... any way to be sure the settings stay put?

---

### Post by taurus on 2008-12-20
You won't know whether the new nvidia driver loads/works until you reboot.  Sooner or later, you have to reboot so might as well find out sooner rather than later.

---

### Post by hunges on 2008-12-20
LOST IT!!!!!!!!!!

I want to cry

should i try holy reds solution again?

How do I...
> 1.After downloading, place the package in /home

---

### Post by hunges on 2008-12-20
ok.. figured out the /home

i ran holy reds solution to a t

Things looked promising until it said it needed to build a kernel?

I then got an 
> error: Unable to build the kernal module.......

then:

> error installation has failed. please see the file
'/var/log/nividia-installer.log'

where do i go from here????:confused:
thanks again

---

### Post by holy_reds on 2008-12-20
hmm...maybe your nvidia driver kinda outdated and it can't build kernel module...

check these 2 links, maybe it can help:

[http://ubuntuforums.org/archive/index.php/t-385829.html](http://ubuntuforums.org/archive/index.php/t-385829.html)

[http://ubuntuforums.org/showpost.php?p=4558708&postcount=37](http://ubuntuforums.org/showpost.php?p=4558708&postcount=37)

---

### Post by hunges on 2008-12-20
could someone explain this process for a dumb newb, thanks.

> 
1. Go to your source location and run make menuconfig
2. Under "Processor type and features" turn "Paravirtualization Support" OFF
3. Exit and save the config.
4. Run make prepare
5. Re-run the NVIDIA Installer
6. Profit.

---

### Post by holy_reds on 2008-12-20
Well I dunno either,lol...

Here is someone using the similar driver:
[http://www.nvnews.net/vbulletin/showthread.php?t=122695](http://www.nvnews.net/vbulletin/showthread.php?t=122695)

Try download the same beta driver to be sure...

---

