---
title: "VX-1000 Webcam not working on Ubuntu 9.10"
date: 2009-11-09
forum: Hardware
---

### Post by majatt on 2009-11-09
Hi guys,


Trying to get a VX-1000 webcam to work on Ubuntu 9.10 (Karmic Koala). It isn't working in cheese or in skype, displays strange looking green.

[IMG]http://img18.imageshack.us/img18/[/IMG][IMG]http://ubuntu-virginia.ubuntuforums.org/%3Ca%20href=http://img18.imageshack.us/i/screenshotcheese.png/%20target=_blank%3E[IMG]http://img18.imageshack.us/img18/1269/screenshotcheese.png[/IMG][IMG]http://img18.imageshack.us/img18/1269/screenshotcheese.png[/IMG]

Was trying to get GSPCA installed but I found on a forum that it is included in the kernel now.

Kernel Version:

[FONT=Courier New]$ uname -r
2.6.31-14-generic-pae[/FONT]

Checked for gspca:
[FONT=Courier New]
$ lsmod | grep gspca
gspca_sonixj           20796  0 
gspca_main             22844  1 gspca_sonixj
videodev               36736  1 gspca_main[/FONT]

So to my limited knowledge the module is installed...but I still can't get anything on the camera.

Can anyone please help me out?

---

### Post by majatt on 2009-11-11
Got the issues resolved.

---

### Post by isbel_l@hotmail.com on 2009-11-18
Hi,

I got the same problem here. Can you describe your solution?

---

### Post by majatt on 2009-11-19
> **isbel_l@hotmail.com said:**
> Hi,

I got the same problem here. Can you describe your solution?


# wget  [http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2](http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2)
# bunzip2 tip.tar.bz2
# tar xf tip.tar
# make

The make will fail.

# cd v4l-dvb-19c0469c02c3
# vi v4l/.config

Change CONFIG_DVB_FIREDTV=m to CONFIG_DVB_FIREDTV=n.

# make
# sudo make install

Then reboot.


That fixed the camera for me and got it to work in Cheese but then to get skype to work I had to use the medibuntu skype:

[FONT=courier new]# sudo aptitude remove skype[/FONT]
[FONT=courier new]# sudo apt-get install skype-common[/FONT]

I tried install skype but no juice, worked all the same though.

P.S. adding medibuntu repository from [here]("http://ubuntuguide.org/wiki/Ubuntu:Karmic").[INDENT]deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free
 
[LIST]
[*]Download the repository key to a folder.
[/LIST]
 
[LIST]
[*]*Example:* The Medibuntu key can be downloaded from
[/LIST]
 [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg)     
[LIST]
[*] Then add the key from:
[/LIST]
   System -> Administration -> Synaptic Manager -> Settings -> Repositories -> Authentication -> Import Key File...   
[LIST]
[*](Alternatively, you can manually add the key from the command line Terminal. See [Add Repository keys]("http://ubuntuguide.org/wiki/Ubuntu:Karmic#Add_Repository_keys").)
[/LIST]
  
[LIST]
[*]Refresh the package list from the new repository:
[/LIST]
  Synaptic -> Reload [/INDENT]

---

### Post by Liudwik on 2009-11-27
Hello,

Thank you. That helped me, but in my case i had to make changes to v4l/.config file between steps "make" and "sudo make install". Otherwise there were no .config file just after extraction of downloaded stuff.

Cheers!

---

### Post by stanca on 2009-11-30
Thanks for the tip.I'll try it too later.Untill now I didn't have any success.:D

---

### Post by Ceyce on 2009-12-19
> **majatt said:**
> # wget  [http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2](http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2)
# bunzip2 tip.tar.bz2
# tar xf tip.tar
# cd v4l-dvb-19c0469c02c3
# vi v4l/.config

Change CONFIG_DVB_FIREDTV=m to CONFIG_DVB_FIREDTV=n.

# make
# sudo make install

Then reboot.

I try it, but  there were no .config file, even not after extraction of downloaded stuff.
Someone can help me please? :)

---

### Post by majatt on 2009-12-21
> **Ceyce said:**
> I try it, but  there were no .config file, even not after extraction of downloaded stuff.
Someone can help me please? :)

As a user above mentioned I made a mistake when I typed the instructions:

After typing *make*, edit the config and then do the *make install*.
Rather going *make* then *make install* because the config file is created by *make*. If you don't do it in that order you'll get the problem. I'll update the original post to reflect that.

---

### Post by Ceyce on 2009-12-24
> **majatt said:**
> 
After typing *make*, edit the config and then do the *make install*.
Rather going *make* then *make install* because the config file is created by *make*. If you don't do it in that order you'll get the problem. I'll update the original post to reflect that.
Thank you! I found the config file, but it still don't work :( Before doing anything, I had it as shown on screen in post 1, now I have this:
[http://img20.yfrog.com/img20/8298/13821902.png](http://img20.yfrog.com/img20/8298/13821902.png)

---

### Post by hobo14 on 2010-01-09
Grrr...
 Was over the moon to find this solution, until I got the following errors during make.  Does anyone know what I can do to make successfully?

Output from make from when things went bad:
```
CC [M]  /home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/et61x251_core.o
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/et61x251_core.c: In function 'et61x251_ioctl_v4l2':
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/et61x251_core.c:2500: warning: the frame size of 1256 bytes is larger than 1024 bytes
  CC [M]  /home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/et61x251_tas5130d1b.o
  CC [M]  /home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-avc.o
  CC [M]  /home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-ci.o
  CC [M]  /home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-dvb.o
  CC [M]  /home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-fe.o
  CC [M]  /home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.o
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:21:17: error: dma.h: No such file or directory
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:22:21: error: csr1212.h: No such file or directory
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:23:23: error: highlevel.h: No such file or directory
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:24:19: error: hosts.h: No such file or directory
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:25:22: error: ieee1394.h: No such file or directory
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:26:17: error: iso.h: No such file or directory
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:27:21: error: nodemgr.h: No such file or directory
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:40: warning: 'struct hpsb_iso' declared inside parameter list
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:40: warning: its scope is only this definition or declaration, which is probably not what you want
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c: In function 'rawiso_activity_cb':
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:56: error: dereferencing pointer to incomplete type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:57: error: implicit declaration of function 'hpsb_iso_n_ready'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:64: error: dereferencing pointer to incomplete type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:65: error: implicit declaration of function 'dma_region_i'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:65: error: dereferencing pointer to incomplete type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:65: error: expected expression before 'unsigned'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:66: warning: assignment makes pointer from integer without a cast
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:67: error: dereferencing pointer to incomplete type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:71: error: dereferencing pointer to incomplete type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:85: error: implicit declaration of function 'hpsb_iso_recv_release_packets'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c: In function 'node_of':
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:90: error: dereferencing pointer to incomplete type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:90: warning: type defaults to 'int' in declaration of '__mptr'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:90: warning: initialization from incompatible pointer type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:90: error: invalid use of undefined type 'struct unit_directory'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c: In function 'node_lock':
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:97: error: implicit declaration of function 'hpsb_node_lock'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:97: error: 'EXTCODE_COMPARE_SWAP' undeclared (first use in this function)
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:97: error: (Each undeclared identifier is reported only once
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:97: error: for each function it appears in.)
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:98: error: 'quadlet_t' undeclared (first use in this function)
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:98: error: expected expression before ')' token
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c: In function 'node_read':
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:106: error: implicit declaration of function 'hpsb_node_read'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c: In function 'node_write':
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:111: error: implicit declaration of function 'hpsb_node_write'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c: In function 'start_iso':
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:122: error: implicit declaration of function 'hpsb_iso_recv_init'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:122: error: dereferencing pointer to incomplete type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:124: error: 'HPSB_ISO_DMA_DEFAULT' undeclared (first use in this function)
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:126: warning: assignment makes pointer from integer without a cast
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:133: error: implicit declaration of function 'hpsb_iso_recv_start'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:136: error: implicit declaration of function 'hpsb_iso_shutdown'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c: In function 'stop_iso':
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:147: error: implicit declaration of function 'hpsb_iso_stop'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c: At top level:
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:162: warning: 'struct hpsb_host' declared inside parameter list
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c: In function 'fcp_request':
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:175: error: dereferencing pointer to incomplete type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:176: error: dereferencing pointer to incomplete type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c: In function 'node_probe':
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:190: error: dereferencing pointer to incomplete type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:190: warning: type defaults to 'int' in declaration of '__mptr'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:190: warning: initialization from incompatible pointer type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:190: error: invalid use of undefined type 'struct unit_directory'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:195: error: dereferencing pointer to incomplete type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:195: error: 'quadlet_t' undeclared (first use in this function)
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:196: error: implicit declaration of function 'CSR1212_TEXTUAL_DESCRIPTOR_LEAF_DATA'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:196: error: dereferencing pointer to incomplete type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:196: warning: assignment makes pointer from integer without a cast
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c: At top level:
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:252: warning: 'struct unit_directory' declared inside parameter list
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c: In function 'node_update':
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:254: error: dereferencing pointer to incomplete type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c: At top level:
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:262: error: variable 'fdtv_driver' has initializer but incomplete type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:263: error: unknown field 'name' specified in initializer
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:263: warning: excess elements in struct initializer
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:263: warning: (near initialization for 'fdtv_driver')
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:264: error: unknown field 'id_table' specified in initializer
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:264: warning: excess elements in struct initializer
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:264: warning: (near initialization for 'fdtv_driver')
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:265: error: unknown field 'update' specified in initializer
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:265: warning: excess elements in struct initializer
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:265: warning: (near initialization for 'fdtv_driver')
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:266: error: unknown field 'driver' specified in initializer
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:266: error: extra brace group at end of initializer
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:266: error: (near initialization for 'fdtv_driver')
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:269: warning: excess elements in struct initializer
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:269: warning: (near initialization for 'fdtv_driver')
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:272: error: variable 'fdtv_highlevel' has initializer but incomplete type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:273: error: unknown field 'name' specified in initializer
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:273: warning: excess elements in struct initializer
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:273: warning: (near initialization for 'fdtv_highlevel')
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:274: error: unknown field 'fcp_request' specified in initializer
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:274: warning: excess elements in struct initializer
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:274: warning: (near initialization for 'fdtv_highlevel')
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c: In function 'fdtv_1394_init':
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:281: error: implicit declaration of function 'hpsb_register_highlevel'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:282: error: implicit declaration of function 'hpsb_register_protocol'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:285: error: implicit declaration of function 'hpsb_unregister_highlevel'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c: In function 'fdtv_1394_exit':
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:292: error: implicit declaration of function 'hpsb_unregister_protocol'
make[3]: *** [/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.o] Error 1
make[2]: *** [_module_/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l'
make: *** [all] Error 2

```

---

### Post by hobo14 on 2010-01-09
I don't suppose I can request a mod remove the [SOLVED] tag?  
There's a lot more life left in this thread yet.

EDIT: obscured my relevant post:
> 
Grrr...
 Was over the moon to find this solution, until I got the following errors during make.  Does anyone know what I can do to make successfully?

Output from make from when things went bad:
```
CC [M]  /home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/et61x251_core.o
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/et61x251_core.c: In function 'et61x251_ioctl_v4l2':
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/et61x251_core.c:2500: warning: the frame size of 1256 bytes is larger than 1024 bytes
  CC [M]  /home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/et61x251_tas5130d1b.o
  CC [M]  /home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-avc.o
  CC [M]  /home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-ci.o
  CC [M]  /home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-dvb.o
  CC [M]  /home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-fe.o
  CC [M]  /home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.o
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:21:17: error: dma.h: No such file or directory
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:22:21: error: csr1212.h: No such file or directory
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:23:23: error: highlevel.h: No such file or directory
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:24:19: error: hosts.h: No such file or directory
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:25:22: error: ieee1394.h: No such file or directory
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:26:17: error: iso.h: No such file or directory
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:27:21: error: nodemgr.h: No such file or directory
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:40: warning: 'struct hpsb_iso' declared inside parameter list
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:40: warning: its scope is only this definition or declaration, which is probably not what you want
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c: In function 'rawiso_activity_cb':
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:56: error: dereferencing pointer to incomplete type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:57: error: implicit declaration of function 'hpsb_iso_n_ready'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:64: error: dereferencing pointer to incomplete type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:65: error: implicit declaration of function 'dma_region_i'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:65: error: dereferencing pointer to incomplete type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:65: error: expected expression before 'unsigned'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:66: warning: assignment makes pointer from integer without a cast
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:67: error: dereferencing pointer to incomplete type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:71: error: dereferencing pointer to incomplete type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:85: error: implicit declaration of function 'hpsb_iso_recv_release_packets'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c: In function 'node_of':
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:90: error: dereferencing pointer to incomplete type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:90: warning: type defaults to 'int' in declaration of '__mptr'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:90: warning: initialization from incompatible pointer type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:90: error: invalid use of undefined type 'struct unit_directory'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c: In function 'node_lock':
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:97: error: implicit declaration of function 'hpsb_node_lock'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:97: error: 'EXTCODE_COMPARE_SWAP' undeclared (first use in this function)
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:97: error: (Each undeclared identifier is reported only once
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:97: error: for each function it appears in.)
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:98: error: 'quadlet_t' undeclared (first use in this function)
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:98: error: expected expression before ')' token
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c: In function 'node_read':
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:106: error: implicit declaration of function 'hpsb_node_read'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c: In function 'node_write':
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:111: error: implicit declaration of function 'hpsb_node_write'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c: In function 'start_iso':
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:122: error: implicit declaration of function 'hpsb_iso_recv_init'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:122: error: dereferencing pointer to incomplete type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:124: error: 'HPSB_ISO_DMA_DEFAULT' undeclared (first use in this function)
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:126: warning: assignment makes pointer from integer without a cast
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:133: error: implicit declaration of function 'hpsb_iso_recv_start'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:136: error: implicit declaration of function 'hpsb_iso_shutdown'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c: In function 'stop_iso':
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:147: error: implicit declaration of function 'hpsb_iso_stop'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c: At top level:
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:162: warning: 'struct hpsb_host' declared inside parameter list
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c: In function 'fcp_request':
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:175: error: dereferencing pointer to incomplete type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:176: error: dereferencing pointer to incomplete type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c: In function 'node_probe':
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:190: error: dereferencing pointer to incomplete type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:190: warning: type defaults to 'int' in declaration of '__mptr'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:190: warning: initialization from incompatible pointer type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:190: error: invalid use of undefined type 'struct unit_directory'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:195: error: dereferencing pointer to incomplete type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:195: error: 'quadlet_t' undeclared (first use in this function)
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:196: error: implicit declaration of function 'CSR1212_TEXTUAL_DESCRIPTOR_LEAF_DATA'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:196: error: dereferencing pointer to incomplete type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:196: warning: assignment makes pointer from integer without a cast
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c: At top level:
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:252: warning: 'struct unit_directory' declared inside parameter list
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c: In function 'node_update':
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:254: error: dereferencing pointer to incomplete type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c: At top level:
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:262: error: variable 'fdtv_driver' has initializer but incomplete type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:263: error: unknown field 'name' specified in initializer
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:263: warning: excess elements in struct initializer
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:263: warning: (near initialization for 'fdtv_driver')
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:264: error: unknown field 'id_table' specified in initializer
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:264: warning: excess elements in struct initializer
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:264: warning: (near initialization for 'fdtv_driver')
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:265: error: unknown field 'update' specified in initializer
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:265: warning: excess elements in struct initializer
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:265: warning: (near initialization for 'fdtv_driver')
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:266: error: unknown field 'driver' specified in initializer
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:266: error: extra brace group at end of initializer
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:266: error: (near initialization for 'fdtv_driver')
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:269: warning: excess elements in struct initializer
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:269: warning: (near initialization for 'fdtv_driver')
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:272: error: variable 'fdtv_highlevel' has initializer but incomplete type
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:273: error: unknown field 'name' specified in initializer
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:273: warning: excess elements in struct initializer
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:273: warning: (near initialization for 'fdtv_highlevel')
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:274: error: unknown field 'fcp_request' specified in initializer
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:274: warning: excess elements in struct initializer
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:274: warning: (near initialization for 'fdtv_highlevel')
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c: In function 'fdtv_1394_init':
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:281: error: implicit declaration of function 'hpsb_register_highlevel'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:282: error: implicit declaration of function 'hpsb_register_protocol'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:285: error: implicit declaration of function 'hpsb_unregister_highlevel'
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c: In function 'fdtv_1394_exit':
/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.c:292: error: implicit declaration of function 'hpsb_unregister_protocol'
make[3]: *** [/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l/firedtv-1394.o] Error 1
make[2]: *** [_module_/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/collins/Desktop/v4l-dvb-b6b82258cf5e/v4l'
make: *** [all] Error 2

```


---

### Post by hobo14 on 2010-01-09
Bump

---

### Post by majatt on 2010-01-11
[COLOR=Black]Have you made the change to the order of commands that [/COLOR]Liudwik suggested?

If so and you are still getting the problem post your kernel version? I will take a close look at your output later a bit short on time.

---

### Post by Ceyce on 2010-01-11
Now i did the make before and after I edited v4l/.config file, and this is the result:
[http://xmages.net/upload/e01ec1a6.png](http://xmages.net/upload/e01ec1a6.png)

It is the image of my room, but its "broken".
Someone knows what else can I do?

---

### Post by jesterthejedi on 2010-01-11
I got a similar result by disabling all the extra drivers from the menuconfig window.

---

### Post by hobo14 on 2010-01-12
> **majatt said:**
> [COLOR=Black]Have you made the change to the order of commands that [/COLOR]Liudwik suggested?

If so and you are still getting the problem post your kernel version? I will take a close look at your output later a bit short on time.

Sorry for the slow response majatt.

I planned to follow Liudwik's order, but I haven't got that far; I'm stuck on the "make" line - the output I posted is all from this.
I'm not at the config file edit or "sudo make install" yet.

My kernel version is:
2.6.31-16-generic #53-ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686 GNU/Linux

I've also tried it with 2.6.31-17, with the same result.

---

### Post by jdmiami on 2010-01-12
Can sombody help me Im a noob... maybe a step by step installation ... Id really appriciate it...

---

### Post by tibike on 2010-01-12
Yeah! I get the same as Ceyce and jesterthejedi...
but I can testify that a couple of week ago (back in 2009) i used the same instructions with success a couple of times (on similar systems). Maybe the v4l-dvb pack has been updated in such a way that it broke...
Same discussion here: [http://ubuntuforums.org/showthread.php?t=1034988&page=6](http://ubuntuforums.org/showthread.php?t=1034988&page=6)
yet another thread here: [http://ubuntuforums.org/showthread.php?p=8650015](http://ubuntuforums.org/showthread.php?p=8650015)

---

### Post by jesterthejedi on 2010-01-19
> **jdmiami said:**
> Can sombody help me Im a noob... maybe a step by step installation ... Id really appriciate it...

Even us "experts" with this cam can't get it working. It will install the driver, but it no longer shows a picture. We wait again for an update. Do we have a bug report somewhere open for this?

Here it is:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460118](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460118)

---

### Post by Ceyce on 2010-01-29
It works now!!!! :D
I did those steps again, and it get worked!

---

### Post by jesterthejedi on 2010-01-29
> **Ceyce said:**
> It works now!!!! :D
I did those steps again, and it get worked!

What steps? Please share your results.

---

### Post by Ceyce on 2010-01-30
> **jesterthejedi said:**
> What steps? Please share your results.
[http://ubuntuforums.org/showthread.php?p=8569519#post8569519](http://ubuntuforums.org/showthread.php?p=8569519#post8569519)

Its for VX-3000, but I have VX-1000 and it worked. ...and you have the same steps in this topic

---

### Post by Ron_ on 2010-05-15
I am using Ubuntu 9.10 amd64.  Has anyone tried   [http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2](http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2) drivers on a 64-bit system?  I _really_ don't want to break what I've got (including proprietary nVidia drivers for my monitor.)

Hang on....  I just plugged in the webcam, fired up Cheese and got a decent picture _without_ installing new drivers.  This is different from the last time that I tested it (a couple of months ago.), as far as I remember.   Can't tell if this will be stable.  PulseAudio Volume Control recognizes the webcam mic.  

Installed 64-bit Skype.  Audio doesn't work.  Tried  LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so .  Did not help audio, but it may have helped send video during calls, so I left it in.   Also, I'm getting TCP and UDP hits on port 13647.  Don't know how to interpret any of this.
 
Additional observations on the webcam mic:
1) I wanted to see if I needed the camera on to make the mic work.  Ran Gnome Sound Recorder with and without Cheese.  No sound either way.

2) Skype Options, Sound Devices shows Microphone = PulseAudio server (local) -- _not_ LifeCam VX-1000.   I edited /home/xxxx/.Skype/yyyy/config.xml  by hand, changing PulseAudio to LifeCam.  This seemed to make no difference in the Options menu when I restarted Skype.

3) A very interesting idea appears here: [http://ubuntuforums.org/showthread.php?t=1348604](http://ubuntuforums.org/showthread.php?t=1348604) .  Ghost|BTFH suggests that certain apps don't work with PulseAudio.  He shows how to restore asoundconf from Intrepid's ALSA-utils.  This enables toggling between two sound cards.  Much to my surprise, gnome-alsamixer tells me that I have two "sound cards": Realtek ALC888 and USB Mixer.  (The webcam mic is obviously on the USB Mixer.)  I am too inexperienced to take this approach, but perhaps it will lead to a solution for other users.   (I tried to accomplish the same thing by installing padevchooser, without success.)

5) I also found this Known Issue at [https://developer.skype.com/LinuxSkype](https://developer.skype.com/LinuxSkype) : "When [PulseAudio]("https://developer.skype.com/PulseAudio") is enabled in the audio settings, only that specific entry will be available."

---

### Post by Ron_ on 2010-05-20
Since the last post, I have played around with a few other approaches to try to get the VX-1000 mic to work -- all without success:

[LIST]
[*]Use gstreamer-properties to change the default input to the ALSA device, bypassing PulseAudio.
[*]Used System > Administration > Users and Groups to include myself and root in the pulse-access group.
[*]Created /etc/asound.conf, as described in a number of places.
[*]Many combinations of these plus gnome-alsamixer, pavucontrol, paman, padevchooser, etc., etc., skype and gnome-sound-recorder
[/LIST]
Has anyone explored the possibility that the VX-1000 might need a Microsoft-proprietary command to open the mic?

---

### Post by Ron_ on 2010-07-07
Kyle just showed me how to produce sound here: [http://ubuntuforums.org/showthread.p...72#post9560972]("http://ubuntuforums.org/showthread.php?p=9560972#post9560972") (post #12.)  Many thanks.

---

