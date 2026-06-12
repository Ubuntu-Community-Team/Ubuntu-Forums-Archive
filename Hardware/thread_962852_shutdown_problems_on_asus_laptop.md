---
title: "shutdown problems on asus laptop"
date: 2008-10-29
forum: Hardware
---

### Post by d34th on 2008-10-29
Hi

I've installed ubuntu 8.10 in an asus x50gl (f5gl motherboard), and it fails to power of the system.

The lower half of the screen displays weird stuff (~artifacts) and the system remains blocked,
Hard drives seem to be stopped, but the system is still on (screen, fans...)

I also have problems with the battery charge levels, and special keys (screen brightness, volume wifi...) I think they could be related (acpi?)

If anyone need more info, just ask :)

Greetings from Spain

---

### Post by dixon on 2008-12-04
Hi,
did you manage to solve this problem? My friend bought the same laptop as you have and he has the exact same problems...

---

### Post by sahmed001 on 2008-12-04
If it has intel audio try turning that off and then shut down

modprobe -r snd-hda-intel or whatever the audio module is. You can check using the lsmod command. 

If that works then add the line in the halt script.

---

### Post by sahmed001 on 2008-12-04
If it has intel audio try turning that off and then shut down

modprobe -r snd-hda-intel or whatever the audio module is. You can check using the lsmod command. 

If that works then add the line in the halt script.

---

### Post by galv on 2008-12-11
> **d34th said:**
> Hi

I've installed ubuntu 8.10 in an asus x50gl (f5gl motherboard), and it fails to power of the system.

The lower half of the screen displays weird stuff (~artifacts) and the system remains blocked,
Hard drives seem to be stopped, but the system is still on (screen, fans...)

I also have problems with the battery charge levels, and special keys (screen brightness, volume wifi...) I think they could be related (acpi?)

If anyone need more info, just ask :)

Greetings from Spain
Same laptop, same issues :(

Greetings from Portugal

---

### Post by jorl17 on 2009-01-17
Greetings from Portugal here too.

I have the same exact issues, right now I'm compiling my kernel with support for Asus ACPI and, in case it doesn't work, I'm compiling it without ACPI enabled.

I do not have any sound issues, only these (i think ACPI-related) issues.

If anyone has any advice please tell me.

P.S: The 'artifacts' are always the same and seem to be the repetition of a scaled down area of the gfx card RAM (the one that contains the end of the progress bar)

---

### Post by crislosi on 2009-01-23
I have the same problem with this laptop, I know the error is in the kernel 2.6.27. This error are in Suse 11.1, Debian Sid, etc. I've installed the kernel 2.6.28 and the error remains again.
I think the error is in the kernel there is an error when reads some memories direction, but i don't hnow how resolving this problem.
The problem is not with sound card nor acpi, I've tried editing all different options in the grub but nothing worked fine.
I've notified this error in launchpad web page but nothing de nothing
Thanks

---

### Post by galv on 2009-01-23
> **crislosi said:**
> I have the same problem with this laptop, I know the error is in the kernel 2.6.27. This error are in Suse 11.1, Debian Sid, etc. I've installed the kernel 2.6.28 and the error remains again.


I think that maybe this issue may only be solved with kernel 2.6.29 :(
[http://bugzilla.kernel.org/show_bug.cgi?id=11884](http://bugzilla.kernel.org/show_bug.cgi?id=11884)

---

### Post by jorl17 on 2009-01-23
I don't know which of these problems are you talking about.

I compiled the kernel with extra asus acpi stuff, yet it didn't work. (also I would need restricted modules recompiled for my wireless card and I'm not up for that soon).

About the 'artifacts' problem:

Recently I messed with my NVIDIA drivers and had a huge mess. During this mess I lost X, I lost GDM, I lost all drivers, then I got them back, but what matters is that some of the times this bug was not visible.

It could either be related to:

a) NVIDIA driver not loaded (I'd scratch that, since I disable modules once and it still happened)

b) X11 not loading (because NVIDIA driver did not respond)

c) Display-resolution changes (seems likely, let me explain: I think that ubuntu boots up in a resolution that is different from the one we use, I'm with 1280x800. As I said, I once booted with NVIDIA drivers disabled and this happened, but when I booted up in another resolution it didn't happen)

So, I still don't know what made that go away, since I went through allot to get my NVIDIA drivers back.

---

### Post by raster on 2009-01-25
I've been doing some tests.

At LinTop ([http://www.linlap.com/wiki/asus+f5gl]("http://www.linlap.com/wiki/asus+f5gl")) I found that an user reported that Knoppix was able to power off the laptop. I tested it and is true. It has kernel 2.6.24-4.

I tried older versions of Ubuntu to check if some of them have the same kernel version and works, but 7.10 fails to boot, hiding the boot splash and showing an InitRam terminal. Version 8.04 fails to boot too, but in a different way: it loads the kernel and remains in that point for a long time; it never starts to launch the INIT scripts.

While booting, I saw that Knoppix loads an ACPI module called ASUS-ACPI. Maybe...

---

### Post by raster on 2009-02-20
At [LinLap]("http://www.linlap.com/wiki/asus+f5gl") a user posted a patch for the ACPI subsystem that seems to fix some (not all) of these problems. The link is here:

[Patch for the kernel (http://patchwork.kernel.org/patch/1478/)]("http://patchwork.kernel.org/patch/1478/")
[Bug explanation (http://bugzilla.kernel.org/show_bug.cgi?id=11880)]("http://bugzilla.kernel.org/show_bug.cgi?id=11880")

What would I do to make this patch enter in current versions of Ubuntu? (Maybe in Backports?)

---

### Post by anthonie on 2009-03-04
> **raster said:**
> I've been doing some tests.

While booting, I saw that Knoppix loads an ACPI module called ASUS-ACPI. Maybe...

I assume you used a non-official 64bit version of Knoppix. Which one and where did you get it? I tried one I found on the net and only got a kernel panic as a result. 

I have written to the techs (and posted at the crappy forum) at Asus to see if they have a solution. 
[http://vip.asus.com/forum/topic.aspx?board_id=3&model=X50Gl&SLanguage=en-us](http://vip.asus.com/forum/topic.aspx?board_id=3&model=X50Gl&SLanguage=en-us)

After way too much digging, reading etc, I found this thread at the Gentoo forums:

[http://forums.gentoo.org/viewtopic.php?t=122145](http://forums.gentoo.org/viewtopic.php?t=122145)

That seems to describe pretty well where the problems with the X50GL/F5GL are. So far, no reaction from the Asus-tech's (Not that I'm surprised about that ofcourse).

What I'd like to know is whether future kernels will have a support for the DSDT/ECDT functionality from these specific Asus laptops.

---

### Post by anthonie on 2009-03-08
Yesterday I was fiddling around a little bit. To my surprise I found I still had the old 2.4.22 kernel laying around, although I had removed the entry from my grub. (I installed 8.04 on this machine and upgraded from there)

So I got the liveCD (AMD64) back from a friend and yes, it actually works. Powerdown, power management, the whole thing is functioning fine. 

So, now I'm looking for a way to fix it from here. Anyone who's able to give me some pointers as what to look for and recompile instructions?

Regards,

Anthonie

---

### Post by jorl17 on 2009-06-22
Well, I finally solved these problems and I'm going to give you a little how-to.

Beware that I shall never be held guilty for anything that happens after you do what is here. I WARN YOU THAT THESE PROCEDURES MIGHT MAKE YOUR COMPUTER MALFUNCTION OR EVEN PREVENT IT FROM RUNNING THE KERNEL.

Given that, be sure to carefully read what I type, so you understand what is going on.

All these problems (except for the artifacts on shutdown) were notoriously related to ACPI-related bugs. However, they were not present in older kernels (such as 2.6.24.1). This is why knoppix and Ubuntu 8.04 worked -- they were using an older kernel.

I will not describe what the bug is, but rather tell you that, to fix it, you need to recompile your kernel with a supplied patch. (Found here: [http://bugzilla.kernel.org/show_bug.cgi?id=11880](http://bugzilla.kernel.org/show_bug.cgi?id=11880) specifically here: [http://bugzilla.kernel.org/attachment.cgi?id=18906](http://bugzilla.kernel.org/attachment.cgi?id=18906))

It was tough to finally get a kernel recompile working, it had been ages since I had last tried.

If you aren't a Free Software "all-hands-go" advocate, you are probably OK using NVIDIA gfx binary drivers, which means you have enabled the proprietary NVIDIA drivers. These seem to mess up multiple things in our X50GL, so I uninstalled them a long time ago and installed the most up-to-date ones.

I can not remember how I *really* uninstalled them, but I think that I:

[SIZE="4"]Removing NVIDIA video drivers and preparing new ones[/SIZE]

(Beware that this might temporarily render your laptop unusable in terms of a graphical environment)

Removed every nvidia related package and purged it (sudo apt-get purge nvidia*) and DID NOT REBOOT

After that, I searched for any NVIDIA video module and removed it (moved it to a 'safe' folder) (find /lib/modules | grep nvidia.ko)

Done with this, I went into the NVIDIA drivers section and downloaded the most up-to-date ones (at the time of writing, these are, for our X50GL's "GeForce 9200M G": [http://www.nvidia.com/object/linux_display_ia32_185.18.14.html](http://www.nvidia.com/object/linux_display_ia32_185.18.14.html) )

I saved that file into a folder named nv_work in my home directory.

[SIZE="4"]Getting the new kernel[/SIZE]

( Check [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile) for more info )

Then, I got the kernel packages for my current kernel. $(uname -r) [Could also be `uname -r`] dictates our running kernel's name.
```
sudo apt-get build-dep linux-image-$(uname -r)
apt-get source linux-image-$(uname -r)
```

Then, I extracted the kernel source and got ready to compile it (I also switched into my usual src folder in the home directory (create it if you don't have it):
```

sudo apt-get install linux-source device-tree-compiler # device-tree-compiler is only needed if you are targeting the PowerPC architecture. We are not...
cd ~/src

```

Now, since you have never compiled a kernel, it might be safe to say you only have one package, so this command should do the trick:

```
tar xjvf $(ls /usr/src | grep linux-source)
```

If it fails, check what your linux-source package is inside /usr/src, mine was "linux-source-2.6.27.tar.bz2"

Next thing is to cd into our kernel directory:

```
cd linux-source-*
```

Now you may want to reuse your current kernel config and execute the following:

```
cp -vi /boot/config-`uname -r` .config
```

But I have already enabled ASUS extras in my kernel's config, as well as as 3 built-in NTFS modules into the kernel and a couple of EXPERIMENTAL things. I attached it, you might just extract it into your linux-source-xxx folder and overwrite the existing one

You can check what is enabled by using the 'xconfig' utility:

```

sudo apt-get install qt3-dev-tools libqt3-mt-dev
make xconfig

```

After that, you need to apply this patch: [http://bugzilla.kernel.org/attachment.cgi?id=18906](http://bugzilla.kernel.org/attachment.cgi?id=18906) .

If you don't know how to apply patches and don't care to learn, you can simply read it and understand that it's just a job where you look for some lines of code here and there and replace them. If there is a minus ('-') you remove that line and if that is a plus ('+') you add that line. At the top there is a line indicating which file and function we're replacing.

With the patch applied we can compile the kernel. You better be ready to wait for a loooong time.

```

export CONCURRENCY_LEVEL=3 #Our X50GL has two cores
fakeroot make-kpkg --initrd --append-to-version=jorl17s-own-kernel kernel-image kernel-headers

```

Replace "jorl17s-own-kernel" with whatever identifier you want to have connected to your kernel. The final output from my compile became: 2.6.27.18jorl17s-own-kernel

By now you should have the kernel compiling. Once it is done you will be able to see the 'blinking terminal cursor' again.

Now, before we start installing the kernel, I should warn you that I had some troubles getting through with its install. Unfortunately I can not precise where it was, but there is a file named nvidia-common somewhere (in a DKMS directory) which you have to rename to nvidia-common_, and chmod -x so that it doesn't try to get installed (which will fail)).

So, let's install the new patched kernel:

```
echo vesafb | sudo tee -a /etc/initramfs-tools/modules
echo fbcon | sudo tee -a /etc/initramfs-tools/modules
cd ..
sudo dpkg -i linux-image-*.deb #This is where the error that I mentioned might occur
sudo dpkg -i linux-headers-*.deb

```

Great, now we have a new kernel installed and upon reboot we should be ready to go. But there's a problem -- We still have to workaround the NVIDIA-drivers!

[SIZE="4"]Rebooting and Installing the NVIDIA modules[/SIZE]

Reboot your computer and you'll probably be facing an X Server error when you boot-up. Don't worry and press CTRL+ALT+F4. Now, in here, type the following (after you've logged in):

```
sudo pkill -sigkill gdm
sudo pkill -sigkill Xorg

```

This should probably have killed gdm and Xorg, so you should be ready to install the modules. Remember that I told you to save them in a folder named nv_work in the home directory? Let's changed directory into it:

```

cd ~/nv_work #Or wherever your NVIDIA binary drivers are
sudo sh *.run #If there is only one .run file

```

Go on with the install. You might choose not to reboot and simply run:

```

sudo /etc/init.d/gdm start

```

But I advise you to reboot. Hopefully now you should have the battery meter working, as well as the CPU sensor and other ACPI fixes. Fn keys should work and a nasty recent kernel bug that made the screen go black should also be fixed. The PC actually shuts down! What remains are artifacts.

Check that there are no errors with:

```
dmesg | grep ACPI
```

Hopefully there shouldn't be any errors and you're ready to roll.

[SIZE="4"]Ready to go![/SIZE]
Now remember that you are running a custom kernel with a proprietary NVIDIA module not supplied by Ubuntu. This means you will receive less support, since you are not under normal conditions. Also, any additional modules you compiled will have to be recompiled against this new kernel.

I hope this was helpful. I decided to share it because it had been pissing me off for so long. It is good to see my CPU temperature now.

Well, greetings from your Portuguese friend,

Jorl17

---

### Post by Dalon on 2009-06-26
This problem is resolved in kernel 2.6.30 (ubuntu kernel is 2.6.28 ) 

go [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/)[]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/") 
download the necessary files 
(see [https://wiki.ubuntu.com/KernelMainlineBuilds]("https://wiki.ubuntu.com/KernelMainlineBuilds") ) 

for example: i386 necessary 
[B]linux-headers-2.6.30-020630-generic_2.6.30-020630_i386.deb	10-Jun-2009 11:27 	598K 
linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb	10-Jun-2009 11:27 	24M
linux-headers-2.6.30-020630_2.6.30-020630_all.deb	10-Jun-2009 10:04 	8.8M[/B]
and 
in the directory with these files: 
```
dpkg-i *. deb
``` 
shutdown and sleep working.

---

