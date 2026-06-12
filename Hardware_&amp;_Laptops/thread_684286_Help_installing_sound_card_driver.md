---
title: "Help installing sound card driver"
date: 2008-01-31
forum: Hardware &amp; Laptops
---

### Post by ondo311 on 2008-01-31
it is a realtek hd sound card and i'm just having trouble understanding what to do because i am an extreme noob and dont get the instructions... they just arent specific enough

i dont want you to rewrite them for me but, could you like clarify them?  thanks if your willing!

> 1) You must have full configured source for the Linux kernel which you
   want to use for the ALSA drivers. Note that ALSA drivers are part
   of the kernel, so there is necessary to resolve all symbol dependencies
   between the used kernel and ALSA driver code. Partly installed kernels
   (for example from distributor makers) can be unuseable for this action.

2) You must turn on sound support (soundcore module).

3) Run './configure' script.

 * General Options
   If you do not want ISA PnP support, use --with-isapnp=no switch.
   If you do not want sequencer support, use --with-sequencer=no switch.
   If you do not want OSS/Free emulation, use --with-oss=no switch.
   If you have udev or devfs and want to use more than eight cards, use
   --enable-dynamic-minors switch.
   If you want to turn on debug mode, use --with-debug=full switch.
   If you want to debug soundcard detection, try --with-debug=detect switch.

 * Kernel Source Tree
   On 2.4/2.6 kernels, the location of the kernel source tree is
   parsed automatilly from the running kernel.
   If it's not in the standard place, specify the path via
   --with-kernel=<kernel_directory>. 
   On 2.6 kernels, the build directory has to be given via
   --with-build=<kernel_build_dir> option additionally, too.

 * Drivers to Compile
   The card drivers to be compiled can be selected via --with-cards option.
   Pass the card driver name without "snd-" prefix.  To specify
   multiple drivers, list names with comma (,).
   Passing "all" will compile all possible drivers (and this is the
   default choice).
   Some drivers have compile options.  They can be passed via
   --with-card-options option.  Multiple options can be passed with comma,
   too.  The default is "all".
   For available cards and options, see ./configure --help.

 * Example
      ./configure --with-debug=full
      ./configure --with-cards=sb16,emu10k1 --with-card-options=sb16-csp

4) Run 'make'.

5) Run 'make install' as root.
   If you have already a system with ALSA init script, you should install
   just only modules via 'make install-modules' so that the existing init
   script won't be replaced.

6) Run the './snddevices' script to create new sound devices in /dev directory.
   Skip this step, if you have already /dev/snd/* files, or if you're
   using a DEVFS or udev.

7) Edit your kernel module config (either /etc/modprobe.conf or
   /etc/modules.conf, depending on the kernel version). If you are not
   sure, what to do, you may try the alsaconf script available in
   the alsa-utils package.

8) Run 'modprobe snd-xxxx' where xxxx is the name of your card.
   Note: All ALSA ISA drivers support ISA PnP natively, so you don't need
         isapnptools any more.  Don't use both together.  It will
         conflict.  For disabling the ALSA ISA PnP support, specify
         --with-isapnp=no configure switch.

thanks again!

---

### Post by oldsoundguy on 2008-01-31
or .. you could get a Creative sound blaster card and it would install without having to do anything. (and sound a lot better!)

---

### Post by Yellow Pasque on 2008-01-31
> **oldsoundguy said:**
> or .. you could get a Creative sound blaster card and it would install without having to do anything. (and sound a lot better!)
LOL, your answer to almost every problem is to buy new hardware. Anyway...

A user named syxbit was nice enough to script the process. I've modified the scripts to grab the latest version of ALSA. Before you go building new drivers, you should probably try to get the sound working with your current drivers.

What do you get from this command? 
```
cat /proc/asound/card0/codec#* | grep Codec
```

Also, what version of Ubuntu are you running?

---

### Post by oldsoundguy on 2008-02-01
There is a reason behind that .. hardware that WORKS out of the box is just a LOT better to deal with.  I paid 20 bucks for a 5.1 Creative on eBay so it is NOT a bank breaker to consider.  This was to replace ON BOARD REALTEC!  (and as a retired audio engineer .. sounds like a tin can on a string!) I have built 3 Llinux boxes in the last year and have about  200 bucks or so tied up in any of them.  Sound/video and WIRELESS communications went flawlessly.  Trying to beat the crud out of a card that really does not want to work really makes no sense if you value SOME of your time.  A learning experience, fine.  BUT if you really want to REPLACE USING WINDOWS, you have to have a computer that WORKS and to USE.  Dinking with it constantly is just as bad as having to maintain a WinBLOWS box with all of it's need for protection, clean up and constant maintenance.

---

### Post by ondo311 on 2008-02-01
> **oldsoundguy said:**
> or .. you could get a Creative sound blaster card and it would install without having to do anything. (and sound a lot better!)

^^ I'm on a laptop so that aint happenin lol i wish i chould


but when i type that in i get

```
Codec: Realtek ID 268
Codec: Generic 11c1 Si3054

```

---

### Post by Yellow Pasque on 2008-02-01
Ok, it's a Realtek ALC268. See if you can get it working with this thread: [http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

If not, you might need the newer version of ALSA.

---

### Post by ondo311 on 2008-02-01
Thanks and it would definatly help if i knew what i was doing lol

so... i guess i should just try the new version of ALSA?

---

### Post by Yellow Pasque on 2008-02-01
Yes, I would try the newer version of ALSA as the ALC268 is a fairly new chip.

---

### Post by ondo311 on 2008-02-02
ok i have the files loaded onto my deskop.. so i have put in the cd /home/matthew/Desktop    what is the command to actually install it

i think it may have something to do with "get"? i dont know...

---

### Post by Yellow Pasque on 2008-02-02
To run a script:
```
sudo sh ./scriptname.sh
```

---

### Post by ondo311 on 2008-02-02
THANK YOU!! lol the installing of the alsa 1 and alsa 2 worked!!!

so once i get the flash fixed my computer is set


then the advanced settings thingy needs fixed but tahts it!! 80% DONE!!!

---

### Post by Yellow Pasque on 2008-02-02
Cool. Enjoy.

---

