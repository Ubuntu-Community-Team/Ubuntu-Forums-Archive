---
title: "Cannot start xfce4"
date: 2015-06-07
forum: Hardware
---

### Post by HDdeltin on 2015-06-07
Hello
I am on an Acer Chromebook C4, when I open the terminal and type
```
shell
```
```
sudo startxfce4
```
and this came up. I have accessed xfce many times. How can I fix this?








Entering /usr/local/chroots/precise...
/usr/bin/startxfce4: Starting X server

ERROR: ld.so: object '/usr/local/lib/croutonfreon.so' from LD_PRELOAD cannot be preloaded: ignored.
_XSERVTransmkdir: Owner of /tmp/.X11-unix should be set to root

X.Org X Server 1.15.1
Release Date: 2014-04-13
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.42-75-generic x86_64 Ubuntu
Current Operating System: Linux localhost 3.8.11 #1 SMP Tue May 26 18:03:42 PDT 2015 x86_64
Kernel command line: cros_secure  console= loglevel=7 init=/sbin/init cros_secure oops=panic panic=-1 root=/dev/dm-1 rootwait ro dm_verity.error_behavior=3 dm_verity.max_bios=-1 dm_verity.dev_wait=1 dm="2 vboot none ro 1,0 2545920 bootcache PARTUUID=748b5685-1911-6f4b-bf25-db836a7869c7/PARTNROFF=1 2545920 cf36f82b4141de51494e8d862437dbcffd6c4c7e 512 20000 100000, vroot none ro 1,0 2506752 verity payload=254:0 hashtree=254:0 hashstart=2506752 alg=sha1 root_hexdigest=12a36f9d2ea513bddea208ab19e6408d08fe0d10 salt=2fd4f0b1115757173480a945a03909de4703d296ce3a29aad73e70af73e720d6" noinitrd vt.global_cursor_default=0 kern_guid=748b5685-1911-6f4b-bf25-db836a7869c7 add_efi_memmap boot=local noresume noswap i915.modeset=1 tpm_tis.force=1 tpm_tis.interrupts=0 nmi_watchdog=panic,lapic iTCO_vendor_support.vendorsupport=3  
Build Date: 12 February 2015  03:37:52PM
xorg-server 2:1.15.1-0ubuntu2~precise5 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.30.2
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(++) Log file: "/tmp/Xorg.crouton.1.log", Time: Sun Jun  7 07:51:34 2015
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
Initializing built-in extension Generic Event Extension
Initializing built-in extension SHAPE
Initializing built-in extension MIT-SHM
Initializing built-in extension XInputExtension
Initializing built-in extension XTEST
Initializing built-in extension BIG-REQUESTS
Initializing built-in extension SYNC
Initializing built-in extension XKEYBOARD
Initializing built-in extension XC-MISC
Initializing built-in extension SECURITY
Initializing built-in extension XINERAMA
Initializing built-in extension XFIXES
Initializing built-in extension RENDER
Initializing built-in extension RANDR
Initializing built-in extension COMPOSITE
Initializing built-in extension DAMAGE
Initializing built-in extension MIT-SCREEN-SAVER
Initializing built-in extension DOUBLE-BUFFER
Initializing built-in extension RECORD
Initializing built-in extension DPMS
Initializing built-in extension X-Resource
Initializing built-in extension XVideo
Initializing built-in extension XVideo-MotionCompensation
Initializing built-in extension XFree86-VidModeExtension
Initializing built-in extension XFree86-DGA
Initializing built-in extension XFree86-DRI
Initializing built-in extension DRI2
Loading extension GLX
(EE) 
Fatal server error:
(EE) xf86OpenConsole: Cannot open /dev/tty0 (No such file or directory)
(EE) 
(EE) 
Please consult the The X.Org Foundation support 
         at [http://wiki.x.org](http://wiki.x.org)
 for help. 
(EE) Please also check the log file at "/tmp/Xorg.crouton.1.log" for additional information.
(EE) 
(EE) Server terminated with error (1). Closing log file.
/usr/bin/xinit: giving up
/usr/bin/xinit: unable to connect to X server: No such file or directory
/usr/bin/xinit: server error
Unmounting /usr/local/chroots/precise...

---

