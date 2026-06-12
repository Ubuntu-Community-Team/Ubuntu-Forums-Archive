---
title: "[SOLVED] xserver and intel 82830m video driver HELP please"
date: 2007-05-19
forum: Hardware &amp; Laptops
---

### Post by Jackie_Treehorn on 2007-05-19
My old hand-me-down gateway solo 1450 laptop will not work with my new install of ubuntu.

xserver crashes at startup.

running command line recovery mode at startup, i can access the xserver config area, however i can not find a combination or driver that works for my screen.

video card is intel 82830m from intel 830 chip family.

i've tried vesa, and the 3 intel drivers listed in the xserver config area.

i'd really like this laptop to be dual boot with xp, but so far ubuntu is not usable.

i've done a lot of reading on this forum and found a few topics about this, but so far nothing has helped.

Thank you for helping!

Jackie

---

### Post by Jackie_Treehorn on 2007-05-19
so far i've found that if i use the i810 driver at a bit depth of 16, i can then 'startx' and the desktop will render at 640x480.

it's working, but only limping along clearly.

help is still needed.

thanks

---

### Post by Jackie_Treehorn on 2007-05-24
I'm still very much in need of help with this issue.

Did I post this message in the correct forum?

Thank you.

---

### Post by jelkner on 2007-05-26
I have the same laptop and the same problem.  I did a fiesty install using the alternate install disk, and can only get X to work at 640x480.

---

### Post by veloce on 2007-05-26
> **jelkner said:**
> I have the same laptop and the same problem.  I did a fiesty install using the alternate install disk, and can only get X to work at 640x480.

If you are using the i810 driver, then you probably need to install "915resolution" - use Synaptic or the command:

sudo apt-get 915resolution

And reboot.  If 915resolution doesn't work automatically, you need to add the desired resolution to the file /etc/defaults/915resolution.

OR: if you are using Feisty, you can upgrade to the "intel" driver which does not need the 915resolution package.

sudo apt-get install xserver-xorg-video-i810

Make sure you alter the driver in the device section of your xorg.conf to "intel"

---

### Post by Jackie_Treehorn on 2007-05-28
915resolution gives me" wrong chipset detected" and will not install on my machine.

intel did not work either.  downloaded and intalled.  black screen.

thus far, the only thing that works is the i810 driver.  but only at the very lowest res. of 640x480 which sucks.

at this point, I'll pay someone to fix and document this issue for me as I want this intel driver working.

---

### Post by jelkner on 2007-05-28
I need it fixed for a friend's laptop as well.  Colin Applegate is working on it today.  He may come up with something, in which case we will immediately share it with you.

---

### Post by Jackie_Treehorn on 2007-05-28
> **jelkner said:**
> I need it fixed for a friend's laptop as well.  Colin Applegate is working on it today.  He may come up with something, in which case we will immediately share it with you.

I'll keep my fingers crossed and I'll keep checking this thread.

Maybe there is a combination of settings in the reconfigure xserver-xorg utility that might work.

On a side note after I gunk up my xserver, how can I reload the backed up version of the file from the command line (safe mode) ubuntu?

I can't figure it out, so after each mess up when my screen goes blank, I've just been reinstalling ubuntu to start fresh again.

Thank you.

---

### Post by colinapplegate on 2007-05-28
Jackie: during the boot process you should see an option to press ESC to enter grub
by default i believe it will count from 2 to 0 then launch ubuntu... but if you press ESC grub will come up.
select recovery mode and press enter
ubuntu will boot you into a console.
perform the following:

cd /etc/X11
mv xorg.conf broken.xorg.conf
mv xorg.conf (press Tab) and you'll be given a list of xorg.confs with dates attached on the end, eg. xorg.conf.20070526105018 xorg.conf
so using that filename it would be: mv xorg.conf.20070526105018 xorg.conf
reboot -n

viola! reverted back to the old x.org config

this chipset is evil but i'm determined to figure out how to hack it into working condition. i should have some free time after work the next few nights to mess with this.

all the best,

Colin Applegate

---

### Post by veloce on 2007-05-29
When X crashes, you can usually get out of it without rebooting.

use the key combination CTL+ALT+F1 (or F2 ...) to bring up a console. 

After logging in, reset your xorg.conf as described above, or, I use:

```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

```
(I saved a working xorg.conf as xorg.conf.backup)

Then:

```
sudo /etc/init.d/?dm stop
sudo /etc/init.d/?dm start

```

(This last bit courtesy of Christchurch LUG)

---

### Post by Jackie_Treehorn on 2007-06-03
Colin,

Any luck with this issue yet?

Thanks,

Jackie

---

### Post by dragoncow2 on 2007-06-09
Hello all!

Dear Sir Colin offered me a free cup of coffee if I fixed this problem. And so, I have! For all you Gateway Solo 1450 users, the problem is simple to fix. I'm going to go do some more extensive testing and write up some documentation, but fear not, as I write this forum post I'm running 1024x768@24 bits on Ubuntu Feisty on a Gateway Solo 1450.

---

### Post by Jackie_Treehorn on 2007-06-10
> **dragoncow2 said:**
> Hello all!

Dear Sir Colin offered me a free cup of coffee if I fixed this problem. And so, I have! For all you Gateway Solo 1450 users, the problem is simple to fix. I'm going to go do some more extensive testing and write up some documentation, but fear not, as I write this forum post I'm running 1024x768@24 bits on Ubuntu Feisty on a Gateway Solo 1450.

Thanks sooooo much!

I can't wait to see your solution.

Jackie

---

### Post by DougieFresh4U on 2007-06-10
> **veloce said:**
> If you are using the i810 driver, then you probably need to install "915resolution" - use Synaptic or the command:

sudo apt-get 915resolution

And reboot.  If 915resolution doesn't work automatically, you need to add the desired resolution to the file /etc/defaults/915resolution.

OR: if you are using Feisty, you can upgrade to the "intel" driver which does not need the 915resolution package.

sudo apt-get install xserver-xorg-video-i810

Make sure you alter the driver in the device section of your xorg.conf to "intel"

So you are saying that where it's saying that driver should say "intel" as you can see in the following what mine says

[B]Section "Device"
	Identifier	"Intel Corporation 82810 CGC [Chipset Graphics Controller]"
	Driver		"i810"
	BusID		"PCI:0:1:0"[/B]

Also, what would be the diff between the two highlighted drivers in screenshot posted/
Thanks

---

### Post by veloce on 2007-06-11
> **DougieFresh4U said:**
> So you are saying that where it's saying that driver should say "intel" as you can see in the following what mine says

[B]Section "Device"
	Identifier	"Intel Corporation 82810 CGC [Chipset Graphics Controller]"
	Driver		"i810"
	BusID		"PCI:0:1:0"[/B]

Also, what would be the diff between the two highlighted drivers in screenshot posted/
Thanks

The "intel" driver is a later version than the "i810".  To use it you need to replace that "i810" with "intel" and use your package manager to install the intel driver - that will uninstall the i810 so you must do **both** before restarting X.

---

### Post by dragoncow2 on 2007-06-11
Alrighty, I've done a bunch of work trying to get this problem fixed, and it turns out to be a very simple fix. Apparently the newer BIOS from gateway is filled with evil. The fix to this problem is to install an older version of the bios. The older version, however, comes with it's own bug. The bug that will be introduced by the older bios is purely cosmetic...you're BIOS will report having a 1066 Mhz processor. This does not matter, for linux will see the full speed of your processor (cat /proc/cpuinfo), and your computer will run at full speed. It's purely a cosmetic problem. I have not tried the intel drivers after I flashed the BIOS, I did try xfree86 and X.org, both work just fine after the BIOS downgrade.

Warning: Flashing your BIOS incorrectly, or losing power while flashing your BIOS will render your laptop a brick that's expensive to repair, and I take no responsibility for your actions. ( It worked for me! :)

Only do this if you're *sure* you have a Gateway Solo 1450. These instructions are for the command line, because I'm going to assume X is broken.

Step 1.) Get a disk image that has the BIOS on it, like this:

ubutnu@ubuntu:~# wget [http://dragoncow2.com/1450_BIOS_bootdisk.dd.gz](http://dragoncow2.com/1450_BIOS_bootdisk.dd.gz)


ubutnu@ubuntu:~# gunzip 1450_BIOS_bootdisk.dd.gz

(Now insert a blank floppy into your floppy drive):

ubutnu@ubuntu:~# dd if=1450_BIOS_bootdisk.dd of=/dev/fd0 bs=1k


Now, put that floppy disk into the Gateway Solo 1450, and boot off it. You'll be greeted with some sort of dos prompt. I don't remember what the prompt looks like, so I'm going to pretend it's: "A:\>" Now type,

A:\> 1450bios.exe

If it asks you questions, answer them with "Yes", I don't remember if it asks you anything or not. It is *VERY* important that your laptop is plugged into a powersource.

The laptop will automatically reboot when it's finished, take out the floppy and boot into Ubuntu. Everything should work just fine (with the default install). If you've already messed around with X trying to get it to work, I believe the following line should fix it:

ubutnu@ubuntu:~# sudo dpkg-reconfigure xserver-xorg

If you have some other dos disk you wish to use instead of the one wgett'd, you can extract the bios-flashing-executable from the image by doing the following:

ubutnu@ubuntu:~# sudo mount -o loop /path/to/image.dd /media/floppy
ubutnu@ubuntu:~# cp /media/floppy/*.exe ~


I found that I could not install using the LiveCD, so I had to use the alternate install cd which worked 100% perfect. Also, it seems with the older bios you must hit "Escape" at the BIOS screen in order to boot off the cd-rom drive, even if the cd-rom drive was set to boot first by default in the bios options. 

I think that's about it, so if anyone else has any questions, feel free to e-mail me at:  [email]dragoncow2@ubuntu.com[/email]

---

### Post by dragoncow2 on 2007-06-11
A few things I forgot to mention, 

The xserver-xorg-video-intel package should not be installed. It appears the intel module does not work with this laptop. Since I'm assuming your Gateway solo1450 behaves exactly like this gateway solo1450...use the i810 driver.

Also, on bootup usplash does silly things with the console. Since usplash is purely cosmetic, I recommend removing it (the console is unusable if you have usplash installed, it seems)

ubutnu@ubuntu:~# apt-get remove usplash

Also, don't install 915resolution. If it is installed, uninstall it. 915resolution is unneeded for this laptop.

---

### Post by Jackie_Treehorn on 2007-06-28
Thank you!  Thank you!  Thank you!

I just did this and mine worked right away.  Awesome.

Cheers!

Jackie

---

