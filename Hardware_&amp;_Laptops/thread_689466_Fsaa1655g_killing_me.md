---
title: "Fsaa1655g killing me"
date: 2008-02-06
forum: Hardware &amp; Laptops
---

### Post by Baylee202 on 2008-02-06
I have been trying to get my wireless to work for ages. And i'm soon regretting that I switched to ubuntu.

I have an Amilo A1655g with an evil BCM4318 card.

I have tried just about every howto guide out there. fwcutter, ndiswrapper, wifiradar, you name it. But I recently thought of the fact that it might be my radio that not on. So I download fsaa1655g and unpacked. Then it gives me an error when I use the make command.  Found another guide that said I needed to install madwifi to get fsaa1655g working. So I get that and installed, only to find out I had madwifi. But I pressed on and tried to install anyways where I had to remove the old madwifi driver first. And it just gives me the same error with minor changes. So now I fear that I dont have madwifi and fsaa1655g is still not installed.

I did sudo apt-get install linux-headers-$(uname -r)
So there should be no problems with the kernel.

$ make install   for madwifi gives me

sh scripts/find-madwifi-modules.sh 2.6.22-14-generic 
for i in ./ath ./ath_hal ./ath_rate ./net80211; do \
                make -C $i install || exit 1; \
        done
make[1]: Entering directory `/home/easytoiron/download/madwifi-0.9.3.3/ath'
test -d //lib/modules/2.6.22-14-generic/net || mkdir -p //lib/modules/2.6.22-14-generic/net
install ath_pci.ko //lib/modules/2.6.22-14-generic/net
install: cannot stat `ath_pci.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/easytoiron/download/madwifi-0.9.3.3/ath'
make: *** [install-modules] Error 1


$ make     for fsaa1655g gives me

make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/easytoiron/download/fsaa1655g modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/easytoiron/download/fsaa1655g/fsaa1655g.o
/home/easytoiron/download/fsaa1655g/fsaa1655g.c:38:26: error: linux/config.h: No such file or directory
make[2]: *** [/home/easytoiron/download/fsaa1655g/fsaa1655g.o] Error 1
make[1]: *** [_module_/home/easytoiron/download/fsaa1655g] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [default] Error 2



And im new to this. So if you have a solution please make a detailed description on what to do.


Thanks

---

### Post by theuninvitedguest on 2008-02-06
As far as I can remember you have to open the makefile and remove the *#include "linux/config.h" * (for example by putting two slashes *//* before it thus making it a comment). I might be totally wrong though... The only thing I'm sure of is that I still couldn't get wireless to work. :mad: Damn 4318...

/Alex

---

### Post by Baylee202 on 2008-02-06
I have opened the Makefile and there is no such thing as #include "linux/config.h"

---

### Post by Baylee202 on 2008-02-08
Ok I found it now and wrote make install.

It gave me,

easytoiron@EVE:~/download/fsaa1655g$ make install
su -c "install -d /lib/modules/2.6.22-14-generic/kernel/net/wireless/ && install -m 644 -c fsaa1655g.ko /lib/modules/2.6.22-14-generic/kernel/net/wireless/ && /sbin/depmod -a"
Password: 
su: Authentication failure
Sorry.
make: *** [install] Error 1
easytoiron@EVE:~/download/fsaa1655g$ 

And I didnt write the password wrong. Unless the root password isent the same as my only profile password. But I think I made it the same a couple of days ago. 


So any suggestions anyone?

---

### Post by Baylee202 on 2008-02-08
Ok minor progress. 

sudo passwd made me able to set the password once again. And it gave me:

easytoiron@EVE:~/download/fsaa1655g$ sudo passwd
[sudo] password for easytoiron:
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
easytoiron@EVE:~/download/fsaa1655g$ make install
su -c "install -d /lib/modules/2.6.22-14-generic/kernel/net/wireless/ && install -m 644 -c fsaa1655g.ko /lib/modules/2.6.22-14-generic/kernel/net/wireless/ && /sbin/depmod -a"
Password: 

After that I had to modprobe and the next hindrance appered.

easytoiron@EVE:~/download/fsaa1655g$ modprobe fsaa1655g
FATAL: Error inserting fsaa1655g (/lib/modules/2.6.22-14-generic/kernel/net/wireless/fsaa1655g.ko): Operation not permitted
easytoiron@EVE:~/download/fsaa1655g$ 


So any ideas?

---

### Post by theuninvitedguest on 2008-02-10
Sorry, was absent a few days. Unfortunately I can't help you more, since I'm a newbie as well... But try to sudo the modprobe command (in your previous message)!

Bye,
Alex

---

### Post by angie IV on 2008-02-21
I had the same problem with the password... but now nothing happens, when I did the modprobe (also with sudo)

angela@angela-laptop:~/Desktop/fsaa1655g$ make
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/angela/Desktop/fsaa1655g modules
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.22-14-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.22-14-generic'
angela@angela-laptop:~/Desktop/fsaa1655g$ make install
su -c "install -d /lib/modules/2.6.22-14-generic/kernel/net/wireless/ && install -m 644 -c fsaa1655g.ko /lib/modules/2.6.22-14-generic/kernel/net/wireless/ && /sbin/depmod -a"
Passwort: 
angela@angela-laptop:~/Desktop/fsaa1655g$ sudo modprobe fsaa1655g
angela@angela-laptop:~/Desktop/fsaa1655g$ 


do you have any ideas?

---

### Post by theuninvitedguest on 2008-02-22
Nope. Got stuck at that point as well.

---

### Post by angie IV on 2008-03-04
I tried it again and again, and now the light is burning :)
but I have the next problem... I want to connect to the FRITZ!Box Fon WLAN 7113. It doesn't connect to internet. And doesn't really find the box. Do I need another driver?
Hope someone has information :confused:

---

