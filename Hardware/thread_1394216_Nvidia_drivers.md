---
title: "Nvidia drivers"
date: 2010-01-30
forum: Hardware
---

### Post by Klitsie on 2010-01-30
Hi all,

I'm pretty new to linux and ubuntu. 
I installed ubuntu on my laptop, wich has a nvidia m9600gt on board.
I was trying to enable the desktop effects, but couldnt do this.
So I figured i needed to install some graphics drivers.
I downloaded the drivers from the offical nvidia site.
Its a .run file, but i can't seem to run it
I tried: sudo sh nvidia.run
Got this message: can't open nvidia.run

It is located on my desktop, do i need to put something in front, like desktop/nvidia.run?
Or is there something else i need to do.
I search the forums, and tried something with chmod, but that didnt work aswell.

Please help,
Regard, Bob

---

### Post by chewearn on 2010-01-31
To install nvidia driver, go to:
Top Panel Menu > System > Administration > Hardware Drivers

A dialogbox should open with a list of available drivers.  Select one (probably the recommended one).

---

### Post by gradinaruvasile on 2010-01-31
Well its not that simple. You have to chmod +x.
First you have to stop the graphical server:

press ctrl+alt+f1, login 

Stop the graphical server:

sudo service gdm stop

Then go to the drivers folder:

cd /path/to/driver

Make the installer executable, otherwise it wont run:

chmod + x drivername

sudo ./drivername

Then start the graphical server:


sudo service gdm start

---

### Post by chewearn on 2010-01-31
He is new to Ubuntu/Linux.  It's best to recommend the restricted driver method for installing nvidia driver.  That way, he wouldn't have to deal with "out of repository" issues later on.

---

### Post by Klitsie on 2010-01-31
> **chewearn said:**
> To install nvidia driver, go to:
Top Panel Menu > System > Administration > Hardware Drivers

A dialogbox should open with a list of available drivers.  Select one (probably the recommended one).

Thanks for the reply.
I tried this, but i get a dialogbox with : No proprietary drivers are in use on this system.



> **gradinaruvasile said:**
> Well its not that simple. You have to chmod +x.
First you have to stop the graphical server:

press ctrl+alt+f1, login 

Stop the graphical server:

sudo service gdm stop

Then go to the drivers folder:

cd /path/to/driver

Make the installer executable, otherwise it wont run:

chmod + x drivername

sudo ./drivername

Then start the graphical server:


sudo service gdm start

Also thanks for the reply. Did not tried this yet.
If I press ctr+alt+f1, how do i get out of that function?
Also, the drivername is nvidia.run and is located on my desktop.
What is the path? is it username/desktop ?

---

### Post by chewearn on 2010-01-31
> **Klitsie said:**
> Thanks for the reply.
I tried this, but i get a dialogbox with : No proprietary drivers are in use on this system.

That's odd.  Can you post the output from this command.
```
lshw -c display
```

This will show the exact graphics hardware detected by Ubuntu.

---

### Post by 5au1 on 2010-02-04
Hi,

I've installed the driver for a Nvidia Geforce2 Mx 400 video card following the method described by gradinaruvasile, however after updating the system (including the kernel, from 2.6.31-14 to 2.6.31-16) I need to re-install the driver again. To my surprise, the commands: ```
sudo service gdm stop
``` or ```
sudo stop gdm
``` don't work anymore, I get the following, ```
stop: Unknown instance
``` This is strange because with the previous kernel (2.6.31-14) I didn't have such problem.

What can I do?

Thanks in advance

---

### Post by chewearn on 2010-02-04
Up to Ubuntu Intrepid, it was...

Stop:
```
sudo /etc/init.d/gdm stop
```

Start:
```
sudo /etc/init.d/gdm start
```

Restart:
```
sudo /etc/init.d/gdm restart
```

Has it change in Jaunty and Karmic?

---

### Post by sandy8925 on 2010-02-04
It's changed in Karmic. I don't know whether you can use the old method (/etc/init.d/gdm) anymore although it's still there. I also have an Nvidia 6600 GT on my desktop and that wasn't detected by Karmic either. Going to try installing the nvidia driver. By the way I've been using the gdm stop , install driver,gdm start method for a long time and it works well.

---

### Post by jstateson on 2010-02-13
Hi

I found this thread via google as I have 2 similar problems

1 - difficulty stopping gdm so as to install / reinstall nvidia driver and

2 - gpu not always recognized on subsequent reboots.

I did a clean install of 9.1 replacing a 8.04 after I added a GTS-250 nvidia card.  I have 190.53 and got the build essentials and the ia32 libraries.  Attempting the nvidia install I quickly ran into the problem of stopping the gdm.

Unaccountably, "sudo su" cannot be used to both stop the gdm and start the nvidia install.  I consistently got "unknown instance" and discovered that only

sudo stop gdm
and
sudo ./NVIDIA-linux-64-190-53-whatever.sh 
were required and I could not operate out of "sudo su" like I normally do.

Anyway, out of 5 boots there were 3 that the gpu was not found

I just did my first upgrade of 9.1 (200 or so files) and had the same problem: "sudo su" not allowing a stop of gdm nor an install of the NVIDIA stuff.

After getting the install to finally work, it took 3 reboots before the gpu was recognized.

By 3 reboots I mean that the deskop came up fine, the driver was working, but BOINC 6.10.32 reported a missing GPU device.  After the 3rd reboot (shutdown and power off), the GPU was seen by BOINC.

It would be nice if the SUDO SU stuff could be used as that is convenient.

---

