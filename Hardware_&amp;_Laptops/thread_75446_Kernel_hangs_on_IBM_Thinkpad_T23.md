---
title: "Kernel hangs on IBM Thinkpad T23"
date: 2005-10-13
forum: Hardware &amp; Laptops
---

### Post by tirant on 2005-10-13
i have tried with the recent released 5.10 version and the previous RC.

The first reboot after the initial installation, the computer hangs when it show

"Uncompressing Linux Ok, booting the Kernel"


It used to work with version 4.10.


My laptop is an IBM thinkpad T23. 1Ghz P3, 640 MB RAM, 20GB HD.

---

### Post by badger on 2005-10-14
I have a T23 (type 2647-4ma) as well. If I recall correctly this has happened to me in the past, until I booted the install kernel with acpi disabled (and maybe noapic as well).

I've just tried a clean install on my T23 with the 5.10 install CD and had no problem, no hanging, and no need to pass any extra parameters to the kernel. Even suspend and hibernate seemed to work out of the box.

Cheers.

---

### Post by tirant on 2005-10-16
Thanks, i will try to pass those parameters to the kernel.

---

### Post by tirant on 2005-10-17
Passed thos parameters and it hangs again :( I have reinstalled it like 5 times...

Now I'm trying to boot the laptop in recovery mode, but it also hangs!!!

It stays there hanged..

[xxxxxx:xxxxx] checking if image is in ramfs...

---

### Post by esmail on 2005-10-18
I have exactly the same problem with 5.10 on my T23. (I also
have Windows 2000 on this system. Gentoo worked fine with
W2K, but I really wanted to install Ubuntu in place of Gentoo)

:-(

---

### Post by badger on 2005-10-19
Did you try "nolapic" as well? (not that I know exactly what this does).

The only other thing that comes to my mind is to try and update the BIOS and the Embedded Controller, which is something I've done a few times. I currently have the 1.18 (1AET62WW) / 2004-07-06 version of the BIOS and 1.06a version of the Embedded Controller. Take a look at [http://www.thinkwiki.org/wiki/BIOS_Upgrade](http://www.thinkwiki.org/wiki/BIOS_Upgrade) for some info. on upgrading your laptop (and heed the warnings).

I don't know if this will help you. Good luck!

cheers

---

### Post by esmail on 2005-10-19
[QUOTE=badger]Did you try "nolapic" as well? (not that I know exactly what this does).[/QUOTE]

Hi I had tried that I'm pretty sure, but without luck.

The update suggestion of the BIOS etc software was a great suggestion.
I had tried to update all previous software before through the Windows
side (and Lenovo updater), but on further checking after your suggestion
I realized that my BIOS was v 1.17 and updated it and the other too.

A reboot into Linux didn't succeed, it still stuck. However, after the
BIOS update I checked the Lenovo/Windows update, and it downloaded
a more recent power management software...

*Then*!! I was able to boot into Ubuntu ... horay!! .. Sound worked,
then I used the updater successfully, but didn't do much else with
the system.

However, that was the only time I was able to do this. I didn't have to
use any additional parameters to the kernel, so I am not sure why this
isn't working now .. *but* at least I know it's possible, so thank you
very much for your suggestion. 

If anyone reading is is passing any special parameters to their Kernel
line, please let me know. In the meantime I'll try out some things. If
I succeed I will report back.

thanks again for the help,

Esmail

---

### Post by esmail on 2005-10-20
Just an update .. since my last post I was able to boot into Ubuntu only once. It works nicely when I can use it, but I wish it would always work 

At this point the boot seems to almost always hang at

**[INDENT]checking if image is initramfs ...[/INDENT]**

regardless if I do regular or safe boot. (I turn off "quiet" in
the regular boot mode to see the startup messages.)

The only other problem I noticed is that if it boots I get
a message that it fails in mounting the local file system, 
but everything seems to be there .. not sure if this is
possibly related?

Gentoo had no problem co-existing with the W2K dual boot
set up with grub before so I'm hoping I can get this to work too.

So close, but still not there ...

---

### Post by pardasaniman on 2005-10-20
Try turning off both quiet AND splash in the boot parameters.

You should be able to see detailed info about where it hangs.

---

### Post by esmail on 2005-10-20
> Try turning off both quiet AND splash in the boot parameters.

Hi there!

I can try disabling splash too, but it doesn't get to that
stage yet (I am assuming splash puts up the graphical
status messages).

It just dies when it gets to 

*checking if image is initramfs ...*

.. very frustrating ...

---

### Post by esmail on 2005-10-20
Ok, one more question .. I am wondering why I can so easily boot with the install CD but not with this setup. Is a different kernel (more plain vanilla) used? Is that an approach worth pursuing?

---

### Post by esmail on 2005-10-27
hi,

just an update in case anyone was reading this due to a similar problem.

for some reason, the problem with the startup went away, i am not quite
sure why? perhaps one of the updates i was able to apply when i got into
ubuntu actually fixed whatever problem there was before. 

in any case, i'm happy to report that i can now use ubuntu very nicely
on my TP23 ...

cheers, and thanks again for all who posted.

esmail

---

### Post by aweit on 2005-11-21
I got this to work without updating the BIOS. Simply add "noacpi noapic" to the end of the kernel line in grub. In my case...

Kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/hda1/ ro splash noacpi noapic

---

### Post by esmail on 2005-11-27
Greetings all.

.. the saga continues ... this time kernel 2.6.12-9 vs 2.6.12-10

The previous kernel worked well for me with this line in my grub
configuration menu.lst

kernel   /boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro  nosplash

However, since updating to kernel 2.6.12-10-386 last week, it won't
boot, but hangs as it used to do earlier at

"checking if image is initramfs ..."


I tried to modify the default kernel line for grub to:

kernel   /boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro  nosplash noacpi noapic

No go, so for now I'm just booting with the earlier kernel. A bit
frustrating that this isn't working.

Anyone else run into any problems with the latest kernel update?
I briefly scanned the messages in the forum as best as I can, but
didn't find anything.

Esmail

---

### Post by esmail on 2005-12-04
Installed 2.6.12-10-686 and everything works great!

---

### Post by eanders on 2005-12-06
I think the 686 kernel is the way to go.

I had this happen a few times when I updated to 2.6.12-10-386 kernel. If I do a clean install and don't update everything's great, and if I install the 686 kernel it works too.

---

### Post by esmail on 2005-12-06
Yup, and no special parameters were required with the 686 parameter.

:-)

---

### Post by jeremyc on 2005-12-07
I am having ths same problem with ubuntu 5.10 (the pressed CD a friend got in the mail).

I've tried with the noapic and nolapic options mentioned above several times in various combinations with no luck.

I would like to try to install the i686 kernel image, but I can't find an ISO for that.

Without being able to boot into a base install, I don't know how to do a network install of the 686 image.

Any ideas?

Thanks!
Jeremy

---

### Post by didi156 on 2005-12-31
I can confirm the problems with T23.
I was running hoary w/o major problems.
Since I installed breezy, I'm quite unhappy.
I had to install with noacpi to get setup working.
Later i manually deleted the noacpi param from the grub config file, since a  OS w/o working suspend is useless for me. It used to work fine (apart some little nerving things like serial port and XV (XVideo-extension) not working and sound muted after suspend...).
But at some point (maybe after a kernel update) I sometimes had a total freeze. This didn't happen often, but it's bad enough that it happens, since I can't reproduce it.

---

