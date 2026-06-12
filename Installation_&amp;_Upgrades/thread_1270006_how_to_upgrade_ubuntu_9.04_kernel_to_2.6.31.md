---
title: "how to upgrade ubuntu 9.04 kernel to 2.6.31"
date: 2009-09-19
forum: Installation &amp; Upgrades
---

### Post by beemzet on 2009-09-19
Hi guys,

How do I upgrade linux kernel to the latest one on ubuntu 9.04?

Thanks

---

### Post by stlsaint on 2009-09-19
i think you need to change options in your sources manager. not exactly sure to what tho...are you trying to install kernel yourself? this is a very tricky process and not made to be taken lightly. i recommend you try on a "test" system before you go touching your main system!

---

### Post by beemzet on 2009-09-19
> **stlsaint said:**
> i think you need to change options in your sources manager. not exactly sure to what tho...are you trying to install kernel yourself? this is a very tricky process and not made to be taken lightly. i recommend you try on a "test" system before you go touching your main system!

thanks for the reply. it's just wireless doesn't work well on my macbook pro santa rosa. but it works great on ubuntu karmic alpha. so I thought the only difference between jaunty and karmic would be the kernel (though there are many other difference). so here i am, trying to install latest kernel to solve my buggy wireless.

---

### Post by stlsaint on 2009-09-19
well like i said this is a very tricky situation when it comes to messing with kernel...not trying to judge your level of knowledge with ubuntu but i think you should definately get some one on one help in the irc.
here is where you can check out kernels tho

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

or just to search for updates do this: 
Click on System > Administration > Update Manager > Click on Check button > Apply all updates including kernel. 
2)Use Synaptic, search for linux-image and select the generic kernel version you want to install (i.e. linux-image-2.6.xx-yy-generic).  


cant stress it enough tho...get help if your not sure...dont 'TEST' anything!
and do a complete backup of system prior to any changes!
hope i was of help!

---

### Post by beemzet on 2009-09-19
thanks again.

I just wonder why kernel updates don't show up in synaptic? latest stable is 2.6.31 but in synaptic it's only 2.6.28-15.

---

### Post by QIII on 2009-09-19
2.6.31 is included with Karmic.

It is not available in the updates for Jaunty.

I would not recommend attempting to back port it from the Karmic repositories into Jaunty simply because it has not been tested for that purpose.

---

### Post by beemzet on 2009-09-19
> **QIII said:**
> 2.6.31 is included with Karmic.

It is not available in the updates for Jaunty.

I would not recommend attempting to back port it from the Karmic repositories into Jaunty simply because it has not been tested for that purpose.

yeah, but why is not it available in the updates for Jaunty? Does that mean the linux kernel doesn't get updated for Jaunty?

---

### Post by snowpine on 2009-09-19
> **beemzet said:**
> yeah, but why is not it available in the updates for Jaunty? Does that mean the linux kernel doesn't get updated for Jaunty?

All Ubuntu releases are "frozen" after their release date. You never get major updates to the kernel or applications, only minor "point" upgrades such as bug fixes and security patches. This is one reason why Ubuntu is so stable.

If you want the newest kernel, you have to install it yourself. Stlsaint has already given you the link to the correct repository.

---

### Post by AmerNewbieInDE on 2009-09-19
ubuntu doesnt give the latest kernel update untill they try it out and make sure it works right..

---

### Post by beemzet on 2009-09-19
thanks for the info guys. guess I'll have to wait until karmic is available. I've installed 2.6.31 but NVIDIA didn't work, so every time I logged in, there was a message that ubuntu was running on a low  graphics mode. tried to install nvidia from nvidia's site, but couldn't get it working.

thanks again.

---

### Post by darco on 2009-09-20
Strange....I just upgraded from mainline .30  kernel to the Karmic .31 kernel using the 190.32 nvidia drivers and all is working fine...I did hear from another thread that the .32 driver wasnt playing nice w/.31 kernel but possibly because it wasnt the final version?
It was posted a few weeks back. Which driver are you using?

darco

---

### Post by beemzet on 2009-09-20
> **darco said:**
> Strange....I just upgraded from mainline .30  kernel to the Karmic .31 kernel using the 190.32 nvidia drivers and all is working fine...I did hear from another thread that the .32 driver wasnt playing nice w/.31 kernel but possibly because it wasnt the final version?
It was posted a few weeks back. Which driver are you using?

darco

on my jaunty i installed an nvidia driver through hardware drivers option, but since it didn't work after kernel update, i tried to install it through this file at [http://www.nvidia.com/object/linux_display_ia32_185.18.36.html](http://www.nvidia.com/object/linux_display_ia32_185.18.36.html)

---

### Post by darco on 2009-09-20
Try this thread....

[http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia)

good luck

darco

---

### Post by jessiebrownjr on 2009-09-21
Could anybody post a link to a website that goes into detail on how to do update a kernel?

I just installed a fresh 9.04 install on my DESKTOP, and its perfect testing grounds to make sure I get it right!

And im not interested in the suppository style of installing it, I want to do it the hard way :-)

Thanks for any help!

:guitar:

---

### Post by snowpine on 2009-09-21
> **jessiebrownjr said:**
> Could anybody post a link to a website that goes into detail on how to do update a kernel?

I just installed a fresh 9.04 install on my DESKTOP, and its perfect testing grounds to make sure I get it right!

And im not interested in the suppository style of installing it, I want to do it the hard way :-)

Thanks for any help!

:guitar:

I thought the "suppository style" WAS the hard way? ;)

Seriously, stlsaint has already given you the correct link:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31/)

In the subfolder for the kernel you want, you'll see a bunch of .deb files. You need to download three of them:

1. linux-headers...amd64.deb or linux-headers...i386.deb (depending whether you have 64- or 32-bit)
2. linux-headers...all.deb
3. linux-image...amd64.deb or linux-image...i386.deb

In the terminal, navigate to whichever directory you downloaded the 3 files, then install them with dpkg, for example:

```
cd /home/jessiebrownjr/Desktop
sudo dpkg -i *.deb
```

I consider that "the easy way" personally. :)

---

### Post by jessiebrownjr on 2009-09-21
hehe I saw the link to the suppository but I didn't know what to do once they were downloaded. I'm learning Linux backwards I guess :-) More fun that way!

---

### Post by jessiebrownjr on 2009-09-21
> **snowpine said:**
> I thought the "suppository style" WAS the hard way? ;)

Seriously, stlsaint has already given you the correct link:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.31/")

In the subfolder for the kernel you want, you'll see a bunch of .deb files. You need to download three of them:

1. linux-headers...amd64.deb or linux-headers...i386.deb (depending whether you have 64- or 32-bit)
2. linux-headers...all.deb
3. linux-image...amd64.deb or linux-image...i386.deb

In the terminal, navigate to whichever directory you downloaded the 3 files, then install them with dpkg, for example:

```
cd /home/jessiebrownjr/Desktop
sudo dpkg -i *.deb
```I consider that "the easy way" personally. :)

I did this on my desktop, and it gave me the following output. 

Setting up linux-headers-2.6.31-020631 (2.6.31-020631) ...
Setting up linux-headers-2.6.31-020631-generic (2.6.31-020631) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.31-020631-generic                                                   
 *  nvidia (180.44)...                                                                                                       nvidia (180.44): Installing module.
...........(bad exit status: 10)
  Build failed.  Installation skipped.
                                                                                                                      [fail]
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common

Setting up linux-image-2.6.31-020631-generic (2.6.31-020631) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-020631-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-020631-generic
Found kernel: /boot/vmlinuz-2.6.28-15-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.31-020631-generic                                                   
 *  nvidia (180.44)...                                                                                                       nvidia (180.44): Installing module.
..........(bad exit status: 10)
  Build failed.  Installation skipped.
                                                                                                                      [fail]
run-parts: executing /etc/kernel/postinst.d/nvidia-common

this was after it did its thing with the 3 packages... I have an nvidia geforce card. Now what :-) I haven't rebooted yet, no idea if I did any damage, about to do that now !

---

### Post by snowpine on 2009-09-21
> **jessiebrownjr said:**
> 
this was after it did its thing with the 3 packages... I have an nvidia geforce card. Now what :-) I haven't rebooted yet, no idea if I did any damage, about to do that now !

Re-read this thread, particularly post #10.

Your old kernel should still be in your Grub boot menu, and should work fine.

---

### Post by jessiebrownjr on 2009-09-21
Alrighty I just rebooted, it installed, but the nvidia failed, im in low graphics mode.. Im assuming this should be an easy fix because its booting :-)

Will browse more threads, reply if you got some insight :-) thanks!

---

### Post by snowpine on 2009-09-21
> **jessiebrownjr said:**
> Alrighty I just rebooted, it installed, but the nvidia failed, im in low graphics mode.. Im assuming this should be an easy fix because its booting :-)

Will browse more threads, reply if you got some insight :-) thanks!

Choose your old kernel (2.6.28 ) from the Grub boot menu.

---

### Post by jessiebrownjr on 2009-09-21
> **snowpine said:**
> Choose your old kernel (2.6.28 ) from the Grub boot menu.

Kinda defeats the purpose of updating the kernel mate :-)

lol, yeah I figured I could do that if I wanted to, but im just tooling around. If you recall I said this kernal upgrade im doing is on my desktop(my laptop is my baby) and my desktop has nothing on it period, just a fresh install.

---

### Post by snowpine on 2009-09-21
> **jessiebrownjr said:**
> Kinda defeats the purpose of updating the kernel mate :-)

lol, yeah I figured I could do that if I wanted to, but im just tooling around. If you recall I said this kernal upgrade im doing is on my desktop(my laptop is my baby) and my desktop has nothing on it period, just a fresh install.

Please re-read this thread carefully:

1. 2.6.28 is the ONLY kernel officially supported by Ubuntu 9.04
2. Install any other kernels at your own risk
3. This tutorial DOES NOT WORK if you have an nvidia card (post #10)
4. Karmic 9.10 comes out next month and will use the 2.6.31 kernel by default (presumably with the appropriate nvidia patches, though not having an nvidia card myself, I can't comment on this)

---

### Post by jessiebrownjr on 2009-09-21
> **snowpine said:**
> Please re-read this thread carefully:

1. 2.6.28 is the ONLY kernel officially supported by Ubuntu 9.04
2. Install any other kernels at your own risk
3. This tutorial DOES NOT WORK if you have an nvidia card (post #10)
4. Karmic 9.10 comes out next month and will use the 2.6.31 kernel by default (presumably with the appropriate nvidia patches, though not having an nvidia card myself, I can't comment on this)



If I wanted my os to be boring and easy and just handed to me brainlessly I can boot over to Vista and drool..

I'm doing this on my desktop as a learning experience, if I crash it, I wasted about 45 minutes of my life, but it was during free time anyway :-)... I'm trying to get my hands dirty here!

Now one thing I think might have been misconstrued, this is why im editing this post. My wifi card wouldn't support injection until I patched the driver... I ended up learning how to do it manually etc, etc, like madwifi/compat wireless... I figured maybe somebody else has a site like this for graphics cards, but I honestly don't know yet :-) I see the official drivers just dont work with nvidia period, and that sucks... but well see! hehe. 2nd update, they already have user patches out for it, going to post an update later on a new thread if I get it to work. Seems simple enough!

---

### Post by gianluca.pettinello on 2009-09-29
I've Jaunty with kernel 2.6.31 and nvidia 190.32 working fine on hp dv 2690.
My suggestion is that you download from kernel mainline the three files mentioned above in the thread. Then you install them (first the headers and then the image.
Reboot your system in low graphic mode Than you have to install or reinstall the nvidia driver 190.32. To do this you have to include in the sources.list the ppa of nvidia-vdpau and so you will have in synaptics the available files for the nvidia upgrade

Ciao
Gianluca

---

### Post by ride4fitness on 2009-10-04
> **gianluca.pettinello said:**
> I've Jaunty with kernel 2.6.31 and nvidia 190.32 working fine on hp dv 2690.
My suggestion is that you download from kernel mainline the three files mentioned above in the thread. Then you install them (first the headers and then the image.
Reboot your system in low graphic mode Than you have to install or reinstall the nvidia driver 190.32. To do this you have to include in the sources.list the ppa of nvidia-vdpau and so you will have in synaptics the available files for the nvidia upgrade

Ciao
Gianluca

I've also been trying to updated the kernel in 9.04 to 2.6.31.  I've downloaded the files and done the install as described in this post.  However when I re-boot, the grub boot menu does not show the new 2.6.31. kernel, only the previously installed ones. The only odd message during the install was that there was no "splash screen".

Thanks!!

---

### Post by Ginsu543 on 2009-11-02
I was thinking of doing this upgrade myself, but for those of you who have 2.6.31 running on 9.04 Jaunty, do you notice any differences/benefits? Is it worth trying or is it just a matter of having the latest and greatest?

---

### Post by satish_j on 2010-09-08
> **AmerNewbieInDE said:**
> ubuntu doesnt give the latest kernel update untill they try it out and make sure it works right..

:lol::lol:What a Joke!!!!!
They are good at creating CodeNames for the releases..Maverick,Lucid,Jaunty............

---

