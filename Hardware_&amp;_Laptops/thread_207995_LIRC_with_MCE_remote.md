---
title: "LIRC with MCE remote"
date: 2006-07-02
forum: Hardware &amp; Laptops
---

### Post by Mateo on 2006-07-02
I'm attempting to install LIRC with the MCE remote (the philips kind).  I am following these instructions:  []("http://www.mythtv.org/wiki/index.php/MCE_Remote#Media_Center_Remotes")

I am attempting to compile from source.  I do the .setup.sh and the configuration runs, and this is what it ends with:

```

checking for which drivers can be installed on this system...
checking for caraca_init in -lcaraca_client... no
checking for ir_strerror in -lirman... no
checking for ir_strerror in -lirman_sw... no
checking for portaudio.h... no
checking for alsa/asoundlib.h... no
checking for scsi/sg.h... yes
checking for linux/input.h... yes
checking for sys/soundcard.h... yes
configure: error: *** you need to have the Linux kernel source installed
        for this driver

```

Taking advice from others, I went on synaptic and got 'linux-kernel-devel', 'linux-headers-2.6.15-25', 'linux-headers-2.6.15-25-386', and 'build-essential' but get the same error.  Anything else i should be getting/doing?  Thanks!!!!

---

### Post by Mateo on 2006-07-04
bump, anyone know what's going on or can point me in the right direction?

---

### Post by kuja on 2006-07-05
How very odd, the linux-headers package should be what you need to correct that error, in fact, I just went through this within the last half hour (thus how I accidentally found the thread). Are you sure you've got the right linux headers package... run "uname -r" in a terminal and check that you've got exactly the right version... who knows, maybe it's not the right one?

---

### Post by Mateo on 2006-07-05
hmm, I reinstalled the drivers and it seemed to work.  great!  I used LIRCD and tested it.  However in this part, [http://www.mythtv.org/wiki/index.php/MCE_Remote#Media_Center_Remotes](http://www.mythtv.org/wiki/index.php/MCE_Remote#Media_Center_Remotes)

it says:

> If everything works, then autoload lirc_mceusb2 when your computer loads (how to depends on your distro) and start lircd as well (also depends on your distro).

how do you autoload these two in Ubuntu?  thanks!

---

### Post by Mateo on 2006-07-06
Anyone as to how to automatically run "modprobe lirc_mceusb2" and "lircd" when my computer starts?

---

### Post by cracker on 2006-07-07
Add lirc_mceusb2 to /etc/modules for the kernel module. As for starting lircd, you need to add it to the RC scripts, which I am completely unfamiliar with. Someone else, or a thorough search of the web, should be able to get you going there.

---

### Post by Mateo on 2006-07-07
anyone know how to load LIRCD when i boot?

---

### Post by kuja on 2006-08-12
The post is aging, but I finally figured out a way to do it, if you're still interested, and alive.

```
cd /etc/init.d
sudo touch startlirc.sh
sudo chmod +x startlirc.sh
kdesu kate startlirc.sh OR sudo gedit startlirc.sh
```

In the empty file, put this, and then save.
```
lircd
```
Afterwards, to finish things up
```
sudo update-rc.d startlirc defaults
```

And that should do it.

---

### Post by aussiedude on 2007-02-19
I was having similar problems to Mateo, turned out to be I had the wrong kernel-source for my kernel version.
I'm still having issues though, make is giving me an error:
```
make[5]: *** [/usr/src/lirc-0.8.1/drivers/lirc_dev/lirc_dev.o] Error 1
make[4]: *** [_module_/usr/src/lirc-0.8.1/drivers/lirc_dev] Error 2
make[4]: Leaving directory `/usr/src/linux-2.6.15'
make[3]: *** [lirc_dev.o] Error 2
make[3]: Leaving directory `/usr/src/lirc-0.8.1/drivers/lirc_dev'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/usr/src/lirc-0.8.1/drivers'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/src/lirc-0.8.1'
make: *** [all] Error 2
```
Any idea what is wrong here? I'm a noob when it comes to compiling code.

---

