---
title: "So close to installing nvidia driver"
date: 2009-07-07
forum: Hardware
---

### Post by bguy on 2009-07-07
Hi,
Long time Ubuntu enthusiast.  I've managed to get all of the hardware recognised and working without trouble but the nvidia graphics card driver is still giving my trouble.  When i install the driver recommended for my quadro nvs 440 (Im only rinning 1 monitor and do not intend to run more)i do the cntrl alt f2 trick to get to the command line (i think this is what it does) and then login as root and then disable the xserver by doing the following /etc/init.d/gdm stop and then the driver installs (it took me forever to get to this point) So it asks me a couple questions about updating some file and i tell it to go ahead and do it.  So far so good.  It then bumps me back to the command line prompt where i do the init start thingy.  WHen i reboot im still at the command line and it will not enter ubuntu.  Can someone help me out.  I'm so close to victory.  BTW im writing this message after reinstalling the OS again.  Im using ubuntu 9.1 x64
B

---

### Post by bguy on 2009-07-07
I should add that there was a message saying something relating to the graphics car, if not the graphics card itself, failed.

---

### Post by bguy on 2009-07-07
I've also tried using the ones ubuntu itself suggests under the new hardware drivers thing and on reboot i get to the command line and cannot enter ubuntu.

---

### Post by wojox on 2009-07-07
Have you read this?

[http://ubuntuguide.org/wiki/Ubuntu:Jaunty#Install_Latest_Nvidia.2FATI_drivers](http://ubuntuguide.org/wiki/Ubuntu:Jaunty#Install_Latest_Nvidia.2FATI_drivers)

---

### Post by bguy on 2009-07-07
> **bguy said:**
> I should add that there was a message saying something relating to the graphics car, if not the graphics card itself, failed.

this message came up post install.  The install process itself seemed to go off without a hitch.

---

### Post by bguy on 2009-07-07
> **wojox said:**
> Have you read this?

[http://ubuntuguide.org/wiki/Ubuntu:Jaunty#Install_Latest_Nvidia.2FATI_drivers](http://ubuntuguide.org/wiki/Ubuntu:Jaunty#Install_Latest_Nvidia.2FATI_drivers)

I downloaded it to the Desktop and then ran it via the command line from the Desktop.  It looks like i should be moving the driver to the home directory and running it there?  Is that right?  Do i have to  create a directory in the home folder specifically for the driver?

---

### Post by bguy on 2009-07-07
> **wojox said:**
> Have you read this?

[http://ubuntuguide.org/wiki/Ubuntu:Jaunty#Install_Latest_Nvidia.2FATI_drivers](http://ubuntuguide.org/wiki/Ubuntu:Jaunty#Install_Latest_Nvidia.2FATI_drivers)

sudo killall gdm gets me  gdm: no process found

---

### Post by bguy on 2009-07-07
> **bguy said:**
> sudo killall gdm gets me  gdm: no process found

I just went to synaptic and apparently gdm is installed

---

### Post by bguy on 2009-07-07
> **bguy said:**
> I just went to synaptic and apparently gdm is installed

btw cntrl alt f1 doesnt do anything for me only cntrl alt f2 takes me to the command line.

we're so close i can feel it

---

### Post by bguy on 2009-07-07
so the killall gdm didnt work so i tried the etc/init.d/gdm stop and it said that the display thingy was stopped.  I then initiated the install which then said that no pre compiled kernel was found to match your kernel.  It then asked me if i wanted to try to download one which failed and then i requested that it compile one for me.  It said building kernel module and then the nvidia installer said it was unable to install and i rebooted.  Any help would be appreciated.  THanks,
B

---

### Post by cmike2 on 2009-07-07
I was able to install nvidia drivers just today. I seem to have lost the link to the guide...

To have the nvidia drivers compile a kernel module, you need the linux headers of your kernel.

to find your kernel version, use this terminal command
```
uname -r
```
then install the header for your version
```
sudo apt-get install linux-headers-<kernel version>
```

for example, my kernel version is 2.6.24-24-generic, so I used this command:
```
sudo apt-get install linux-headers linux-headers-2.6.24-24-generic
```

(I installed linux-headers package too because I wasn't sure). Hope that at least helps you compile the kernel module.

---

### Post by bguy on 2009-07-07
thanks for responding cmike
i tried what you said and got the following output
me@ubuntu:~$ uname -r
2.6.31-2-generic
me@ubuntu:~$ sudo apt-get install linux-headers linux-headers-2.6.31-2-generic
[sudo] password for me: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers is a virtual package provided by:
  linux-headers-2.6.29.5-2-rt 2.6.29.5-2.3
  linux-headers-2.6.29.5-1-rt 2.6.29.5-1.2
  linux-headers-2.6.29-1-rt 2.6.29-1.1
  linux-headers-2.6.28-3-rt 2.6.28-3.12
  linux-ports-headers-2.6.30-2 2.6.30-2.4
  linux-headers-2.6.31-2-server 2.6.31-2.16
  linux-headers-2.6.31-2-generic 2.6.31-2.16
  linux-headers-2.6.31-2 2.6.31-2.16
  linux-headers-2.6.31-1-server 2.6.31-1.14
  linux-headers-2.6.31-1-generic 2.6.31-1.14
  linux-headers-2.6.31-1 2.6.31-1.14
  linux-headers-2.6.30-9-server 2.6.30-9.10
  linux-headers-2.6.30-9-generic 2.6.30-9.10
  linux-headers-2.6.30-9 2.6.30-9.10
  linux-headers-2.6.30-10-server 2.6.30-10.12
  linux-headers-2.6.30-10-generic 2.6.30-10.12
  linux-headers-2.6.30-10 2.6.30-10.12
You should explicitly select one to install.
E: Package linux-headers has no installation candidate
me@ubuntu:~$ 

Do you know where i go from here?
Thanks again,
B

---

### Post by bguy on 2009-07-07
I tried,
sudo apt-get install linux-headers linux headers-2.6.31-2-generic 2.6.31-2.16

and got the following

You should explicitly select one to install.
E: Package linux-headers has no installation candidate

I think if i could sort this one issue out i could get the driver in.
So close yet so far.  I swear i've been trying to get this driver in for months.  If you look at my other posts i struggled to get the driver in a few months ago and ended up giving up and going back to windows.  
grrrr

---

### Post by bguy on 2009-07-07
here is the latest 

me@ubuntu:~$ sudo apt-get install linux-headers-2.6.31-2-genericReading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.31-2-generic is already the newest version.
linux-headers-2.6.31-2-generic set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

am i good to go?

---

### Post by wojox on 2009-07-07
Can you access nvidia x server settings?

---

### Post by bguy on 2009-07-07
I don't know how to do that.

---

### Post by bguy on 2009-07-07
do the headers get installed during a normal install?  i don't know if i installed them personally or if they were installed with the default install

---

### Post by bguy on 2009-07-07
Thanks for the help

---

### Post by cmike2 on 2009-07-07
Hmm...if you already have the linux headers you should be able to compile the kernel module during the nvidia driver installation. What is the error message that comes up when installing drivers?

---

