---
title: "Agere et131x driver now on sourceforge"
date: 2006-10-12
forum: Hardware &amp; Laptops
---

### Post by rla3rd on 2006-10-12
I just finished helping dadams1969 of [http://dadams1969.googlepages.com/et131xkernelmodule](http://dadams1969.googlepages.com/et131xkernelmodule) migrate the driver source to sourceforge with patches already applied to run on newer 2.6 kernels.  It now works on edgy :).  The driver can be found here [http://sourceforge.net/projects/et131x](http://sourceforge.net/projects/et131x).

To build the driver on edgy:

1.  install linux headers and source
```

sudo apt-get install linux-headers-$(uname -r)
sudo apt-get install linux-image-$(uname -r)

```

2. download the source 
```

wget http://osdn.dl.sourceforge.net/sourceforge/et131x/et131x.1.2.2.src.tar.gz

```

3. move file to the your target directory of choice and extract
```

tar zxvf et131x.1.2.2.src.tar.gz

```

4. cd to driver directory
```

cd et131x

```

5. build and install the driver
```

sudo make && make modules_install
sudo depmod -a
sudo modprobe et131x

```

Enjoy!

---

### Post by tmogeem on 2007-05-23
> **rla3rd said:**
> I just finished helping dadams1969 of [http://dadams1969.googlepages.com/et131xkernelmodule](http://dadams1969.googlepages.com/et131xkernelmodule) migrate the driver source to sourceforge with patches already applied to run on newer 2.6 kernels.  It now works on edgy :).  The driver can be found here [http://sourceforge.net/projects/et131x](http://sourceforge.net/projects/et131x).

To build the driver on edgy:

1.  install linux headers and source
```

sudo apt-get install linux-headers-$(uname -r)
sudo apt-get install linux-image-$(uname -r)

```

2. download the source 
```

wget http://osdn.dl.sourceforge.net/sourceforge/et131x/et131x.1.2.2.src.tar.gz

```

3. move file to the your target directory of choice and extract
```

tar zxvf et131x.1.2.2.src.tar.gz

```

4. cd to driver directory
```

cd et131x

```

5. build and install the driver
```

sudo make && make modules_install
sudo depmod -a
sudo modprobe et131x

```

Enjoy!

when i did that, everything went fine, except the last command, this is what i got

FATAL: Module et131x not found.

what now plz?

---

### Post by tmogeem on 2007-05-23
never mind .. got everything working 

> insmod et131x.ko
> depmod
> modprobe et131x

---

### Post by McTek on 2007-05-24
I followed the directions below and I'm up and running thanks to McLois.

---

### Post by McLois on 2007-05-30
Ubuntu 7.04   This is how I solved (total n00b solution since I'm totally n00b * )

First got the latest download from the website ([http://sourceforge.net/project/platformdownload.php?group_id=179406](http://sourceforge.net/project/platformdownload.php?group_id=179406))

Then followed everything and the change point was:

sudo make && **sudo** make modules_install

the second use of sudo seems to avoid that strange error during compiling.
Now I see the gigabit ethernet card. Nice that this worked with a et131x on Express card!!! (on a Dell xps1210).

Hope it can help others!:popcorn:





* = I never liked linux before, too much time to learn commands, no drives, no software and so on (I'm a Windowz man), however I got really impressed by Ubuntu (I installed 2 days ago) and now I start to love it! Great Job to all the staff!!!

---

### Post by McTek on 2007-05-31
This post needs to be upgraded.

---

### Post by noctis_vulpes on 2007-07-03
A strange thing... When I try this, I get like, over 100 lines of error.

> vulpes@vulpes-laptop:~$ cd '/home/vulpes/et131x_20060131_v1-2-2/et131x/linux/driver' 
vulpes@vulpes-laptop:~/et131x_20060131_v1-2-2/et131x/linux/driver$ sudo make
Password:
#@make -C /lib/modules/2.6.20-15-generic/build M=/home/vulpes/et131x_20060131_v1-2-2/et131x/linux/driver modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/vulpes/et131x_20060131_v1-2-2/et131x/linux/driver/et131x_main.o
In file included from /home/vulpes/et131x_20060131_v1-2-2/et131x/linux/driver/et131x_main.c:79:
/home/vulpes/et131x_20060131_v1-2-2/et131x/linux/driver/et131x_version.h:85:26: error: linux/config.h: No such file or directory
In file included from /home/vulpes/et131x_20060131_v1-2-2/et131x/linux/driver/ET1310_common.h:89,
                 from /home/vulpes/et131x_20060131_v1-2-2/et131x/linux/driver/ET1310_phy.h:90,
                 from /home/vulpes/et131x_20060131_v1-2-2/et131x/linux/driver/et131x_main.c:111:
/home/vulpes/et131x_20060131_v1-2-2/et131x/linux/driver/ET1310_address_map.h:115:9: warning: "_BIT_FIELDS_HTOL" is not defined

... ((Like, 80 lines of this same thing... Only difference is the number after address_map.h))

/home/vulpes/et131x_20060131_v1-2-2/et131x/linux/driver/ET1310_address_map.h:3100:9: warning: "_BIT_FIELDS_HTOL" is not defined
In file included from /home/vulpes/et131x_20060131_v1-2-2/et131x/linux/driver/et131x_adapter.h:84,
                 from /home/vulpes/et131x_20060131_v1-2-2/et131x/linux/driver/et131x_main.c:116:
/home/vulpes/et131x_20060131_v1-2-2/et131x/linux/driver/ET1310_tx.h:99:13: warning: "_BIT_FIELDS_HTOL" is not defined
/home/vulpes/et131x_20060131_v1-2-2/et131x/linux/driver/ET1310_tx.h:195:9: warning: "_BIT_FIELDS_HTOL" is not defined
In file included from /home/vulpes/et131x_20060131_v1-2-2/et131x/linux/driver/et131x_adapter.h:85,
                 from /home/vulpes/et131x_20060131_v1-2-2/et131x/linux/driver/et131x_main.c:116:
/home/vulpes/et131x_20060131_v1-2-2/et131x/linux/driver/ET1310_rx.h:138:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/vulpes/et131x_20060131_v1-2-2/et131x/linux/driver/ET1310_rx.h:169:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/vulpes/et131x_20060131_v1-2-2/et131x/linux/driver/ET1310_rx.h:245:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/vulpes/et131x_20060131_v1-2-2/et131x/linux/driver/ET1310_rx.h:284:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/vulpes/et131x_20060131_v1-2-2/et131x/linux/driver/ET1310_rx.h:315:9: warning: "_BIT_FIELDS_HTOL" is not defined
In file included from /home/vulpes/et131x_20060131_v1-2-2/et131x/linux/driver/et131x_adapter.h:85,
                 from /home/vulpes/et131x_20060131_v1-2-2/et131x/linux/driver/et131x_main.c:116:
/home/vulpes/et131x_20060131_v1-2-2/et131x/linux/driver/ET1310_rx.h:441: warning: ?&#49258;mem_cache_t??is deprecated
/home/vulpes/et131x_20060131_v1-2-2/et131x/linux/driver/et131x_main.c:140: error: expected ????before string constant
/home/vulpes/et131x_20060131_v1-2-2/et131x/linux/driver/et131x_main.c:141: error: expected ????before string constant
make[2]: *** [/home/vulpes/et131x_20060131_v1-2-2/et131x/linux/driver/et131x_main.o] Error 1
make[1]: *** [_module_/home/vulpes/et131x_20060131_v1-2-2/et131x/linux/driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [modules] Error 2
vulpes@vulpes-laptop:~/et131x_20060131_v1-2-2/et131x/linux/driver$ 

... any idea what I might do to correct this? It didn't do this the last time I tried installing Ubuntu on this very same computer and it's driving me up the wall. Nothing changed save for the partitioning (wanted to give Ubuntu more space)... any help will be appreciated

---

### Post by undertakingyou on 2007-08-09
To overcome this go to the sourceforge page.  Download the newest version, which is 1.2.3; this has the patches for the 2.6.20 kernel. Then run the following: ```
sudo make && sudo make module_install
sudo insmod et131x.ko
sudo depmod
sudo modprobe et131x
```

After that everything works!  w00t!

---

### Post by iarkin on 2007-09-18
```
sudo make modules modules_install
```
Made everything tick for me ;)

---

### Post by atnishry on 2007-09-21
hi there,
is there a way to install the drivers on feisty or they will work only on edgy ?
10X
Amit

---

### Post by rla3rd on 2007-10-01
I havent had time to update the downloadable driver.  The subversion version will work though.

---

### Post by murmlos on 2007-10-19
Does it work for gutsy?

Because it gives me errors when trying to make.

Using the linux header 2.6.22-14 ...

Anyone?


Edit: Alrighty got it to work.. [https://sourceforge.net/tracker/index.php?func=detail&aid=1709009&group_id=179406&atid=889025](https://sourceforge.net/tracker/index.php?func=detail&aid=1709009&group_id=179406&atid=889025) that patch seemed to fix it.

Hooray now i can finally surf some serious pr0n under linux.

---

### Post by sailorxyz on 2007-10-29
Hi Murmlos,

How do you apply the patch please? I am a noob and your help will be most appreciated.

Regards,

Sailor

---

