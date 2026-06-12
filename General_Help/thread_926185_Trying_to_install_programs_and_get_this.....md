---
title: "Trying to install programs and get this...."
date: 2008-09-21
forum: General Help
---

### Post by Rival904 on 2008-09-21
Ok, this is just one example, I cant figure out why its erroring out on me, but it does it to every program I try to install, I am still kind of new to this whole thing, but I think if I can figure this out I wont have any more troubles. 

I downloaded aircrack, for instance, cd'd to that directory and ran "sudo make install"

and got 

```

matt@matt-desktop:~/Documents/aircrack-ng-1.0-rc1$ sudo make install
make -C src install
make[1]: Entering directory `/home/matt/Documents/aircrack-ng-1.0-rc1/src'
make -C osdep
make[2]: Entering directory `/home/matt/Documents/aircrack-ng-1.0-rc1/src/osdep'
Building for Linux
make[3]: Entering directory `/home/matt/Documents/aircrack-ng-1.0-rc1/src/osdep'
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -fPIC -I..
-c -o osdep.o osdep.c
osdep.c:21:20: error: stdlib.h: No such file or directory
osdep.c:22:20: error: assert.h: No such file or directory
osdep.c:23:20: error: string.h: No such file or directory
In file included from osdep.c:25:
osdep.h:11:24: error: netinet/in.h: No such file or directory
osdep.h:12:20: error: stdint.h: No such file or directory
In file included from osdep.c:25:
osdep.h:26: error: expected specifier-qualifier-list before ‘uint64_t’
cc1: warnings being treated as errors
osdep.h:106: warning: ‘struct in_addr’ declared inside parameter list
osdep.h:106: warning: its scope is only this definition or declaration, which is
 probably not what you want
osdep.h:127: warning: ‘struct in_addr’ declared inside parameter list
In file included from osdep.c:26:
network.h:11:22: error: inttypes.h: No such file or directory
network.h:12:23: error: sys/types.h: No such file or directory
In file included from osdep.c:26:
network.h:30: error: expected specifier-qualifier-list before ‘uint8_t’
osdep.c: In function ‘wi_read’:
osdep.c:30: warning: implicit declaration of function ‘assert’
osdep.c: In function ‘wi_alloc’:
osdep.c:94: warning: implicit declaration of function ‘malloc’
osdep.c:94: warning: incompatible implicit declaration of built-in function ‘mal
loc’
osdep.c:96: error: ‘NULL’ undeclared (first use in this function)
osdep.c:96: error: (Each undeclared identifier is reported only once
osdep.c:96: error: for each function it appears in.)
osdep.c:97: warning: implicit declaration of function ‘memset’
osdep.c:97: warning: incompatible implicit declaration of built-in function ‘mem
set’
osdep.c:101: warning: implicit declaration of function ‘free’
osdep.c: In function ‘wi_open’:
osdep.c:148: error: ‘NULL’ undeclared (first use in this function)
osdep.c:150: warning: implicit declaration of function ‘strncpy’
osdep.c:150: warning: incompatible implicit declaration of built-in function ‘st
rncpy’
osdep.c: At top level:
osdep.c:199: warning: ‘struct in_addr’ declared inside parameter list
osdep.c:200: error: conflicting types for ‘ti_set_ip’
osdep.h:127: error: previous declaration of ‘ti_set_ip’ was here
osdep.c: In function ‘ti_set_ip’:
osdep.c:202: warning: passing argument 2 of ‘ti->ti_set_ip’ from incompatible po                                                                                                                          inter type
osdep.c: In function ‘ti_alloc’:
osdep.c:211: warning: incompatible implicit declaration of built-in function ‘ma                                                                                                                          lloc’
osdep.c:213: error: ‘NULL’ undeclared (first use in this function)
osdep.c:214: warning: incompatible implicit declaration of built-in function ‘me                                                                                                                          mset’
make[3]: *** [osdep.o] Error 1
make[3]: Leaving directory `/home/matt/Documents/aircrack-ng-1.0-rc1/src/osdep'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/matt/Documents/aircrack-ng-1.0-rc1/src/osdep'
make[1]: *** [osd] Error 2
make[1]: Leaving directory `/home/matt/Documents/aircrack-ng-1.0-rc1/src'
make: *** [install] Error 2

```

Any ideas why? Alot of other programs I run "sudo make install" on I get alot of errors also, so I think they all might be related to a simple thing I am overlooking. 

Any help will be greatly appreciated!

---

### Post by StOoZ on 2008-09-21
type :
> sudo apt-get install build-essential

and then try again.

---

### Post by spibou on 2008-09-21
Generally you first do **make** and if this goes well then you do **sudo make install** Sometimes you have to do **./configure** before issuing make. There should be a README file in the directory where you expanded the tar file. Read this first.

---

### Post by Rival904 on 2008-09-21
> **StOoZ said:**
> type :


and then try again.
I did that, then tried again and got 

```

make -C src all
make[1]: Entering directory `/home/matt/Documents/aircrack-ng-1.0-rc1/src'
make -C osdep
make[2]: Entering directory `/home/matt/Documents/aircrack-ng-1.0-rc1/src/osdep'
Building for Linux
make[3]: Entering directory `/home/matt/Documents/aircrack-ng-1.0-rc1/src/osdep'
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -fPIC -I..    -c -o osdep.o osdep.c
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -fPIC -I..    -c -o network.o network.c
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -fPIC -I..    -c -o linux.o linux.c
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -fPIC -I..    -c -o linux_tap.o linux_tap.c
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -fPIC -I..    -c -o radiotap-parser.o radiotap-parser.c
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -fPIC -I..    -c -o common.o common.c
ar cru libosdep.a  osdep.o network.o linux.o linux_tap.o radiotap-parser.o common.o
ranlib libosdep.a
touch .os.Linux
make[3]: Leaving directory `/home/matt/Documents/aircrack-ng-1.0-rc1/src/osdep'
make[2]: Leaving directory `/home/matt/Documents/aircrack-ng-1.0-rc1/src/osdep'
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -Iinclude   -c -o aircrack-ng.o aircrack-ng.c
In file included from aircrack-ng.c:63:
crypto.h:12:26: error: openssl/hmac.h: No such file or directory
crypto.h:13:25: error: openssl/sha.h: No such file or directory
crypto.h:15:25: error: openssl/rc4.h: No such file or directory
crypto.h:16:25: error: openssl/aes.h: No such file or directory
cc1: warnings being treated as errors
aircrack-ng.c: In function ‘do_wpa_crack’:
aircrack-ng.c:4026: warning: implicit declaration of function ‘HMAC’
aircrack-ng.c:4026: warning: implicit declaration of function ‘EVP_sha1’
aircrack-ng.c:4032: warning: implicit declaration of function ‘EVP_md5’
make[1]: *** [aircrack-ng.o] Error 1
make[1]: Leaving directory `/home/matt/Documents/aircrack-ng-1.0-rc1/src'
make: *** [all] Error 2

```

---

### Post by StOoZ on 2008-09-21
did you read the README before installing it?
also , it could be that you are missing some dependencies..

---

### Post by Rival904 on 2008-09-21
> **StOoZ said:**
> did you read the README before installing it?
also , it could be that you are missing some dependencies..

It says this under the readme 


```

 * Installing:
    make install
    # If you want to use airolib-ng and co,
    # issue 'make SQLITE=true install' instead of 'make install'
    
    # Airpcap installation doesn't require any special parameter
    # since it's built-in (sqlite require an additional file to be
    # installed).

```

when I ran "make SQLITE=true install" I got 

```

make -C src install
make[1]: Entering directory `/home/matt/Documents/aircrack-ng-1.0-rc1/src'
make -C osdep
make[2]: Entering directory `/home/matt/Documents/aircrack-ng-1.0-rc1/src/osdep'
Building for Linux
make[3]: Entering directory `/home/matt/Documents/aircrack-ng-1.0-rc1/src/osdep'
make[3]: `.os.Linux' is up to date.
make[3]: Leaving directory `/home/matt/Documents/aircrack-ng-1.0-rc1/src/osdep'
make[2]: Leaving directory `/home/matt/Documents/aircrack-ng-1.0-rc1/src/osdep'
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -I/usr/local/i
nclude -DHAVE_SQLITE -Iinclude   -c -o aircrack-ng.o aircrack-ng.c
In file included from aircrack-ng.c:63:
crypto.h:12:26: error: openssl/hmac.h: No such file or directory
crypto.h:13:25: error: openssl/sha.h: No such file or directory
crypto.h:15:25: error: openssl/rc4.h: No such file or directory
crypto.h:16:25: error: openssl/aes.h: No such file or directory
aircrack-ng.c:69:21: error: sqlite3.h: No such file or directory
aircrack-ng.c:70: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before
 ‘*’ token
cc1: warnings being treated as errors
aircrack-ng.c: In function ‘do_wpa_crack’:
aircrack-ng.c:4026: warning: implicit declaration of function ‘HMAC’
aircrack-ng.c:4026: warning: implicit declaration of function ‘EVP_sha1’
aircrack-ng.c:4032: warning: implicit declaration of function ‘EVP_md5’
aircrack-ng.c: In function ‘main’:
aircrack-ng.c:4770: warning: implicit declaration of function ‘sqlite3_open’
aircrack-ng.c:4770: error: ‘db’ undeclared (first use in this function)
aircrack-ng.c:4770: error: (Each undeclared identifier is reported only once
aircrack-ng.c:4770: error: for each function it appears in.)
aircrack-ng.c:4771: warning: implicit declaration of function ‘sqlite3_errmsg’
aircrack-ng.c:4771: warning: format ‘%s’ expects type ‘char *’, but argument 3 h                                                                                                                          as type ‘int’
aircrack-ng.c:4772: warning: implicit declaration of function ‘sqlite3_close’
aircrack-ng.c:5363: warning: implicit declaration of function ‘sqlite3_mprintf’
aircrack-ng.c:5363: warning: assignment makes pointer from integer without a cas                                                                                                                          t
aircrack-ng.c:5365: warning: implicit declaration of function ‘sqlite3_exec’
aircrack-ng.c:5366: error: ‘SQLITE_LOCKED’ undeclared (first use in this functio                                                                                                                          n)
aircrack-ng.c:5366: error: ‘SQLITE_BUSY’ undeclared (first use in this function)
aircrack-ng.c:5372: error: ‘SQLITE_OK’ undeclared (first use in this function)
aircrack-ng.c:5372: error: ‘SQLITE_ABORT’ undeclared (first use in this function                                                                                                                          )
aircrack-ng.c:5374: warning: implicit declaration of function ‘sqlite3_free’
make[1]: *** [aircrack-ng.o] Error 1
make[1]: Leaving directory `/home/matt/Documents/aircrack-ng-1.0-rc1/src'
make: *** [install] Error 2


```

---

### Post by Rival904 on 2008-09-21
Ok talked to a buddy, and apparently Im missing a bunch of repositories, any ideas on how to add them? 

Im a little lost at this point

---

### Post by oldos2er on 2008-09-21
> **Rival904 said:**
> Ok talked to a buddy, and apparently Im missing a bunch of repositories, any ideas on how to add them? 

Im a little lost at this point

 I believe aircrack-ng is in Ubuntu's repositories. Go to System, Administration, Software Sources, and make sure all repositories are enabled.

---

### Post by Rival904 on 2008-09-21
Dont have anything close to that in Kubuntu :confused:

---

### Post by stoneage on 2008-09-21
[https://help.ubuntu.com/community/Repositories/Kubuntu](https://help.ubuntu.com/community/Repositories/Kubuntu)

---

