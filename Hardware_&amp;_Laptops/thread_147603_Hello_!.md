---
title: "Hello !"
date: 2006-03-20
forum: Hardware &amp; Laptops
---

### Post by p47 on 2006-03-20
Hello everybody.
I have some problems with my computer, and I want to know if other person had the same promems like me !

I have a Dimension 9150 and when I want to install ubuntu all is ok but ubuntu don't find my net card and video so i had to install "VESA Driver" and in this moment all is ok but I can't install very good my net card.

Somebody can help me ?
I was readed this tutorial:
[http://ubuntuforums.org/showthread.php?t=131429](http://ubuntuforums.org/showthread.php?t=131429)
But I stell have problems because in the last step ubuntu showme a error like this:

------------------------------------------------------------------
[COLOR="DarkRed"]admin@ubuntu:~$ cd /tmp
admin@ubuntu:/tmp$ dir
alsa-dmix-9537-1142798185-794583 gconfd-admin orbit-admin
e1000-7.0.33 keyring-X47Lt0 ssh-QGSKvD9486
e1000-7.0.33.tar.gz mapping-admin
admin@ubuntu:/tmp$ cd e1000-7.0.33
admin@ubuntu:/tmp/e1000-7.0.33$ cd src/
admin@ubuntu:/tmp/e1000-7.0.33/src$ sudo make install
Password:
make -C /lib/modules/2.6.12-10-386/build SUBDIRS=/tmp/e1000-7.0.33/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
CC [M] /tmp/e1000-7.0.33/src/e1000_main.o
In file included from include/linux/if_ether.h:107,
from include/linux/netdevice.h:29,
from /tmp/e1000-7.0.33/src/e1000.h:46,
from /tmp/e1000-7.0.33/src/e1000_main.c:29:
include/linux/skbuff.h: En la función &#8216;skb_add_data&#8217;:
include/linux/skbuff.h:1067: aviso: el puntero que apunta en el paso del argumento 1 de &#8216;csum_and_copy_from_user&#8217; difiere en signo
In file included from include/linux/ip.h:84,
from /tmp/e1000-7.0.33/src/e1000.h:61,
from /tmp/e1000-7.0.33/src/e1000_main.c:29:
include/net/sock.h: En la función &#8216;skb_copy_to_page&#8217;:
include/net/sock.h:992: aviso: el puntero que apunta en el paso del argumento 1 de &#8216;csum_and_copy_from_user&#8217; difiere en signo
/tmp/e1000-7.0.33/src/e1000_main.c: En la función &#8216;e1000_set_mac&#8217;:
/tmp/e1000-7.0.33/src/e1000_main.c:2086: aviso: el puntero que apunta en el paso del argumento 1 de &#8216;is_valid_ether_addr&#8217; difiere en signo
CC [M] /tmp/e1000-7.0.33/src/e1000_hw.o
In file included from include/linux/if_ether.h:107,
from include/linux/netdevice.h:29,
from /tmp/e1000-7.0.33/src/kcompat.h:37,
from /tmp/e1000-7.0.33/src/e1000_osdep.h:43,
from /tmp/e1000-7.0.33/src/e1000_hw.h:36,
from /tmp/e1000-7.0.33/src/e1000_hw.c:33:
include/linux/skbuff.h: En la función &#8216;skb_add_data&#8217;:
include/linux/skbuff.h:1067: aviso: el puntero que apunta en el paso del argumento 1 de &#8216;csum_and_copy_from_user&#8217; difiere en signo
CC [M] /tmp/e1000-7.0.33/src/e1000_param.o
In file included from include/linux/if_ether.h:107,
from include/linux/netdevice.h:29,
from /tmp/e1000-7.0.33/src/e1000.h:46,
from /tmp/e1000-7.0.33/src/e1000_param.c:29:
include/linux/skbuff.h: En la función &#8216;skb_add_data&#8217;:
include/linux/skbuff.h:1067: aviso: el puntero que apunta en el paso del argumento 1 de &#8216;csum_and_copy_from_user&#8217; difiere en signo
In file included from include/linux/ip.h:84,
from /tmp/e1000-7.0.33/src/e1000.h:61,
from /tmp/e1000-7.0.33/src/e1000_param.c:29:
include/net/sock.h: En la función &#8216;skb_copy_to_page&#8217;:
include/net/sock.h:992: aviso: el puntero que apunta en el paso del argumento 1 de &#8216;csum_and_copy_from_user&#8217; difiere en signo
/tmp/e1000-7.0.33/src/e1000_param.c: En el nivel principal:
/tmp/e1000-7.0.33/src/e1000_param.c:78: aviso: el puntero que apunta en la inicialización difiere en signo
/tmp/e1000-7.0.33/src/e1000_param.c:88: aviso: el puntero que apunta en la inicialización difiere en signo
/tmp/e1000-7.0.33/src/e1000_param.c:101: aviso: el puntero que apunta en la inicialización difiere en signo
/tmp/e1000-7.0.33/src/e1000_param.c:113: aviso: el puntero que apunta en la inicialización difiere en signo
/tmp/e1000-7.0.33/src/e1000_param.c:130: aviso: el puntero que apunta en la inicialización difiere en signo
/tmp/e1000-7.0.33/src/e1000_param.c:143: aviso: el puntero que apunta en la inicialización difiere en signo
/tmp/e1000-7.0.33/src/e1000_param.c:155: aviso: el puntero que apunta en la inicialización difiere en signo
/tmp/e1000-7.0.33/src/e1000_param.c:164: aviso: el puntero que apunta en la inicialización difiere en signo
/tmp/e1000-7.0.33/src/e1000_param.c:173: aviso: el puntero que apunta en la inicialización difiere en signo
/tmp/e1000-7.0.33/src/e1000_param.c:182: aviso: el puntero que apunta en la inicialización difiere en signo
/tmp/e1000-7.0.33/src/e1000_param.c:191: aviso: el puntero que apunta en la inicialización difiere en signo
/tmp/e1000-7.0.33/src/e1000_param.c:200: aviso: el puntero que apunta en la inicialización difiere en signo
/tmp/e1000-7.0.33/src/e1000_param.c: En la función &#8216;e1000_check_options&#8217;:
/tmp/e1000-7.0.33/src/e1000_param.c:339: aviso: el puntero que apunta en el paso del argumento 1 de &#8216;e1000_validate_option&#8217; difiere en signo
/tmp/e1000-7.0.33/src/e1000_param.c:369: aviso: el puntero que apunta en el paso del argumento 1 de &#8216;e1000_validate_option&#8217; difiere en signo
/tmp/e1000-7.0.33/src/e1000_param.c:445: aviso: el puntero que apunta en el paso del argumento 1 de &#8216;e1000_validate_option&#8217; difiere en signo
/tmp/e1000-7.0.33/src/e1000_param.c:467: aviso: el puntero que apunta en el paso del argumento 1 de &#8216;e1000_validate_option&#8217; difiere en signo
/tmp/e1000-7.0.33/src/e1000_param.c:489: aviso: el puntero que apunta en el paso del argumento 1 de &#8216;e1000_validate_option&#8217; difiere en signo
/tmp/e1000-7.0.33/src/e1000_param.c:511: aviso: el puntero que apunta en el paso del argumento 1 de &#8216;e1000_validate_option&#8217; difiere en signo
/tmp/e1000-7.0.33/src/e1000_param.c:543: aviso: el puntero que apunta en el paso del argumento 1 de &#8216;e1000_validate_option&#8217; difiere en signo
CC [M] /tmp/e1000-7.0.33/src/e1000_ethtool.o
In file included from include/linux/if_ether.h:107,
from include/linux/netdevice.h:29,
from /tmp/e1000-7.0.33/src/e1000.h:46,
from /tmp/e1000-7.0.33/src/e1000_ethtool.c:31:
include/linux/skbuff.h: En la función &#8216;skb_add_data&#8217;:
include/linux/skbuff.h:1067: aviso: el puntero que apunta en el paso del argumento 1 de &#8216;csum_and_copy_from_user&#8217; difiere en signo
In file included from include/linux/ip.h:84,
from /tmp/e1000-7.0.33/src/e1000.h:61,
from /tmp/e1000-7.0.33/src/e1000_ethtool.c:31:
include/net/sock.h: En la función &#8216;skb_copy_to_page&#8217;:
include/net/sock.h:992: aviso: el puntero que apunta en el paso del argumento 1 de &#8216;csum_and_copy_from_user&#8217; difiere en signo
CC [M] /tmp/e1000-7.0.33/src/kcompat.o
In file included from include/linux/if_ether.h:107,
from include/linux/netdevice.h:29,
from /tmp/e1000-7.0.33/src/kcompat.h:37,
from /tmp/e1000-7.0.33/src/kcompat.c:29:
include/linux/skbuff.h: En la función &#8216;skb_add_data&#8217;:
include/linux/skbuff.h:1067: aviso: el puntero que apunta en el paso del argumento 1 de &#8216;csum_and_copy_from_user&#8217; difiere en signo
LD [M] /tmp/e1000-7.0.33/src/e1000.o
Building modules, stage 2.
MODPOST
CC /tmp/e1000-7.0.33/src/e1000.mod.o
LD [M] /tmp/e1000-7.0.33/src/e1000.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
gzip -c ../e1000.7 > e1000.7.gz
# remove all old versions of the driver
find /lib/modules/2.6.12-10-386 -name e1000.ko -exec rm -f {} \; || true
find /lib/modules/2.6.12-10-386 -name e1000.ko.gz -exec rm -f {} \; || true
install -D -m 644 e1000.ko /lib/modules/2.6.12-10-386/kernel/drivers/net/e1000/e1000.ko
/sbin/depmod -a || true
install -D -m 644 e1000.7.gz /usr/share/man/man7/e1000.7.gz
man -c -P'cat > /dev/null' e1000 || true
man:
no se puede escribir en /var/cache/man/cat7/e1000.7.gz en modo catman.
e1000.
admin@ubuntu:/tmp/e1000-7.0.33/src$[/COLOR]
------------------------------------
Sorry ! is spanish
I can't wite in /var/cache/man/cat7/e1000.7.gz in mode catman.
e1000.
admin@ubuntu:/tmp/e1000-7.0.33/src$
------------------------------------


And I don't know what can I do !


Do you know why ubuntu show me this error !
Well, I do exactly all that the manual said ,I don't know if this afect someting when I download the files of gcc or not are exactly similars

The manual show me this files:
gcc-3.4_3.4.4-6ubuntu8_i386.deb gcc-3.4-base_3.4.4-6ubuntu8_i386.deb
And when I download for example the gcc_base the manual I can see someting almost diferent in all the files for example this:

gcc-3.4-base_3.4.4-6ubuntu8.1_i386.deb on Intel x86 

What should I do ?
Please forgive me my I think that my enlgish is very bad !
I hope you can understand me !

Regards !:-k

---

### Post by Zimmer on 2006-03-24
It looks like you did not unzip the file and put it into the correct directory

I quote from the instructions:
> then:
Code:

cd

to the /e1000-7.0.33/src directory where you unzipped the driver and type:
Code:

sudo make install
It looks like the install fails as it is trying to install the zipped file.

I hope this helps.. no habla espagnol...

---

