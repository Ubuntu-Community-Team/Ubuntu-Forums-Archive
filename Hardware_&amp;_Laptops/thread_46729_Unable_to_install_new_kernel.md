---
title: "Unable to install new kernel"
date: 2005-07-05
forum: Hardware &amp; Laptops
---

### Post by jc3835 on 2005-07-05
Hello again...

I've decided to upgrade to kernel version 2.6.12.2 so that I'll get the included bugfixes and whatnot, specifically for the ALPS touchpad.

I download the kernel from kernel.org and followed luca's HOWTO here:
[http://www.ubuntuforums.org/showthread.php?t=43065](http://www.ubuntuforums.org/showthread.php?t=43065)

I was able to make everything fine using the following command, after reading all of the posts in the thread.

```
make-kpkg kernel_image kernel_headers modules_image --initrd
``` 

Everything went great until I tried loading the new kernel from GRUB (showed up there fine). After selecting the new kernel, the hard drive reads a bit and all I get is a black, blank screen.

Any ideas? I've seen others have the same issue, but never really get a good answer.
Thanks in advance.

---

### Post by Vorian on 2005-07-05
JC,

You can get the touchpad to work with a 686 kernel

(sudo apt-get install linux-686)

You just have to tweak it a bit.

I finnaly was able to get it to work.  I posted what I did in the inspiron 6000 thread you started.

---

### Post by Nimefurahi on 2005-07-05
There may be an issue with initrd.

Without being overly verbose, what does your /boot/grub/menu.lst look like?

You may want to simply comment out your grub's initrd line, something to the effect of:

title        Ubuntu, kernel 2.6.12.2
root        (hd?,?)
kernel     /boot/vmlinuz-2.6.12.2 root=/dev/hd?? ro quiet splash
#initrd    /boot/initrd.img-2.6.12.2
savedefault
boot

Give it a try.

---

### Post by jc3835 on 2005-07-05
[QUOTE=Nimefurahi]There may be an issue with initrd.

Without being overly verbose, what does your /boot/grub/menu.lst look like?

You may want to simply comment out your grub's initrd line, something to the effect of:

title        Ubuntu, kernel 2.6.12.2
root        (hd?,?)
kernel     /boot/vmlinuz-2.6.12.2 root=/dev/hd?? ro quiet splash
#initrd    /boot/initrd.img-2.6.12.2
savedefault
boot

Give it a try.[/QUOTE]

I will give that a try. 
The first time I compiled the new kernel, I didn't do an initrd. I noticed I had them in all the other kernels (386,686), so I added it to the second compile.

@Vorian:
My touchpad "works"... I just want to get the updated synaptics drivers so the scrolling features of the touchpad work also... like we've been talking about in my install thread. There is a thread explaining why to update to 2.6.12.2 here:
[http://www.ubuntuforums.org/showthread.php?t=46106](http://www.ubuntuforums.org/showthread.php?t=46106)

I also see you have replied to my install thread saying you have this working now... you must've just replied to that one  :-P 
I'll give that a try once more.

Thanks.

---

### Post by jc3835 on 2005-07-05
Now I have a question concerning removing kernels, so without starting a new thread, I'll ask it here first.
Since I've installed Ubuntu (386) I've added a 686 kernel and a newer 2.6.12 kernel. I've got 4 kernels in total. How can I clean up the 2 or 3 I never use?
I've searched the forums thinking someone else might have asked, but no luck finding anything. 
I KNOW how to comment them out of GRUB, but I want rid of them completely.

Thanks.

---

### Post by Vorian on 2005-07-06
[QUOTE=jc3835]Now I have a question concerning removing kernels, so without starting a new thread, I'll ask it here first.
Since I've installed Ubuntu (386) I've added a 686 kernel and a newer 2.6.12 kernel. I've got 4 kernels in total. How can I clean up the 2 or 3 I never use?
I've searched the forums thinking someone else might have asked, but no luck finding anything. 
I KNOW how to comment them out of GRUB, but I want rid of them completely.

Thanks.[/QUOTE]
 I'm going to wait for BB for the kernel upgrade.

---

### Post by jc3835 on 2005-07-06
[QUOTE=Vorian]I'm going to wait for BB for the kernel upgrade.[/QUOTE]

I probably should as well... but I saw the "do not use breezy" message in the other forum and was impatient so I thought I'd try to compile my own.
I think it's good to know how to do that anyway, but I can't seem to boot from a new kernel. They show up in GRUB and all, but all I get is a blank/black screen when I select a new kernel.

---

### Post by luca_linux on 2005-07-06
My HowTo kept initrd stuff out since it needs some patches to the vanilla sources.
In fact I'm not using initrd and I don't have any problem.
In my HowTo there's also my kernel.config for reference if you need.

---

### Post by elsewhere on 2005-07-06
[QUOTE=jc3835]I probably should as well... but I saw the "do not use breezy" message in the other forum and was impatient so I thought I'd try to compile my own.
I think it's good to know how to do that anyway, but I can't seem to boot from a new kernel. They show up in GRUB and all, but all I get is a blank/black screen when I select a new kernel.[/QUOTE]

FWIW I upgraded my kernel in Hoary to the 2.6.12-2 in the Breezy repos, other than having to manually compile my nvidia drivers now, it's worked more or less well.  I'm not actually recommending doing so if you're not comfortable with it, just letting you know that it can be done if you're curious to try.  You can always revert back to a previous kernel in grub, anyhow...

You're absolutely right that knowing how to compile your own kernel is good to know for Linux.  Me, I'm just too lazy....  

Cheers,
KV

---

### Post by jc3835 on 2005-07-14
This whole kernel upgrade process is really becoming frustrating. I've tried following every guide I can find, including Luca's HowTo on this forum, the guide on kernelnewbies.com, and the one on Debian.
Every time, no matter which guide I follow, once I select the new kernel in GRUB the screen goes black and nothing much more happens.
I've tried on 2 laptops now, same result, on completely clean installs.
Any suggestions more than what you've given already?
 ](*,)

---

### Post by Nimefurahi on 2005-07-14
[QUOTE=jc3835] (in part)... Every time, no matter which guide I follow, once I select the new kernel in GRUB the screen goes black and nothing much more happens. ](*,)[/QUOTE]
"... and nothing much more happens." Could it be that there is still some activity and loading, but unseen? By that I mean to say, could it be that the kernel and init are loading whilst the screen is black. Once I had symptoms like these. I simply waited long enough and ... finally... the gdm log-on screen appeared. Give it a try. Boot, walk away from your workstation, and hopefully you'll find the gdm screen on your return, in which case we'll help you with including whatever drivers->graphic->console options you may need to include in your kernel.

Oh yes, and did you try commenting out the initrd line in /boot/grub/menu.lst ?

---

### Post by jc3835 on 2005-07-14
i've tried it with and without the initrd line, yes.
following luca's howto, i didn't even have the initrd at all.
i did let it sit at the black screen for quite a while, but i can try again. i watched the hard drive activity light go for a while, but once it stopped, i figured nothing else would happen.
i haven't given up, just whining a bit  :-#

---

### Post by Nimefurahi on 2005-07-14
Verify that when configuring your kernel, you have selected:

Device Drivers ---> Graphics Support ---> Console Display driver Support --->
 
    * Video mode selection support
    * Framebuffer Console support
    * Select compiled-in fonts
    * VGA 8x16 font

You may also want:

Device Drivers ---> Graphics Support --->  * Support for frame buffer devices

and your particular card or generic VESA VGA graphics support.

Then, too, there is the inotify issue. I had to add noinotify to my Grub's kernel line: kernel /boot/bzImage root=/dev/hda1 ro idebus=66 **noinotify** vga=0x317

(Yes, I'm grasping at straws, but we have to get you up-and-running!)

---

### Post by jc3835 on 2005-07-15
I notice you're using the bzImage instead of vmlinux. I tried that as well from a HowTo on the net somewhere.
I will start again, configure and make sure those options are selected, and then see what happens.
Thanks for the advice.

---

### Post by luca_linux on 2005-07-18
[QUOTE=Nimefurahi]Verify that when configuring your kernel, you have selected:

Device Drivers ---> Graphics Support ---> Console Display driver Support --->
 
    * Video mode selection support
    * Framebuffer Console support
    * Select compiled-in fonts
    * VGA 8x16 font

You may also want:

Device Drivers ---> Graphics Support --->  * Support for frame buffer devices

and your particular card or generic VESA VGA graphics support.

Then, too, there is the inotify issue. I had to add noinotify to my Grub's kernel line: kernel /boot/bzImage root=/dev/hda1 ro idebus=66 **noinotify** vga=0x317

(Yes, I'm grasping at straws, but we have to get you up-and-running!)[/QUOTE]
 Yes, as said by Nimefurahi, you probably need these options.

---

### Post by jc3835 on 2005-07-18
We have success!!  \\:D/ 

I think those fixes posted by Nimefurahi did the trick. I'm running the new 2.6.12.3 kernel right now. 
Have to update my other laptop tonight, with the same results hopefully, because that's the one I really needed the new kernel for... wanted the latest synaptics touchpad drivers that are in the new kernel...
I know, I could've just updated the synaptics drivers. But I figured, hey, why not learn something else in the process!  :smile: 

FYI:
I used the following to bake the kernel:
```
sudo make-kpkg --append-to-version=-custom kernel_image modules_image --initrd binary
``` 

That was after I checked the options that Nimefurahi mentioned in xconfig.

Thanks to all who offered help.
Luca, your HowTo still rocks!

JC

---

### Post by Nimefurahi on 2005-07-18
[QUOTE=jc3835] (in part)... Have to update my other laptop tonight, with the same results hopefully, because that's the one I really needed the new kernel for... JC[/QUOTE] And how is your other laptop upgrade coming along?

---

### Post by jc3835 on 2005-07-18
[QUOTE=Nimefurahi]And how is your other laptop upgrade coming along?[/QUOTE]


Well... unfortunately I went to the casino and had dinner and drank and played cards too much tonight to do anything to my home laptop  :roll: 
I'll have to let you know tomorrow!

---

### Post by Nimefurahi on 2005-07-18
Ha!
Been there, did that, and I've since lost the Tee shirt!
But did you have a good time?

---

### Post by jc3835 on 2005-07-19
[QUOTE=Nimefurahi]Ha!
Been there, did that, and I've since lost the Tee shirt!
But did you have a good time?[/QUOTE]
Had a fantastic time!!  :smile: 
I should get to the other laptop tonight... and hopefully it works just the same. I'd like to say it should, but then a lot of you guys' laptops were working with the HowTos, and mine wasn't.
Regardless... I'm learning and moving along.
I'll keep you updated.

---

### Post by jc3835 on 2005-07-20
Well I got the new kernel installed on my home laptop last night. Had some issues with Splashy, so I removed that so I could see the verbose output of linux loading.
Once I removed splashy, the new kernel booted to the login screen. I am able to login, but the computer then freezes on the little Ubuntu splash screen and never makes it to Gnome. Did this a couple of times.
I imagine it's a .config file tweak somewhere that will fix this... any ideas?
Thanks.

---

### Post by Nimefurahi on 2005-07-20
I had the same problem. Try this:

Include **noinotify** to your Grub's kernel line, such as... ```
kernel /boot/bzImage root=/dev/hda1 ro idebus=66 **noinotify** vga=0x317
``` Cheers!

---

### Post by jc3835 on 2005-07-20
[QUOTE=Nimefurahi]I had the same problem. Try this:

Include **noinotify** to your Grub's kernel line, such as... ```
kernel /boot/bzImage root=/dev/hda1 ro idebus=66 **noinotify** vga=0x317
``` Cheers![/QUOTE]

That's right... you did say that already... sorry... it's early and I wasn't remembering!
 [-X 

Thanks again... I'll give it a try when I get back from vacation.

---

### Post by Nimefurahi on 2005-07-20
[QUOTE=jc3835]... I'll give it a try when I get back from vacation.[/QUOTE]Vacation? What, and leave a kernel uncompiled?
You enjoy, my friend. Truth be told, I'm taking off the next two days to do some top-water fly fishing for Smallmouth Bass down the river.
Kernels can wait!

---

### Post by jc3835 on 2005-07-28
nope... no help with the noinotify
finally got a chance to try that tonight... still freezing after i enter my login and password on the gnome login screen.
i'm going to rebuild the kernel now... have an idea.

---

### Post by jc3835 on 2005-07-29
Alright... finally got a new kernel to install and load on this machine! :)
Unfortunately, however, I lost my eth1 device (wireless) when I booted into that kernel. During the bootup, I also didn't have any verbose output of the loading process either, but I let it go the normal time, and eventually got the login screen. I'm back in the old kernel at the moment trying to get ideas on how to fix those issues.
Any suggestions?

JC

---

### Post by Nimefurahi on 2005-07-29
Did you address the following as you did with the other laptop:> Device Drivers ---> Graphics Support ---> Console Display driver Support --->

* Video mode selection support
* Framebuffer Console support
* Select compiled-in fonts
* VGA 8x16 font

You may also want:

Device Drivers ---> Graphics Support ---> * Support for frame buffer devices

and your particular card or generic VESA VGA graphics support.


---

### Post by jc3835 on 2005-07-29
Yes I did.
I did the exact same thing, and like I said, I finally got it working... but for some reason the wireless device disappeared here on this computer.
Easy way to reinstall it?

---

### Post by Nimefurahi on 2005-07-29
Sorry,

I have Zero experience with wireless.

---

### Post by jc3835 on 2005-07-29
now i can't even get that kernel to load a second time...  :???: 
o well... i'll just keep plugging away. there'll be a new release of ubuntu by the time i figure anything out!  :razz:

---

