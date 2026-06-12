---
title: "installing ubuntu on a EVEREX SA2053T.. how i did it"
date: 2008-02-22
forum: Hardware &amp; Laptops
---

### Post by eldragon on 2008-02-22
most ideas of what went wrong i found here: [http://poplarware.com/everexlinux.html](http://poplarware.com/everexlinux.html)

there was another post on how to use the alternative install disk but i just lost it. if you find it let me know so due credit is added here.

first download the gutsy alternative install cd and just start the install as you would

when it starts loading drivers, hit alt-F2 to switch to a second terminal and navigate to
```

/lib/modules/[tab][tab]/drivers/net

```
and start trying to delete the file 8139too.ko until you succeed. (its going to be loaded from the cd. you might have to try a couple of times till its loaded onto the ramdrive

switch back to terminal 1 (alt-f1) and you will find an error about not finding a network adapter, thats fine, wireless will work anyway,

then once youve done that, follow the install procedure from alt+f1 (first terminal) until after the step of doing the harddisc formatting

when it starts copying the needed files. you have to delete from the tarket drive the card reader and ethernet modules so they dont get loaded after you boot the first time

for this. navigate to 
```

/target/lib/modules/[tab][tab]/drivers/net

```
and delete 8139too.ko again, just keep trying to get to that folder and deleting the file until you succeed.

then you have to do the same for the card reader, go to:
```

/target/lib/modules/[tab][tab]/drivers/mmc/host

```

and delete sdhci.ko

when youve done this, you can keep on with the install....

after the first reboot, before installing any driver.

you have to blacklist 8139too, mmc_core and sdhci (in that order)

to do this, run 
```

sudo gedit /etc/modprobe.d/blacklist

```

and append to the end of the file the following lines
```

blacklist 8139too
blacklist mmc_core
blacklist sdhci

```

make sure you have added them in that order, if you switch mmc_core and sdhci the computer wont be able to boot after updates.

the post above states that there was problems with keyboard, touchpad, screen resolution and wireless. and suggests solutions for those problems. i havent experienced them, so i didnt have to do any further tweaking.

if you wish to have ethernet working, there is tons of info about doing so but it involves recompiling the kernel and setting 8139too to PIO mode. i dont know how to do this, so im just stuck with wireless. no big deal. 

if anyone knows how to get the card reader working, id appreciate that, since i was planning to move my boot partition to it :D will have to wait.

if i missed something, just let me know, i'll add corrections :D


EDIT
apparently, the rt73usb kernel module doesnt work as well as i thought it would, so i ended up with a dodgy connection from time to time. which led to reboots.

i found a solution to the problem, which involves compiling the serialmonkey driver. since its in [spanish]("http://wiki.ubuntuparatodos.org/wiki/index.php/Driver_linux_chip_rt73_(conceptronic_c54ru,_etc.)"), ill translate

first make sure you downloaded all the needed stuff to compile and load the driver:
```

sudo apt-get install build-essential linux-headers-`uname -r`

```

and 
```

~$ wget http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz

```

then we remove the dodgy module

```

sudo rmmod rt73usb

```

and we make sure its not going to be loaded again (dont know if this is needed, but just in case

```

sudo gedit /etc/modprobe.d/blacklist

```

and append "blacklist rt73usb" to the end of the file. save and close

now we have to unpack the new driver
```

tar -xvzf rt73-cvs-daily.tar.gz

```
and we get into the module's folder
```

cd rt73[tab]/Module

```

now its compiling time!!

```

make
strip -S rt73.ko
sudo make install
sudo modprobe rt73
sudo ifconfig wlan0 up


```

only catch is that the gnome network manager cant see our newly built driver, so you must set the a manual network or add your info to /etc/network/interfaces

this did it for me.

cheers

you could install from the repositories rutilt and use it to configure your wlan with a gui, works quite well.

just remember to remove the gnome network manager, it screws things up.

---

