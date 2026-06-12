---
title: "eee PC 1005ha internet"
date: 2009-09-13
forum: Hardware
---

### Post by Fizban140 on 2009-09-13
For the past four days I have been attempting to get UNR working on my 1005ha. I have been running into problem after problem and this is the only one I can't fix.  I followed  [http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/](http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/) that guide and when I did the wireless part wired stopped working. How do I get both working?  Also how do I get flash working without blowing up my netbook?

---

### Post by rob-ward on 2009-09-14
Once you have upgraded the kernel you have to recompile the ethernet drivers, have you done this?

If not you need to get the drivers again from [http://www.jfwhome.com/wp-content/uploads/2009/08/atheros-wired-driver-1005ha-linux.zip](http://www.jfwhome.com/wp-content/uploads/2009/08/atheros-wired-driver-1005ha-linux.zip)

Once you have got teh driver you need to extract it, then you need to run the following commands(inside the extracted folder:

```
sudo rmmod atl1e.ko
```

that removes the old module

```
make
```

```
make install
```

```
sudo insmod atl1e.ko
```

Let me know if that works, as soon as I get home I will check my ethernet still works on mine.

---

### Post by Fizban140 on 2009-09-14
Run it inside the folder? I have no idea what this means, what exactly do I type into the terminal? Everything I did before, or only the last two lines?

---

### Post by rob-ward on 2009-09-14
> **Fizban140 said:**
> Run it inside the folder? I have no idea what this means, what exactly do I type into the terminal? Everything I did before, or only the last two lines?

Sorry, what I meant was that once you have extracted the zip into a directory, say you call it atherosdrivers, you cd into the directory containing the extracted files and then cd into the source directory(src), once inside there you need to run the 4 commands that I listed, the first command makes sure that the current ethernet module is removed, the second makes the new module that will use the new kernel info, the third installs the module and the 4th activates it.

Let me know how you get on.

---

### Post by rob-ward on 2009-09-14
What I just said may still be unclear, maybe this will be clearer to understand, if you open a terminal and just run these commands in order it should work for you:

```
mkdir atherosdrivers
```
```
cd atherosdrivers
```
```
 wget http://www.jfwhome.com/wp-content/uploads/2009/08/atheros-wired-driver-1005ha-linux.zip
```
```
unzip atheros-wired-driver-1005ha-linux-zip
```
```
cd src
```
```
sudo rmmod atl1e.ko
```
```
make
```
```
sudo make install
```
```
sudo insmod atl1e.ko
```

Them commands should do all of the work for you, they will download the driver, extract it move to the correct directory, remove the old drive, make and install the newone and activate it.

Once you have run them you should be good to go(you may require a reboot)

Hope that get you sorted, any problems let me know.

---

### Post by Fizban140 on 2009-09-14
> **rob-ward said:**
> What I just said may still be unclear, maybe this will be clearer to understand, if you open a terminal and just run these commands in order it should work for you:

```
mkdir atherosdrivers
``````
cd atherosdrivers
``````
 wget http://www.jfwhome.com/wp-content/uploads/2009/08/atheros-wired-driver-1005ha-linux.zip
``````
unzip atheros-wired-driver-1005ha-linux-zip
``````
cd src
``````
sudo rmmod atl1e.ko
``````
make
``````
sudo make install
``````
sudo insmod atl1e.ko
```Them commands should do all of the work for you, they will download the driver, extract it move to the correct directory, remove the old drive, make and install the newone and activate it.

Once you have run them you should be good to go(you may require a reboot)

Hope that get you sorted, any problems let me know.For some reason I do that and when I reboot none of it works.

---

### Post by rob-ward on 2009-09-15
aah, by the sounds of it the module isn't loading on startup, to fix that you will need to add it to the file /etc/modules

to do that enter this command

```
sudo gedit /etc/modules
```

then at the bottom of the file you need to add this line

```
atl1e
```

Now whenever your computer reboots you will have the ethernet drivers loaded.

---

### Post by jon0051 on 2009-09-20
How did you install, i have some computer, and I have ubuntu downloaded to flash, but there are no instructions on how to install???

---

