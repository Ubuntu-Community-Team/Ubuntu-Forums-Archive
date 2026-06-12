---
title: "Hardy Heron + ASUS A8V-XE = fail"
date: 2008-10-23
forum: General Help
---

### Post by anoxan on 2008-10-23
hello ubuntu community! I type this in mandriva 2009 gnome, because for some reason, hardy heron AND the intrepid ibex beta either won't boot after an upgrade, or just won't even start for a clean install.

I've tried downloading hardy at least 4 times, and upgrading twice. each time I get this "initramfs" prompt, and it just stalls. I tried that '8.04.1' re-release a couple times and got the same result. I wasn't expecting the beta to boot, really. just wanted to try it and see if there was a difference. glad I have cd-rws! suse just stalls (could be the same issue), and I get the same results in mint

I've gone through nearly every option in my bios including: cycling my sata through ide, raid, and ahci modes (cd drive is sata, media hdd is sata. trying to install on an ide hdd) , disabled the serial, printer, onboard lan, onboard sound, disabled/removed floppy...I can't remember anything else atm..

what is up with this? I don't know if it's my board, or ubuntu. 7.10 will work, but I'm wanting to upgrade. mainly for gnome. that, and I want to see if my linksys wusb54gc had better support. it's a little annoying having to re-compile my lan driver every kernel update..](*,) I heard asus was gimping their bios for linux. something about their bios being biased to xp/vista, but I didn't read too much on that. think maybe it's that?

I like mandriva, but I like ubuntu more. much more. mandriva seems to be babysitting me on certain things. really user-friendly for first-timers, but a little annoying for people like me. I mean, sudo doesn't even work! I have to use su. I don't know the difference, other than the extra two letters, and that I had to learn a new term, but that's not really a problem to me, just proves that linux needs to be a little more standardized..I'm ranting. anyway...

can *anyone* shed some light on this? I'm about ready to reinstall 7.10, compile gnome 2.24, and go from there, but I want to upgrade! :cry:

quick specs of my setup:
asus a8v-xe mobo, athlon64 3000, 1 sata dvd-rw, 1 sata hdd, 2 ide hdds, nvidia 7200gs, 1gb ram...if you need more info just ask :p

any help will be appreciated greatly!

/me

Update: I'm now successfully booting into 8.10. the problem lies in ubuntu's custom kernel. it is solved easily enough.

1. install 7.10, and update to 8.04.
2. when you reboot and come to the loading screen for grub, hit escape to get into the grub menu.
3. select kernel 2.6.22-15-generic, and boot.
4. update to 8.10. when you restart, repeat steps 2-3.
5. enjoy.

to make this solution permanent, you'll have to edit grub. refer to post #9 for this, as I'm lazy and don't feel the need to repeat it. it's all here though.

---

### Post by daemonfly on 2008-10-24
I just got a new Seagate 1TB drive to add into my system that already has 2 IDE drives. Ubuntu won't even recognize the new drive at all, and if I boot from any of the live CDs, they dump right to the busybox promt like you get. Seems to be something with Ubuntu and the SATA on this mobo(I have the A8V-X). Perhaps manual drivers, or kernel options, I just haven't figured it out yet.


Edit: actually, for your problem, you may want to read [http://vip.asus.com/forum/view.aspx?id=20070913012840078&board_id=1&model=A8V&page=1&SLanguage=en-us](http://vip.asus.com/forum/view.aspx?id=20070913012840078&board_id=1&model=A8V&page=1&SLanguage=en-us)
It says this mobo can't boot from SATA.

---

### Post by Yellow Pasque on 2008-10-24
> Seems to be something with Ubuntu and the SATA on this mobo(I have the A8V-X).
IIRC, VIA 8237 southbridges don't do SATA 300 and don't negotiate down to SATA 150 like the SATA standard calls for. See if there's an option to jumper your drive into SATA 150 (aka "comatibility mode").

EDIT: [http://www.seagate.com/images/support/en/us/cuda_sata_block.gif](http://www.seagate.com/images/support/en/us/cuda_sata_block.gif)

---

### Post by daemonfly on 2008-10-24
Thanks for info, I'll try that once I get off work. 

Just re-read the original post and guess I missed where he said it was working on 7.10.

---

### Post by ilcontegis on 2008-10-26
i have the same problem with the same m/b....
Until the kernel 2.6.22-15 the m/b works fine...after is nt anymore supported! 
I put this kernel version and it works. Now i have ubuntu 8.10 and the 2.6.22-15 as kernel.
Why the kernel developers stopped the support? to who can i ask to include again the support to the next kernel version?
Thank you..

---

### Post by anoxan on 2008-10-28
Temüjin, I have a wd sata hdd, but I'll give it a try tomorrow. I swear if that's it I'm gonna stab this motherboard with a screwdriver and send it back to asus. then go find me a nice abit board..

[quote=ilcontegis]Until the kernel 2.6.22-15 the m/b works fine...after is nt anymore supported!
I put this kernel version and it works. Now i have ubuntu 8.10 and the 2.6.22-15 as kernel...[/quote]
how did you do this?

this could be the problem. I don't see why 8.x couldn't boot, unless something in the kernel changed; since 7.10 works so well!

---

### Post by ilcontegis on 2008-10-28
yes after ubuntu 7.10 this motherboard is not supported anymore. there is no support in the kernel. I have no idea why, but it is like this.
How i did? i installed ubuntu 7.10 i updraded until ubuntu 8.10 keeping the old kernel.

I am looking to some adress where to write, to ask the kernel developpers to put bak the support to our matherboard.

---

### Post by anoxan on 2008-10-28
how did you keep the old kernel? I know you can have multiple kernels in grub, but I don't know how to edit grub..:P

if you do find some sort of contact, be sure to post it here, 'cause I'd like to email them as well. it's not like this is an old board either. my old chinese-made (chyang fun...lol) shuttle pc with a 1.7ghz p4 and 9600xt from 2002 runs just fine, albeit slow.

---

### Post by ilcontegis on 2008-10-28
the old kenrnel if you install from ubuntu 7.10 is kept automatically if YOU do not erase :)
you can select from the grub the kernel that you prefer in this way.

You can as well edit the grub and put in comment the newer kernel to boot automatically from the old one without choosing every time.

How to do this? very easy
```
cd /boot/grub
sudo gedit menu.lst

```
Insert the password
It will appear something like this
```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=e26e3edb-af91-493c-a824-90f013ce8d2e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

#title		Ubuntu 8.10, kernel 2.6.27-7-generic
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e26e3edb-af91-493c-#a824-90f013ce8d2e ro quiet splash 
#initrd		/boot/initrd.img-2.6.27-7-generic
#quiet

#title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e26e3edb-af91-493c-#a824-90f013ce8d2e ro  single
#initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.22-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=e26e3edb-af91-493c-a824-90f013ce8d2e ro quiet splash 
initrd		/boot/initrd.img-2.6.22-15-generic
quiet

title		Ubuntu 8.10, kernel 2.6.22-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=e26e3edb-af91-493c-a824-90f013ce8d2e ro  single
initrd		/boot/initrd.img-2.6.22-15-generic

title		Ubuntu 8.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e26e3edb-af91-493c-a824-90f013ce8d2e ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e26e3edb-af91-493c-a824-90f013ce8d2e ro  single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```
Now what we are interested in is only this part
```
#title		Ubuntu 8.10, kernel 2.6.27-7-generic
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e26e3edb-af91-493c-#a824-90f013ce8d2e ro quiet splash 
#initrd		/boot/initrd.img-2.6.27-7-generic
#quiet

#title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e26e3edb-af91-493c-#a824-90f013ce8d2e ro  single
#initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.22-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=e26e3edb-af91-493c-a824-90f013ce8d2e ro quiet splash 
initrd		/boot/initrd.img-2.6.22-15-generic
quiet

title		Ubuntu 8.10, kernel 2.6.22-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=e26e3edb-af91-493c-a824-90f013ce8d2e ro  single
initrd		/boot/initrd.img-2.6.22-15-generic

title		Ubuntu 8.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e26e3edb-af91-493c-a824-90f013ce8d2e ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e26e3edb-af91-493c-a824-90f013ce8d2e ro  single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
```

As you can see for the first 2 optioon (the newer kernel version) i putted a # at the beginning making the line a comment.
Repeat this for all the line you don't want in the boot. Of course if one day you want them back just put away the #.

Is it clear? please tell me if I can help more.

Let's try to find a contact for the kernel support.
See ya

---

### Post by anoxan on 2008-10-28
ah, I see...your instructions are crystal. :) I'll post back with results

---

### Post by anoxan on 2008-10-28
update: I'm successfully booting into 8.04, but ran into a snag with it not recognizing my monitor, and not wanting to load my gfx card driver. I'm hoping when I jump to 8.10, it will magically fix itself. linux tends to do that with me..

onward!

---

### Post by ilcontegis on 2008-10-28
> **anoxan said:**
> update: I'm successfully booting into 8.04, but ran into a snag with it not recognizing my monitor, and not wanting to load my gfx card driver. I'm hoping when I jump to 8.10, it will magically fix itself. linux tends to do that with me..

onward!

did you install some proprietary driver? (ati/nvidia) you should not install anything. when you update you should have only the official "things"..once the update is finished (you have ubuntu 8.10) then you install what you want.

---

### Post by anoxan on 2008-10-29
yeah, I had the restricted driver installed when I started the upgrade, so I guess that had some sort of effect. it seems to be resolved, though now for some reason my login screen is like, 3x bigger than my monitor, and I have no idea why. I'm sure it has to to with using the v.173 driver instead of the reccomended v.177, but when I enabled that driver, my desktop got all wonky on me and refused to display my resolution correctly.

in any case, I'm now running 8.10! thank you for your help. I'm sure someone else using our mobo will be having this problem, and now we don't have to blame ubuntu for it.

I must say though, it's nice being able to switch kernels almost on-the-fly. ms could learn something here. then again ms is mainstream, and anything mainstream needs to be as idiot-proof as possible.

if only ubuntu could play my hd video files without lag. maybe a new nvidia driver could fix this...

oh, I haven't found anything close to an email for any kernel developers. maybe I'm not looking in the right direction. I'm gonna try to get in contact with cannonical (sp?) and see if they can point me in the right direction. as stated before, there's no reason to drop a 2 year old *asus* motherboard and keep a 6 year old no-name chinese motherboard.

---

### Post by ilcontegis on 2008-10-29
I completely agree with you.
I tried to check on the linux kernel website, but i could not find any contact......
Let's try to look more deeply maybe we'll find something.:)

---

### Post by ilcontegis on 2008-11-15
no news? nobody has a more elegant solution? nobody knows why the kernel doesnt support the MB anymore? or who to contact?

---

### Post by anoxan on 2008-11-25
ok, I have an update. 8.10 has a tendency to crash to the login prompt whenever I have more than 2 windows open in all my workspaces, so I decided to see if fedora would load, since they have a new version out. I'm typing this in fedora core 10 with kernel 2.6.27.5...

now I don't know too much about linux, but I do know I'm running a much newer kernel with fedora than ubuntu, so our theory of the kernel devs cutting support for our boards wasn't right.

I therefore point my finger at ubuntu, and I'm not happy with that. I have no clue what the ubuntu devs did to the kernel, but it's frustrating to say the least. I'm in no mood to compile kernels (or anything else) either, but if I want to ditch my 'pirated' student copy of windows, it looks like I won't have much of a choice.

I still like ubuntu more than the others. mainly because it's debian-based. but I won't be pushed into buying new hardware. microsoft does that, and that's why I'm so adamant on finding a linux distro that will work. my pc is plenty fast, and only 2 years old.

oh well, enough of my ranting. fedora's security selinux thing is really starting to piss me off, and it's getting shot in the face..metaphorically.

I'm off to reinstall 7.10 (again), update to 8.04, keep the old kernel, and stop screwing with things.

---

### Post by ilcontegis on 2008-11-27
Now Ubuntu 8.10 has 2.6.27.7 kernel, but is still not working....
I do not understand how is it possible....
The kernel should be the same even if the distribution is different....or not? How is possible that on fedora it works and on ubuntu it doesn't?

So it means that ubuntu's developers putted away some driver from the kernel, but why? I really do not understand...

I hope that with the new kernel 2.6.28 something will change even if I am not so optimistic as it is since the kernel 2.6.22 that nothing works anymore. (more than one year ago..)

---

### Post by happyhamster on 2008-11-27
Could be related to this bugreport:
[https://bugs.launchpad.net/ubuntu/+bug/190492](https://bugs.launchpad.net/ubuntu/+bug/190492)

No solution yet, but there's a workaround listed.

---

### Post by ilcontegis on 2008-11-27
> **happyhamster said:**
> Could be related to this bugreport:
[https://bugs.launchpad.net/ubuntu/+bug/190492](https://bugs.launchpad.net/ubuntu/+bug/190492)

No solution yet, but there's a workaround listed.

Thanks a lot man!
This is the same bug....Im a very sad to see that the bug is still not solved, BUT there is a very simple workout to do for now.
Open the boot menu with gedit or whatever you want
```
sudo gedit /boot/grub/menu.lst
```
and add the option pci=nomsi to the kernel to boot, like this
```
title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e26e3edb-af91-493c-a824-90f013ce8d2e ro quiet splash **pci=nomsi**
initrd		/boot/initrd.img-2.6.27-7-generic
quiet
```
And it works! Personally I had to disinstall the ATI proprietary driver before to pass to the new kernel and reinstall them after, But except this no other problem. Now is working.
I hope that the will be able to solve soon....
Thank you happyhamster :guitar:

---

### Post by anoxan on 2008-11-28
hm.. this is good news, and I like good news. :D I'll try this as soon as I uninstall my gfxcard. best to be safe..

happyhamster, thanks for the link! I was beginning to think we were the only ones with this weird bug..:p

so, what does 'pci=nomsi' do exactly?

---

### Post by ilcontegis on 2008-11-28
I have no idea.....:confused:

---

### Post by happyhamster on 2008-11-28
Take a look at:

[http://en.wikipedia.org/wiki/Message_Signaled_Interrupts](http://en.wikipedia.org/wiki/Message_Signaled_Interrupts)

[http://www.mjmwired.net/kernel/Documentation/MSI-HOWTO.txt](http://www.mjmwired.net/kernel/Documentation/MSI-HOWTO.txt)

---

### Post by ilcontegis on 2009-04-01
I updated to Jaunty, but the problem is always the same. So for those owning my same M/B please keep using the

```
pci=nomsi
```

solution as said before.

---

### Post by executorvs on 2009-06-09
the thread above me is correct. I have been using this method for some time and had no issues.

---

