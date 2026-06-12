---
title: "cisco vpn 32bits howto"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by cuby on 2009-11-02
Hello,
Instating the network manager plug-in was not enough for me in 9.10 (Karmic). I had to install the cisco vpn client and a patch for it. The original page is in Portuguese [here]("http://softwarelivre.org/mundolunga/blog/instalando-o-cisco-vpn-client-no-ubuntu-9.10-karmic"), so I decided to translate the fundamental parts and make some adaptations.

[Download client]("http://www.lan.kth.se/vpn/bin/vpnclient-linux-x86_64-4.8.02.0030-k9.tar.gz").
[URL="http://www.4shared.com/file/145508563/490d1885/vpnclient-linux2631.html"]
Download patch[/URL].

1st, you need to extract the client.
2nd, copy the patch to the vpnclient dir.
3rd, patch the client:

    ```
patch < vpnclient-linux.2.6.31.diff 
```

It will return something like:
> 
patching file interceptor.c

Then to install:

   ```
 sudo ./vpn_install
```

---

### Post by ballin on 2009-11-05
This worked for me thanks, I didn't fancy the other method after reports of timeouts.

---

### Post by angrydill on 2009-11-10
Thanks, for the helpful info. The patch worked for me.

I'm getting sporadic disconnects, but that may be due to problems with the Atheros wifi module, rather than vpnclient.

-a.d.-

---

### Post by galoisgalois on 2009-11-26
I still get "cisco_ipsec.ko" error when I run the install command.

I am running Ubuntu Karmic. Here are the details of the error. 

Thank you for the help.

[I]galois@galois-desktop:~/Desktop/vpnclient$ sudo ./vpn_install 
Cisco Systems VPN Client Version 4.8.02 (0030) Linux Installer
Copyright (C) 1998-2006 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 

Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.

Directory containing linux kernel source code [/lib/modules/2.6.31-15-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.31-15-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.31-15-generic/build" will be used to build the module.

Is the above correct [y]

Shutting down /opt/cisco-vpnclient/bin/vpnclient: module cisco_ipsec is not running.
Stopped: /etc/init.d/vpnclient_init (VPN init script)
Making module
make -C /lib/modules/2.6.31-15-generic/build SUBDIRS=/home/galois/Desktop/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-15-generic'
scripts/Makefile.build:49: *** CFLAGS was changed in "/home/galois/Desktop/vpnclient/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/galois/Desktop/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-15-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
galois@galois-desktop:~/Desktop/vpnclient$ 
[/I]

---

### Post by galoisgalois on 2009-11-26
I downloaded the below patch and applied it from the vpnclient folder. I re-ran the* sudo ./vpn_install* and it installed successfully.
[I]wget [http://lamnk.com/download/vpnclient-linux-4.8.02-64bit.patch](http://lamnk.com/download/vpnclient-linux-4.8.02-64bit.patch)
patch < ./vpnclient-linux-4.8.02-64bit.patch [/I]

But when I created a profile *vpn2work.pcf* in */etc/opt/cisco-vpnclient/Profiles* to connect to work and ran the command* vpnclient connect vpn2work.pcf*, this results into the following:

*The profile specified could not be read.*

Any hints to solve the puzzle, please?

Here is a summary for some new who is trying to install:
[I]Download vpnclient-linux-x86_64-4.8.02.0030-k9.tar.gz 
tar -zxvf vpnclient-linux-x86_64-4.8.02.0030-k9.tar.gz 
cd vpnclient
Download vpnclient-linux.2.6.31.diff and copy it to the above directory vpnclient
Run the following commands from the vpnclient directory:
patch < vpnclient-linux.2.6.31.diff
[/I][I]wget [http://lamnk.com/download/vpnclient-linux-4.8.02-64bit.patch](http://lamnk.com/download/vpnclient-linux-4.8.02-64bit.patch)
patch < ./vpnclient-linux-4.8.02-64bit.patch 
sudo ./vpn_install[/I]

Thank you.

---

### Post by mokojin on 2009-11-27
Hello

I have this error when appling the patch:


```

atching file interceptor.c
Hunk #1 FAILED at 116.
Hunk #2 succeeded at 132 (offset -5 lines).
Hunk #3 succeeded at 249 (offset -5 lines).
Hunk #4 succeeded at 278 (offset -5 lines).
Hunk #5 succeeded at 301 (offset -5 lines).
1 out of 5 hunks FAILED -- saving rejects to file interceptor.c.rej

```

Then when I try to compile I get:

```

Making module
make -C /lib/modules/2.6.31-15-generic/build SUBDIRS=/home/ricardo/Desktop/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-15-generic'
  CC [M]  /home/ricardo/Desktop/vpnclient/linuxcniapi.o
In file included from /home/ricardo/Desktop/vpnclient/Cniapi.h:15,
                 from /home/ricardo/Desktop/vpnclient/linuxcniapi.c:31:
/home/ricardo/Desktop/vpnclient/GenDefs.h:113: error: conflicting types for ‘uintptr_t’
include/linux/types.h:41: note: previous declaration of ‘uintptr_t’ was here
make[2]: *** [/home/ricardo/Desktop/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/ricardo/Desktop/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-15-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

```


Please any help would be helpfull :)

---

### Post by xamat on 2009-11-30
Remember to edit the kernel files every time you update your kernel sources. See complete (and working, for me) instructions here: [http://www.unixmen.com/linux-tutorials/540-cisco-vpn-client-in-ubuntu-karmic-solved](http://www.unixmen.com/linux-tutorials/540-cisco-vpn-client-in-ubuntu-karmic-solved)

---

