---
title: "Acer Travelmate 8103"
date: 2005-07-05
forum: Hardware &amp; Laptops
---

### Post by dorris on 2005-07-05
Hi, got one of these badboyz last week, spent the rest of this week trying to make it work, found a lot of resources all over the web, of others running into my same problems, put together a complete howto from top to bottom to get the laptop to a nice useable state, if anyone else gets one, let me save you the hassles, heres what I did, it now works .... OK.
video                                  :    works
LAN                                    :    works
Wireless                              :   works 
sound                               :   works under ESD/ALSA
CD/DVD-write                    :works under certain apps
pcmcia                             :   Broken
cpu freq scaling               :   Scales between 800-1800  \\:D/ 
Battery status                    :   Works
bluetooth                          :   Works
BLuetooth light/button      : Works
wireless light/button          : Works
card-reader                       : Untested
infra-red                            : Untested
bluetooth                          : Works
ACPI functions                   :Some work

TO Install, I had to use bootstring:
```
linux vga=771 noapic
```
this causes pcmcia to crash on detection in install, so it requires another switch, can't remember the specifics of it, its in one of the f1:f6 options, it says something about installer, don't detect pcmcia

once installed, I couldn't get into X at all, but the system hadn't hung, terminals still worked, ie ctrl+alt+F2.
using a terminal + vi, I edit ```
/etc/X11/xorg.conf
```
add line ```
	Option		"MonitorLayout"	"LVDS,AUTO"
``` to end of Device section.

then upon reboot, X should happily start, if you don't want to reboot, type ```
sudo /etc/init.d/gdm restart
```

you will notice that video now works, but not sound, and some of the network interfaces, obviously ACPI is non-existant.

go to /boot/grub  , and edit menu.lst , remove the option ```
vga=771
```
also change it in the defaults section, to avoid this change with every new kernel y

by now, the only thing that really works is my vga, no wireless/bluetooth/sound/acpi
NOW WE GET TO THE FUNSTUFF

I changed my repo sources to breezy for a moment, downloaded linux-source-2.6.12 (2.6.12 kernel with ubuntu patches)
then changed my sources back to hoary

to compile the kernel, I extracted the sources into /usr/src folder, it created a folder /usr/src/linux-source-2.6.12

for the rest, use[Luca_linux howto](http://ubuntuforums.org/showthread.php?t=43065&page=1&pp=10) , although I recommend replacing ```

sudo make-kpkg --append-to-version=-custom kernel_image modules_image

``````
sudo make-kpkg --append-to-version=-custom binary modules_image

```
to also get debs with kernel headers etc, so kernel/headers can be installed on new install, without compilation again.

to save anyone else the troubles of config files, I will attach mine, so all that is required is to copy my config file to /usr/src/linux/.config
.config adds modules necessary for ACPI, sound driver, as well as IPW2200 functionality (the drivers themselves didn't quite do the trick)
wifi is in the wireless networkingg section somewhere, ipw2200
sound is under section:
sound driver, ALSA->PCI->High definition audio

If the forum permits, I'll also upload my kernel, to really save trouble!

compile the kernel.
after a whole whack of dsdt debugging (found a very helpful resource in the end on the gentoo forums), and came out with a clean compile on iasl v20050309, my dsdt's will be attached.
I recommend adding a custom dsdt to the kernel before compile time, alternatively, the table can be slapped into the initrd.

after the kernel is compiled, and installed, ie
```
dpkg -i kernel-***-2.6.12*.deb 
cd /boot
sudo mkinitrd -o /boot/initrd.img-2.6.12-*YOURKERNELNAME* 2.6.12-*YOURKERNELNAME*

```

add the line ```
initrd          /boot/initrd.img-2.6.12-*YOURKERNELNAME*

```
into /boot/grub/menu.lst, under your new kernel entry

voila!

to fix the supercool wifi light/button, to know WTF ITS TRYING TO DO, create the file
```
/etc/modprobe.d/ipw2200
```
containing line
```
options ipw2200 led=1
```
Now when you reboot into your new kernel, upon hotplug init, you should see the orange light start flashing!
if wifi still is not working as expected, which I doubt it will , copy the latest firmwares from the ipw2200 project into the hotplug firmware folder: /lib/hotplug/firmware


ONce rebooted, go to systems selector, and ensure ESD is preferred device.
To get ALSA working, use the howto (I can't remember the location, but it was explained on these forums recently)

also, the cd/dvd write functionality was very problematic in gnomebaker, and k3b, the reason for this, is the mount device ubuntu installer chooses for the cd/dvd-writer, modify the file 
/etc/fstab, and change the device for cd/dvd-w to 
```
/dev/sr0
```


Now, if anyone has got ACPI working properly, I will be most grateful for the assistance, in particular, battery status/pcmcia . its probably my incorrect debugging of dsdt table, so anyone else can have a go! :razz: 

****************************EDIT*********************************
Finally , did it, uploaded a new dsdt table, with the new one, battery status works, only hibernation and PCMCIA is now an issue. Since I won't be needing it for a while, I won't be bothering to go any further with this.
****************************EDIT*********************************


Attached are files that will be of interest

kernel files contains my config, as well as 2 files that were modified slightly to enhance cd/dvd-r functionality
dsdt.tar.gz contains my dsdt folder
Tried to attach kernel deb, but was too big!

---

### Post by MrLizard on 2005-09-08
Hi Dorris,

First, thanks for your helpful How-To, it's got me much further than i was before...

Unfortunately, I have no idea how to go about adding the dsdt table to the kernel.  everything else is straightforward and perfectly spelt out but you seem to have skipped over something major here...

Thanks

---

### Post by dorris on 2005-09-09
[QUOTE=MrLizard]Hi Dorris,

First, thanks for your helpful How-To, it's got me much further than i was before...

Unfortunately, I have no idea how to go about adding the dsdt table to the kernel.  everything else is straightforward and perfectly spelt out but you seem to have skipped over something major here...

Thanks[/QUOTE]
 Hey MrLizard, thats very true...
i didn't really go into it, coz theres just so many ways to do it, some people have mentioned a way of slapping it into the INITRD once the kernel is compiled, I'v never really tried it, for me, what worked, was to insert the option into the kernel at compiletime.

I can't really remember where the option was, when I get home, I can take a look.
but google around a little, and see what u come up with.

ok... I'll be extra nice, a little later today, I'll upload the kernel-image.deb and kernel_sources.deb files to my local webserver, will put up url once its done.

so u can get the patched files straight.
cheers

---

### Post by MrLizard on 2005-09-09
Hi Dorris,

That would be soo awesome if you do that!  i've been battling with this for about 3 days now and wasting precious time i should be spending doing real work.

incidentally, i mentioned my struggles to some hardcore fedora fans the other night and ubuntu seemed to draw some hefty snorts of contempt...help me prove them wrong!

---

### Post by dorris on 2005-09-11
The kernel files should be in the folder [http://dorris.no-ip.com:30000/apt/kernel/](http://dorris.no-ip.com:30000/apt/kernel/)

you will need the kernel-image file, and if u might ever need the headers,  I would download them now too.  
As I am hosting them on my local machine, chances are, at next OS reload, the files will be gone.
install using dpkg -i kernelfile.deb

in regards to distro rivalry, it will always be there, theres a lot of upset from many communities about the ubuntu project. its too new, and too big for many peoples liking.

---

### Post by MrLizard on 2005-09-11
fantastic, thanks, it's downloading just now...

i've also just managed to compile the kernel, following your instructions and sticking the dsdt.hex into the source folder and hoping your config file would tell it what to do...

i've no idea whether this should've worked (in case you hadn't guessed, i'm totally new to doing anything with the kernel and have only actually been using linux at all for a couple of months) but it hasn't.

i've got a sneaking feeling i should probably tell you i got greedy when i ordered this laptop and got a memory upgrade....does this mean your dsdt isn't valid for me?

i did, at one point, get hold of the iasl compiler on the instructions of someone on linuxforums.de but, since the whole thing is in german, i didn't get terribly far. (in fact it took me a while to even realise that google had 'translated' bits of code for me...)  I did however, manage to produce some dsdt files that might be valid for me so that might also be worth a shot

another question:  if the acpi is up and running properly, will my usb mouse work nicely? seems pretty slow just now using the kernel i just compiled (and no, it's nothing to do with the mouse speed).  i googled and this seems like it might be a generic linux issue

---

### Post by dorris on 2005-09-11
dsdt is valid for any 8103 with default hardware, the RAM won't affect it at all
using my kernel , I can use a usb mouse, althoughI have noticed that a usb mouse sometimes causes the system to hang, unsure y.

to test if your dsdt table is in action, either install the gnome battery indicater, or type 
```

cat /proc/acpi/battery/BAT1/state
```
if it returns useful info, the dsdt has been implemented.

---

### Post by MrLizard on 2005-09-11
hmm...

oddly enough, i couldn't quite get your kernel image to work on this machine, i'm probably using the wrong kernel option or something.

no matter though, i ended up recompiling with my own dsdt.hex which was, again, unsuccessful (possibly because i was using source without custom dsdt enabled, i'm not sure)

so, having a  kernel which appeared to be fully functional except for acpi (without your .config file, i couldn't even get sound), i found out an easy way to get my own DSDT.aml to load into the initrd and the correct kernel option (noapic) to get rid of the pcmcia. ..still no joy.

until i found: [http://www.ubuntuforums.org/showthread.php?p=245101#post245101](http://www.ubuntuforums.org/showthread.php?p=245101#post245101)

namely, the part:

1. boot into recovery mode
2. execute: dpkg --purge pcmcia-cs

which appears to have successfully eliminated the blasted pcmcia stuff (not an issue for me at all...the only gadget i have with such a card is my phone, which has usb, bluetooth and infrared so it would actually be *more* hassle to use the card slot)

i also have sound, which is good news, so do i need to worry about ALSA?  i'm not entirely sure what it is...

Thanks soooo much for your help again, i was starting to think i might actually have to rely on CYGWIN or something for a decent level of functionality.

---

### Post by dcardamo on 2005-10-23
Hi,

I'm using breezy and followed these directions and I'm stuck on the ACPI part.  I tried the binary kernels that are linked to in this thread but they just crash on me early in the boot process.

When I patch my kernel by running:
```

echo -n "INITRDDSDT123DSDT123" >> initrd-2.6.12-custom
cat DSDL.aml >> initrd-2.6.12-custom
echo -n "INITRDDSDT321DSDT321" >> initrd-2.6.12-custom

```

I get no working acpi sound, wireless, and cat of proc/acpi/batter/BAT1/state don't work.

If I run dpkg --purge pcmcia-cs it wants to remove ubuntu-desktop which I'm sure I don't want to do.  So I just removed the link in /etc/rc2.d that was starting it and I'm still without a working acpi.

Have either of you upgraded to breezy, and if so can you give me some tips or your binary kernels images?

Thanks,

Dan

---

### Post by dorris on 2005-10-23
[QUOTE=dcardamo]Hi,

I'm using breezy and followed these directions and I'm stuck on the ACPI part.  I tried the binary kernels that are linked to in this thread but they just crash on me early in the boot process.

When I patch my kernel by running:
```

echo -n "INITRDDSDT123DSDT123" >> initrd-2.6.12-custom
cat DSDL.aml >> initrd-2.6.12-custom
echo -n "INITRDDSDT321DSDT321" >> initrd-2.6.12-custom

```

I get no working acpi sound, wireless, and cat of proc/acpi/batter/BAT1/state don't work.

If I run dpkg --purge pcmcia-cs it wants to remove ubuntu-desktop which I'm sure I don't want to do.  So I just removed the link in /etc/rc2.d that was starting it and I'm still without a working acpi.

Have either of you upgraded to breezy, and if so can you give me some tips or your binary kernels images?

Thanks,

Dan[/QUOTE]


I haven't tried upgrading to breezy, using gentoo on laptop now.
my advice:
if u using the initrd method to bring in dsdt, I would not use my binaries and config, try the breezy kernels, I'm sure they enabled snd-hda in their kernels
which should give you sound.

If you're acpi is not working, its probably coz the dsdt table has not been pushed into the initrd properly, I have no experience working with it, but, what is DSDL.aml, shouldn't it be dsdt.aml??

did the dsdt tables compile succesfully?
removing the pcmcia link would be sufficient to stop it running, if you're system isn't crashing on boot, pcmcia is not running.

my advice,
1. run the std breezy kernel (boot with noapic)
2. do an "lsmod" and check if any hda_intel modules are loaded, if so, sound is configured in kernel for your laptop, try check the multimedia systems selector, and see if u can get sound on alsa/esd, also check mixer options, try push up headphones, pcm, front, some drivers separate front speaker volume from headphone, but defaults headphone to gnome volume control!
3. all that you require now is a dsdt table. (nothing more to do with kernel if using initrd method) otherwise, download breezy source packages, do a make oldconfig, and then follow steps to add dsdt.hex into kernel during make menuconfig, and install the kernel 
good luck

---

### Post by dcardamo on 2005-10-23
Thanks dorris.  I'm up and running now with ACPI.  I'm using the breezy kernel, downloaded the 8104 3c22 DSDT from acpi.sf.net and put it in /etc/mkinitramfs/DSDT.aml so that dpkg-reconfigure linux-image would pick it up.

I can cat my battery now and it works.  And my wifi led comes on so I think that's working also (didn't spend time to figure out wpa yet).  I'll look at the sound card next.

Thanks for the help.

---

### Post by Asraniel on 2005-10-23
for sound, you just have to unmute it!

---

### Post by fiss on 2005-11-14
[QUOTE=dorris]The kernel files should be in the folder [http://dorris.no-ip.com:30000/apt/kernel/](http://dorris.no-ip.com:30000/apt/kernel/)

you will need the kernel-image file, and if u might ever need the headers,  I would download them now too.  
As I am hosting them on my local machine, chances are, at next OS reload, the files will be gone.
install using dpkg -i kernelfile.deb

in regards to distro rivalry, it will always be there, theres a lot of upset from many communities about the ubuntu project. its too new, and too big for many peoples liking.[/QUOTE]
Hi, Thank you for your advice but i can't reach your webserver where you have uploading your special kernel. Can you check your websever or send me the kernel please ?

---

### Post by christgod on 2005-11-19
I'm trying to install Ubuntu 5.10 on my Travelmate 8101WlMi, but I'm running into a few problems not mentioned here:

1. USB is not working properly. My mouse is skipping as if usb was working with only 5hz. USB stick/hd not recognized at all.

2. Networking doesnt work. I have a simple NAT at home, DHCP should do the job, I also tried setting it up manually, but it doesnt work.

Is it a good idea to try the new 2.6.14 kernel?

Which kernel boot arguments could I try?

---

### Post by strandlooper on 2005-11-20
I'm running complite the same laptop but not one of your problems I have faced. There must be something else. Breezy worked out of the box exept battery status.

---

### Post by tOpEzz on 2005-11-22
hurmmm nice nice... i wonder why some laptop that i want to install ubuntu cannot work/boot... i ever try using acer laptop that using intel processor?? but i install on the amd processor i can boot.. anyone can help me??

---

### Post by cougem on 2005-12-05
Hey  thanks so much for the help. I'm compiling with your config though, and I'm getting an error after answering those questions, when its compiling, which says:

  CC      fs/inode.o
fs/inode.c:1093: error: static declaration of ‘generic_drop_inode’ follows non-static declaration
include/linux/fs.h:1418: error: previous declaration of ‘generic_drop_inode’ was here
make[2]: *** [fs/inode.o] Error 1
make[1]: *** [fs] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.12'
make: *** [stamp-build] Error 2


Do you know what could be causing this?
Many thanks,

cougem

---

### Post by DerekRom on 2006-03-09
As a new Ubuntu member, I think I had a certain amount of luck in finding the information I wanted on hindsight. I saved the place where I found the information, but have since been unable to navigate to spot otherwise. I even passed the information on to another query. And in turn was solicited for help. I got my graphical mode working , on a TravelMate 8104, by editing the file: /etc/X11/xorg.conf in the way suggested, but have no idea how or why it worked, but it did, so I can now more easily explore the Breezy Badger Linux system. Thankyou!

---

### Post by avatar-1 on 2006-03-29
[QUOTE=christgod]I'm trying to install Ubuntu 5.10 on my Travelmate 8101WlMi, but I'm running into a few problems not mentioned here:

1. USB is not working properly. My mouse is skipping as if usb was working with only 5hz. USB stick/hd not recognized at all.

2. Networking doesnt work. I have a simple NAT at home, DHCP should do the job, I also tried setting it up manually, but it doesnt work.
[/QUOTE]

I had this problems after playing around and upgrading Breezy to Dapper.

The problem was the new kernel which won't work out of the box with correct IRQ Plug'n'Play.

It works like a charm with this kernel options in grub:
ro quiet splash noapic acpi=off pci=biosirq pci=assign-busses irqpoll

Good luck, avatar.

---

