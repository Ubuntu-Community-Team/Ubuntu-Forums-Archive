---
title: "Scanner module not loading? (plustek_pp)"
date: 2006-07-16
forum: Hardware &amp; Laptops
---

### Post by fabertawe on 2006-07-16
Hi folks... I'm bumping this from deep within another thread, I hope that's ok ;) 

I've been trying to get my parallel port Plustek OpticPro 4830P working for some time now and I've tried everything I could find. I got it working (almost) as a '[direct]' device with the plustek_pp backend but only xscanimage recognised it as a device and then only as root. I say almost as it couldn't communicate with the scanner anyway.

So I thought I'd try compiling the module and using that. I changed plustek_pp.conf to use '[kernel]' and added pt_drv to '/etc/modules'. I've tried booting with 'apm=on acpi=force' added to the relevant '/boot/grub/menu.lst' entry and I've tried adding 
```
alias char-major-40 pt_drv
options  pt_drv  lampoff=180  warmup=15  port=0x378 lOffonEnd=0  mov=0 slowIO=1 forceMode=0
```
to '/etc/modprobe.conf'.

pt_drv is loading...
```
paul@ubuntu:~$ lsmod | grep pt_drv
pt_drv                126120  0
parport                43532  4 ppdev,pt_drv,lp,parport_pc
```

but is failing to open...
```
paul@ubuntu:~$ sudo scanimage -L
[sanei_debug] Setting debug level of plustek_pp to 128.
[sanei_debug] Setting debug level of sanei_pp to 128.
[sanei_pp] pp_init: called for the first time
[sanei_pp] pp_init: initializing libieee1284
[sanei_pp] pp_init: 1 ports reported by IEEE 1284 library
[sanei_pp] pp_init: port 0 is `parport0`
[sanei_pp] pp_init: initialized successfully
[sanei_pp] pp_calibrate_delay: Delay expected: 1000, real 1016, pp_thresh=0
[plustek_pp] PlustekPP backend V0.43-10, part of sane-backends 1.0.18
[plustek_pp] ># Plustek-PP SANE Backend configuration file<
[plustek_pp] ># For use with Plustek parallel-port scanners<
[plustek_pp] >#<
[plustek_pp] ><
[plustek_pp] >#<
[plustek_pp] ># user either [direct] or [kernel] to access the scanner<
[plustek_pp] ># when using [kernel], device specifies the device-node, which is created<
[plustek_pp] ># by the kernel-module loader (applies only to Linux)<
[plustek_pp] ># when using [direct], device is used to set the parallel-port base address<
[plustek_pp] ># or a device-name suitable for libieee1284, i.e. parport0<
[plustek_pp] >#<
[plustek_pp] >#[direct]<
[plustek_pp] >#device 0x378<
[plustek_pp] ><
[plustek_pp] >#<
[plustek_pp] ># example for accessing the scanner via libieee1284<
[plustek_pp] >#<
[plustek_pp] >#[direct]<
[plustek_pp] >#device parport0<
[plustek_pp] ><
[plustek_pp] >#<
[plustek_pp] ># leave the default values as specified in /etc/modules.conf<
[plustek_pp] >#<
[plustek_pp] >#option warmup    -1<
[plustek_pp] >#option lOffOnEnd -1<
[plustek_pp] >#option lampOff   -1<
[plustek_pp] ><
[plustek_pp] ># model override switch, mostly for cosmetic changes, if the autodetection<
[plustek_pp] ># does not work or could not work correctly<
[plustek_pp] >#option mov 7<
[plustek_pp] ><
[plustek_pp] >#<
[plustek_pp] ># example for accessing the scanner via the kernel module<
[plustek_pp] >#<
[plustek_pp] >[kernel]<
[plustek_pp] >device /dev/pt_drv<
[plustek_pp] Decoding device name >/dev/pt_drv<
[plustek_pp] >#<
[plustek_pp] >option warmup    -1<
[plustek_pp] Decoding option >warmup<
[plustek_pp] >option lOffOnEnd -1<
[plustek_pp] Decoding option >lOffOnEnd<
[plustek_pp] >option lampOff   -1<
[plustek_pp] Decoding option >lampOff<
[plustek_pp] attach (/dev/pt_drv, 0x7fffffaa12e0, (nil))
[plustek_pp] Device configuration:
[plustek_pp] device name   : >/dev/pt_drv<
[plustek_pp] direct I/O    : no
[plustek_pp] warmup        : -1s
[plustek_pp] lampOff       : -1
[plustek_pp] lampOffOnEnd  : yes
[plustek_pp] model override: 0
[plustek_pp] ---------------------
[plustek_pp] drvopen()
[plustek_pp] open: can't open /dev/pt_drv as a device
[plustek_pp] open failed: -1
[plustek_pp] sane_get_devices (0x7fffffaa33e0, 0)
device `v4l:/dev/video1' is a Noname OV511+ USB Camera virtual device
device `v4l:/dev/video0' is a Noname BT878 video (Pinnacle PCTV Stud virtual device
[plustek_pp] sane_exit
```

I would be immensely grateful if anyone has any suggestions as to my next course of action as this is driving me potty!

Cheers ... Paul

---

### Post by fabertawe on 2006-07-17
Ok, couldn't get anywhere with pt_drv so I've reverted to trying the backend again.

It's operational -
```
paul@ubuntu:~$ scanimage -L
device `plustek_pp:parport0' is a Plustek 4830P parallel port flatbed scanner
```
but not an available device for XSane or xscanimage.

However, the following does yield some activity -
```
paul@ubuntu:~$ scanimage -d plustek_pp:parport0
P6
# SANE data follows
248 150
255
scanimage: received signal 2
scanimage: trying to stop scanner
scanimage: sane_read: Operation was cancelled
```

Unfortunately all it does is move the scan head up to the end of the bed and make ratchety noises. That's when I did CTRL-c.

Any ideas folks? I wouldn't still be pursuing this if my scanner wasn't actually supposed to be fully functional! I may give up soon though.

Cheers ... Paul

---

### Post by woodsb02 on 2006-07-23
I am trying to get my Plustek OpticPro 4800P to work with dapper and am having no luck at all.

Nothing recognises it. scanimage, xscanimage... nothing.

I have tried altering /etc/sane.d/plustek_pp.conf... but to no avail.

Its also a parallel port printer.

Any ideas?

---

### Post by fabertawe on 2006-07-24
I'm sorry to say I've actually given up trying. My printer driver (Lexmark Z53) is also supposedly fully functional and compatible but I had to downgrade from 'cupsys-driver-gutenprint' to 'cupsys-driver-gimpprint' to get it working. I no longer have the enthusiasm (or expertise) to waste many hours more on plustek_pp.

Paul

---

### Post by immanueloffice on 2006-08-04
I also had problems with my Plustek scanner - different model, same backend.

Here's how I got it to work (thanks to the devel list for sane!):

1. Bios set to EPP (not ECP) for parallel port

2. Comment out all put net and plustek_pp in your sane dll.conf file

3. Run scanimage -L as root (this was the key for me) - does it show up?

4. Run xsane as root (not recommended - you get warnings). I am working now on getting xsane to recognize my scanner as a normal user.

I am able to scan and ocr an image with xsane.

Hope this helps.

---

### Post by immanueloffice on 2006-08-04
I got my scanner to work without being root. Here's what worked for me:

I changed quite a few things, so I don't know if they all need to be changed. The last thing I changed that made it work was to add my user to the lp group by editing /etc/group and then logging in again.

Other things I changed along the way that might have affected it:

1. Uncommented sane-port in /etc/services

2. Added / edited file sane-port in /etc/xinet.d/
**Restart xinetd after this change**

# default: off
# description: The sane server accepts requests \
# for network access to a local scanner via the \
# network.
service sane
{
        disable = no
        port            = 6566
        socket_type     = stream
        wait            = no
        groups          = yes
        user            = root
        group           = root
        server          = /usr/sbin/saned
}

3. added 'localhost' line to /etc/sane.d/saned.conf and /etc/sane.d/net.conf

4. Uncommented 'net' line in /etc/sane.d/dll.conf (near the top)

---

### Post by fabertawe on 2006-08-05
A thousand thankyous immanueloffice for taking the time to post! :D 

First the good news... by implementing things from your second post (i'd already tried everything in the first) my scanner is available from xsane (non root)!

Now the bad news... the head moves to the end of the bed with the lamp off and just judders there until I get the 'device i/o' error.

Oh, so close ](*,) ...ah well, another reason to keep dual booting Windows unfortunately.

Thanks ... Paul

---

