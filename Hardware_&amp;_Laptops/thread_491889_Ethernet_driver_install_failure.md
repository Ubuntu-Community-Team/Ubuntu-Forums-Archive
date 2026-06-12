---
title: "Ethernet driver install failure"
date: 2007-07-04
forum: Hardware &amp; Laptops
---

### Post by noctis_vulpes on 2007-07-04
...on an LG Xnote. I know that [drivers exist for this particular hardware (Agere et131x)]("http://ubuntuforums.org/showthread.php?p=2958695#post2958695") and have previously got it to work properly. However, since then I did a clean wipe of the system to give Feisty more space, and for some unknown (and probably stupid) reason, I am now getting this whenever try to do "make".

(USERNAME)@(USERNAME)-laptop:~$ cd '/home/(USERNAME)/et131x_20060131_v1-2-2/et131x/linux/driver' 
(USERNAME)@(USERNAME)-laptop:~/et131x_20060131_v1-2-2/et131x/linux/driver$ sudo make
Password:
#@make -C /lib/modules/2.6.20-15-generic/build M=/home/(USERNAME)/et131x_20060131_v1-2-2/et131x/linux/driver modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/(USERNAME)/et131x_20060131_v1-2-2/et131x/linux/driver/et131x_main.o
In file included from /home/(USERNAME)/et131x_20060131_v1-2-2/et131x/linux/driver/et131x_main.c:79:
/home/(USERNAME)/et131x_20060131_v1-2-2/et131x/linux/driver/et131x_version.h:85:26: error: linux/config.h: No such file or directory
In file included from /home/(USERNAME)/et131x_20060131_v1-2-2/et131x/linux/driver/ET1310_common.h:89,
                 from /home/(USERNAME)/et131x_20060131_v1-2-2/et131x/linux/driver/ET1310_phy.h:90,
                 from /home/(USERNAME)/et131x_20060131_v1-2-2/et131x/linux/driver/et131x_main.c:111:
/home/(USERNAME)/et131x_20060131_v1-2-2/et131x/linux/driver/ET1310_address_map.h:115:9: warning: "_BIT_FIELDS_HTOL" is not defined

... ((Like, 80 lines of this same thing... Only difference is the number after address_map.h))

/home/(USERNAME)/et131x_20060131_v1-2-2/et131x/linux/driver/ET1310_address_map.h:3100:9: warning: "_BIT_FIELDS_HTOL" is not defined
In file included from /home/(USERNAME)/et131x_20060131_v1-2-2/et131x/linux/driver/et131x_adapter.h:84,
                 from /home/(USERNAME)/et131x_20060131_v1-2-2/et131x/linux/driver/et131x_main.c:116:
/home/(USERNAME)/et131x_20060131_v1-2-2/et131x/linux/driver/ET1310_tx.h:99:13: warning: "_BIT_FIELDS_HTOL" is not defined
/home/(USERNAME)/et131x_20060131_v1-2-2/et131x/linux/driver/ET1310_tx.h:195:9: warning: "_BIT_FIELDS_HTOL" is not defined
In file included from /home/(USERNAME)/et131x_20060131_v1-2-2/et131x/linux/driver/et131x_adapter.h:85,
                 from /home/(USERNAME)/et131x_20060131_v1-2-2/et131x/linux/driver/et131x_main.c:116:
/home/(USERNAME)/et131x_20060131_v1-2-2/et131x/linux/driver/ET1310_rx.h:138:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/(USERNAME)/et131x_20060131_v1-2-2/et131x/linux/driver/ET1310_rx.h:169:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/(USERNAME)/et131x_20060131_v1-2-2/et131x/linux/driver/ET1310_rx.h:245:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/(USERNAME)/et131x_20060131_v1-2-2/et131x/linux/driver/ET1310_rx.h:284:9: warning: "_BIT_FIELDS_HTOL" is not defined
/home/(USERNAME)/et131x_20060131_v1-2-2/et131x/linux/driver/ET1310_rx.h:315:9: warning: "_BIT_FIELDS_HTOL" is not defined
In file included from /home/(USERNAME)/et131x_20060131_v1-2-2/et131x/linux/driver/et131x_adapter.h:85,
                 from /home/(USERNAME)/et131x_20060131_v1-2-2/et131x/linux/driver/et131x_main.c:116:
/home/(USERNAME)/et131x_20060131_v1-2-2/et131x/linux/driver/ET1310_rx.h:441: warning: ?&#49258;mem_cache_t??is deprecated
/home/(USERNAME)/et131x_20060131_v1-2-2/et131x/linux/driver/et131x_main.c:140: error: expected ????before string constant
/home/(USERNAME)/et131x_20060131_v1-2-2/et131x/linux/driver/et131x_main.c:141: error: expected ????before string constant
make[2]: *** [/home/(USERNAME)/et131x_20060131_v1-2-2/et131x/linux/driver/et131x_main.o] Error 1
make[1]: *** [_module_/home/(USERNAME)/et131x_20060131_v1-2-2/et131x/linux/driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [modules] Error 2
(USERNAME)@(USERNAME)-laptop:~/et131x_20060131_v1-2-2/et131x/linux/driver$ [/QUOTE]

... any idea what I might do to correct this? As I have said, it didn't do this the last time I tried installing Ubuntu on this very same computer and it's driving me up the wall. Version of Windows I installed in another partition changed but that shouldn't affect anything. This is what I did, in case one of you can tell me what I'm doing wrong.

1. Using a 100GB hard drive, I first divided into 25 and 75GB partition.  Formatted both as ntfs and used 25GB partition to install Windows XP professional in it.

2. Using Feisty live CD, I gave 35GB to the ntfs partition that I was going to use for data storage, giving me 40GB to install Feisty in.

3. I then take 3GB to be used as swap partition, and mapped the rest as root. primary/logical settings were left alone during this process and the install finishes without any problems.

4. I reboot, and for some reason during the initial testing it says that the create/modified dates are set in the future. (which I don't recall seeing from my previous, successful, attempt at installing Ubuntu). At the end of the check it says that I have some error which the installer has corrected. It makes me reboot again.

5. Boots into Ubuntu just fine, but when I try to install the ethernet card driver, the above error happens every single time. I've reinstalled Feisty like, 7 times already - Sometimes using a slightly different setting to see if anything at all has changed.

... Needless to say, nothing changed. 

Thousand thanks to anyone who can help me out.

---

### Post by noctis_vulpes on 2007-07-15
...I have still yet to solve this problem... Is there anyone who can help?

---

