---
title: "Last set of upgrades broke fglrx"
date: 2008-11-16
forum: General Help
---

### Post by corwinspyre on 2008-11-16
Hi!  After installing the last set of updates, I rebooted to x being broken.  During the boot process, it says fglrx fails to load, and it eventually takes me to a black screen.  I can ctrl-alt-f# and log in to a console but can't get X back.  The version of fglrx-kernel-source I have installed is 8.552, and I'm running the 2.6.27-8-generic kernel on Intrepid.

After googling around some, I tried using module-assistant to rebuild it, but it comes up with the error:
> "Bad luck, the kernel headers for the target kernel version could not be found and you did not specify other valid kernel headers to use.
However, you can install the header files for your kernel which are provided by the linux-headers-2.6.27-8-generic package. For most modules packages, these files are perfectly sufficient without having the original kernel source.
To install the package, run the PREPARE command from the main menu, or on the command line:
module-assisaant prepare
or
apt-get install linux-headers-2.6.27-8-generic

Previous to this I ran sudo module-assistant prepare, and linux-headers-2.6.27-8-generic is installed.

I also tried sudo dpkg-reconfigure fglrx-kernel-source, which outputted this:
> Removing all DKMS Modules
Done.
Adding Module to DKMS build system
Doing initial module build

Error! Build of fglrx.ko failed for 2.6.27-8-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.552/build/for more information.
Installing initial module

Error! Could not locate fglrx.ko for module fglrx in the DKMS tree.
You must run a dkms build for kernel 2.6.27-8-generic (x86_64) first.
Done.

So, I tried running sudo dkms build -m fglrx -v 8.552, but it also errored out:
> Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
pushd /var/lib/dkms/fglrx/8.552/build; sh make.sh --nohints --uname_r=2.6.27-8-generic; popd....

Error! Build of fglrx.ko failed for:  2.6.27-8-generic (x86_64)
Consult the make.log in the build directory /var/lib/dkms/fglrx/8.552/build/ for more information.

make.log has no useful information.

How do I get it working again?  Thanks!

Please let me know if you need any other information.

---

### Post by Marcus Derekus on 2008-11-16
try booting into recovery mode and choose the **xfix** option

please post results

---

### Post by corwinspyre on 2008-11-16
> **Marcus Derekus said:**
> try booting into recovery mode and choose the**xfix** option

please post results

fglrx still fails to load, but gdm starts and I can log into gnome (since it isn't using fglrx anymore).

---

### Post by Marcus Derekus on 2008-11-16
what graphics adapter are you using?

perhaps you could try completly removing fglrx then go to
System>Administration>Hardware drivers and enable your graphics card

(i have a feeling  that it'll give you the same problem but i'd try it anyway since you can always run xfix)

and tell me your graphics adapter (sorry about repeating, just making sure oyou didnt miss it)

please post results

---

### Post by corwinspyre on 2008-11-17
I have an onboard radeon HD 3200 graphics adapter ("lspci -nn | grep VGA" gives "01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics] [1002:9612]")

I tried removing it via apt-get remove --purge to make sure it was gone, but no luck.

---

### Post by Marcus Derekus on 2008-11-17
Well, if xorg-driver-fglrx doesn't work, and enabling graphics adapter didn't work (probably just tried to install fglrx anyway)

You could try going to [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html) and getting the driver for your card there (make sure you get the linux driver)

that's what i did

BTW fglrx and other graphics drivers are known to have problems when compiz is enabled (usually just blinking graphics but im telling you just in case)

---

### Post by at78rpm on 2008-11-17
Same thing happened with me.  I'm running a ThinkPad with an ATI Radeon Mobility X600 card, and it always gave me headaches with Gutsy.  I had EnvyNG installed to see if it would help, and it did, to some extent.  Anyway, after the last round of updates in Intrepid, Nov. 12, say, fglrx was dead as a doornail.  FAIL was that awful word I kept saying as I tried booting into earlier versions of Linux AND in recover mode.  

Nothing worked until I got to a command line and deleted EnvyNG.  After that, it worked fine -- but with no bells and whistles like 3D graphics.  I backed everything up and did a clean install -- and now everything works beautifully.  Wobbly windows, ATI graphics, fglrx...

So: check to see if you have Envy or any competing graphics software.  It worked for me.

---

### Post by Marcus Derekus on 2008-11-17
yeah i think that might work. 

cuz i had fglrx installed at one point but 3d would blink (I didn't know compiz was the issue). so i tried envy then fglrx would't work any more so i got confused and just got my drivers from [http://www.ati.com](http://www.ati.com)

---

