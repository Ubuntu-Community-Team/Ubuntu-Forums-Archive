---
title: "Still no sound cure for Ubuntu on the Lenovo laptop?"
date: 2007-03-04
forum: Hardware &amp; Laptops
---

### Post by JohnGorenfeld on 2007-03-04
There have been some earlier threads about the continuing inability of certain Ubuntu setups to work with the RealTek sound card found on the Lenovo c200 laptop.

In some situations, people have been able to make it work by setting "acpi=ht" on bootup. But elsewhere across the Web,  a number of users say it hasn't worked for them, and the response has been inconclusive.

I'm still struggling to make my laptop speakers play under Edgy. If anyone has made any progress on this, is there an easy, newbie-friendly description for how to get the sound to work on this great machine? I'd love to see a more in-depth discussion of the problem than is out there, including figuring out under what circumstances ACPI interferes with the sound, why it's happening, and what I can do to make my system work.

---

### Post by rubbsdecvik on 2007-03-04
I also am having troubles with my T32 notebook.  If anyone else has any input, I would love to know.

---

### Post by toolish on 2007-03-12
Hi John,

I have the same model laptop, it would be great to see some pointers on the acpi interactions with the sound. I have managed to get this almost fixed (card recognized but needing acpi=ht for speakers)

Here's the steps you need to take to get it working as much as it is at the moment. It's a two-stage fix, basically you compile/install the latest alsa drivers, then the acpi=ht bit. I don't actually do this because if you have enough external amplification the sound is passable and i'd rather have the acpi working properly. It's been made easier recently as the card recognition fix has been commited in the latest alsa rc so no need for hg compiles. Here's the steps:

Open up a terminal, in your home directory make a folder called alsa-src or something similar. Donwnload the latest alsa-driver, alsa-lib and alsa-utils:

```
cd ~
mkdir alsa-src
cd alsa-src
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc3.tar.bz2
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.14rc3.tar.bz2
wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.14rc2.tar.bz2
```

Then we untar and compile each one, Its best to stop alsa at this point.:

```

sudo /etc/init.d/alsasound stop

tar xvf alsa-driver-1.0.14rc3.tar.bz2
tar xvf alsa-lib-1.0.14rc3.tar.bz2
tar xvf alsa-utils-1.0.14rc2.tar.bz2

cd alsa-driver-1.0.14rc3
./configure --with-cards=hda-intel
make
sudo make install

cd ../alsa-lib-1.0.14rc3
./configure
make
sudo make install

cd ../alsa-utils-1.0.14rc3
./configure
make
sudo make install

```

Now we need to select the card so we run alsaconf
```
sudo alsaconf
```
Select the top card, it should mention hda-intel.

Thats the card recognition over with so now we can restart alsa and verify the new driver is loaded:
```
sudo /etc/init.d/alsasound start
cat /proc/asound/version
```
You should see alsa 1.0.14rc3.
Now your card should be recognized properly in the mixer, although the speakers do not work at this point and the sound is very quiet from the headphone jack.

To get the speakers working it is necessary to do the acpi=ht fix. A clean way to do this is to copy your current kernel entry in the grub menu.lst and add acpi=ht to that.
This can vary depending on the kernel you are using. I'll do it for the latest stock kernel. Your root line will probably be different. As will the root=/dev/sda* part of the kernel line. These parts are marked in red.
The easiest way is probably with gedit so:
```
gksudo gedit /boot/grub/menu.lst
```

And find the entry that looks like this:
```
title		Ubuntu, kernel 2.6.17-11-generic
root		[COLOR="Red"](hd0,5)[/COLOR]  #maybe different on your system!
kernel		/boot/vmlinuz-2.6.17-11-generic root=[COLOR="Red"]/dev/sda6[/COLOR] ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot
```

Copy and paste this entry below its current position and add acpi=ht to the kernel line, and modify the title to something recognizable. Make it look like this, new bits in blue:
```
title		Ubuntu, kernel 2.6.17-11-generic [COLOR="Blue"]acpi fix[/COLOR]
root		[COLOR="Red"](hd0,5)[/COLOR]  #maybe different on your system!
kernel		/boot/vmlinuz-2.6.17-11-generic root=[COLOR="Red"]/dev/sda6[/COLOR] ro quiet splash [COLOR="Blue"]acpi=ht[/COLOR]
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

```

Now when you reboot you should see your new kernel option in the grub list, select and hopefully you will now have speakers, albeit with the limitation of the acpi not working properly so no cpu frequency switching, no battery info etc.

I'm still working on the acpi problems, will let you know once a fix is found.

Hope that helps, let me know how it goes for you or if you need further help.

Toolish

---

