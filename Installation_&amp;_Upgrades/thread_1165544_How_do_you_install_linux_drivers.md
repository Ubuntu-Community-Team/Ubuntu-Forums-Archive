---
title: "How do you install linux drivers?"
date: 2009-05-20
forum: Installation &amp; Upgrades
---

### Post by Adam25 on 2009-05-20
I downloaded a driver for my usb wifi at [http://www.ralinktech.com](http://www.ralinktech.com).

I extraced it but have no idea how to run it. Thanks for the help.

---

### Post by stillious on 2009-05-20
What kind of file is it? i.e. .deb .tar.gz etc

---

### Post by Adam25 on 2009-05-20
It is a tgz file.

---

### Post by stillious on 2009-05-20
It might be best if you have a read of this, first :)

[http://www.tuxfiles.org/linuxhelp/softinstall.html]("http://www.tuxfiles.org/linuxhelp/softinstall.html")

---

### Post by Adam25 on 2009-05-20
Ok i see this,

< The procedure >
The installation procedure for software that comes in tar.gz and tar.bz2 packages isn't always the same, but usually it's like this:

# tar xvzf package.tar.gz (or tar xvjf package.tar.bz2)
# cd package
# ./configure
# make
# make install

If you're lucky, by issuing these simple commands you unpack, configure, compile, and install the software package and you don't even have to know what you're doing. However, it's healthy to take a closer look at the installation procedure and see what these steps mean.


Ok the file is on my desktop and is named "2009_0424_rt2870_linux_sta_b2.1.1.0.tgz" useing those commands what would i type in to make the files?

Im totally new to ubuntu and honestly only reason im using it is windows wont install on the pc its on for some reason. So we tryed it and just basicly want to web browse and the network card dont work. So we bought a usb wifi adapter and cant get it set up.

---

### Post by Mark Phelps on 2009-05-20
Basically, you enter the commands listed (following the "#") in a terminal, one at a time.

Open a terminal by clicking on Applications (upper left of screen), and selecting Accessories --> Terminal.

Notice the prompt is a dollar sign.  That means that you're NOT running as root.  The terminal defaults to your user /home directory, so once in the terminal, enter "cd Desktop".  Then, enter "ls -l" to see the list of files.  Your .tgz file should be shown.

To switch over to root, enter "sudo -i" and supply your password.  Notice that the prompt now switches to "#" (which is NOT a "pound sign", but everyone calls it that).  This means that you're running as root.

From there, enter the commands in the list, one at a time.

---

### Post by cariboo on 2009-05-20
That driver is already included with the kernel. Open an Applications-->Accessories-->Terminal and type:

```
sudo lshw -C network
```

the above command will list all the details of your network devices including if the driver is loaded.

---

### Post by Adam25 on 2009-05-20
It dose list 2, one my nic wich dosent work so i dont see how its showing up its even disabled in the bios. But lets see, we have 2 showing but both say ethernet id 1 & 2 1 is eth 4 2 is pan0. the second one says disabled. 1 shows as a 3com so that has to be the onboard nic that wasent working. And the usb is a belkin.

Now that being said back to compiling the driver,

The driver file is located at,
-rw-r--r-- 1 marie marie 662852 2009-05-18 14:07 2009_0424_RT2870_Linux_STA_V2.1.1.0.tgz

I tryed,
# tar xvzf package.tar.gz -rw-r--r-- 1 marie marie 662852 2009-05-18 14:07 2009_0424_RT2870_Linux_STA_V2.1.1.0.tgz

# tar xvzf 1 marie marie 662852 2009-05-18 14:07 2009_0424_RT2870_Linux_STA_V2.1.1.0.tgz
 
# tar xvzf 662852 2009-05-18 14:07 2009_0424_RT2870_Linux_STA_V2.1.1.0.tgz

# tar xvzf  2009_0424_RT2870_Linux_STA_V2.1.1.0.tgz

I also tryed the save variants with the tar xvjf and they all say no such directory or file.

Also lsusb shows " Bus 001 Device 002: ID 050d:935a Belkin components. NDISwrapper dose say the driver is installed but all i ever did was use the windows wireless driver and load the inf file from the desktop where the inf file and the driver was located. Either way i cant get it to work or show it as being there.

---

### Post by Mark Phelps on 2009-05-21
I'm hoping I misread your response, but it looks like you tried to do the tar command using the complete file info.

You only supply the filename, not the other stuff as well.  Sample command would be "tar xvzf 2009_0424_*.tgz".  

Don't do tar after tar, only do one tar and follow with the other commands in the list (in Adam25's post).

---

