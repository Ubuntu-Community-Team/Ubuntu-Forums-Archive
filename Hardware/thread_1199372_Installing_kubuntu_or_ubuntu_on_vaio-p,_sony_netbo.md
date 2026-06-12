---
title: "Installing kubuntu or ubuntu on vaio-p, sony netbook"
date: 2009-06-28
forum: Hardware
---

### Post by spb37 on 2009-06-28
Re: Installing on the Dell Mini 12
I tried the approach below with my vaio-P both with kubuntu lpia jaunty and ubuntu non lpia jaunty on my vaio-p. Both times the xserver would keep trying to start (giving the vaio screen) but fall back to the text login mode. Using the failsafe xorg.conf which relies on vesa works but is not the native driver / holy grail. Everything else works better than expected, it even goes to sleep when I close the lid. Ubuntu and kubuntu both boot faster than windows 7 and even my home desktop kubuntu. So I am eager to get the poulsbo driver working. The vaio-p linux wiki page is blank but if I poulsbo to work it would be a great post. So close but yet so far.

Appreciate any help / suggestions.









Quote:
Originally Posted by pachistano View Post
i don't have my laptop near me, sorry if i am generic. in case, post questions:

here is what I did

1) install ubuntu dell image 9.04 (jauntry) - 2.1 GB is the correct size
2) run a system update
apt-get update
apt-get upgrade
synaptic (or apt, whatever.. ) will remove the old version of Xorg and install a new one, and will do more things...say yes to everything, don't worry and drink a coffe, smoke a cigarette or play for a while with your girl or your pet
suggestion: in case you are playing with your girl, do-not-stop playing once synaptic is ready! otherwise your girl will get angry with you! (my experience)

3) remove from /boot/grub/menu.lst the lines the system added after the update
this because with the new kernel, psb does not work!

-> this rows are referred to the NEW kernel you installed. in facts, after the update you will have 2 different kernel versions inside your system and inside your menu.lst
so, remove the new one ( i remember the last kernel is the 2.6.2x.13)

4) add to your /etc/apt/sources the repositories of psb drivers

deb [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main

- thanks to [http://www.tipsandthoughts.com/?p=4](http://www.tipsandthoughts.com/?p=4)

5) run a synaptic update one more time, or apt-get update

6)install xserver-xorg-video-psb it is supposed to be version 0.31.0
apt-get install xserver-xorg-video-psb

the system will install some addtional packages related to psb

7) reboot

8 )at this point, you are supposed to have a 9.04 running in 2D with the resolution you paid for


it worked with my brand new dell mini 10


questions? post here

bye,
fabio

---

### Post by darth_ru on 2009-07-01
I have successfully made native poulsbo driver to work on may vaio p with ubuntu jaunty.

1. Install Ubuntu Jaunty.
2. sudo apt-get update && sudo apt-get upgrade && sudo reboot
3. Add to /etc/apt/sources.lst
[INDENT]deb [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main
[/INDENT]4. sudo apt-get update && sudo apt-get install poulsbo-driver-2d poulsbo-driver-3d
5. Add to the parameters of new kernel in /boot/grub/menu.lst mem=1500MB (tnx to [http://www.happyassassin.net/2009/05/13/native-poulsbo-gma-500-graphics-driver-for-fedora-10/](http://www.happyassassin.net/2009/05/13/native-poulsbo-gma-500-graphics-driver-for-fedora-10/))
6. Reboot.
7. Enjoy

In fact, the difference between this and method in your quote is that I use new kernel (old kernel doesn't work with psb at all).

---

### Post by g675 on 2009-07-16
Help!

Darth_ru your instructions are excellent, though I am still getting the framesize buffer error which your step 5 is meant to resolve. I've tried reading through the linked thread on AdamW but to no avail.

When you edit the mem=1500MB where exactly should this go within the file and do I need anything else?

I'm running Ubuntu 9.04

Thanks in advance, I'd LOVE to get my VAIO-P running in native

---

### Post by tomranson on 2009-07-16
Hi all,

Haven't touched Ubuntu for a god few months (using RHEL/CentOS/Fedora more these days), however I've been very keen to get 'the brown one' working on my VAIO P given I feel it is the best suited distro for such a system.

I have this evening (finally) managed to kick the thing into life after following the experiences of a number of other like-minded people and with a bit of poking around as necessary.

I quote from darth_ru's post (if I may), modifying the steps where I found necessary.

1. Install Ubuntu Jaunty 9.04.

2. sudo apt-get update && sudo apt-get **dist-upgrade** && sudo reboot

dist-upgrade option is necessary to force to kernel 2.6.28-13; no joy with psb driver under 2.6.28-11 and I would typically prefer the latest kernel regardless.

3. Add to /etc/apt/sources.lst

    deb [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main
    deb-src [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main

4. sudo apt-get update && sudo apt-get install poulsbo-driver-2d poulsbo-driver-3d

(4a.) Add the line 'psb' to /etc/modules; may not be strictly necessary however I found this to be required at some point during my experiences in order to load the module at boot.

5. Modify/add to the parameters of kernel 2.6.28-13 in /boot/grub/menu.lst: **no**splash mem=1500MB

6. Reboot.

7. If X tells you it needs to run in low graphics mode, accept this. From the CLI, execute 'sudo dpkg-reconfigure xserver-xorg' and complete process to give the X configuration a necessary kick.

8. Restart GDM: sudo /etc/init.d/gdm restart

7. Enjoy :-)

Hope this info helps others - it'll also be here for when I forget how it all happened ;-)

Tom

---

### Post by g675 on 2009-07-17
Hi Tom,

Thank you for your detailled instructions.  Unfortunately I'm not quite there with my VAIO-P.

I have followed your instructions to the letter, but even on re-booting from CLI I still get the Low Graphics Mode error. When I view the error log I get the following message:

xf86MapVidMem: Could not mmap framebuffer (0x7f6a3010,0x800000) (Operation not permitted)

I understood this to be the same error which AdamW referred to in his linked article above, and why entering mem=1500MB is required. Trying that originally, or your version of nosplash mem=1500MB still provides the above error.

Am I perhaps placing it in the wrong place within the file?

---

### Post by takezero on 2009-07-22
i managed to get the poulsbo driver working on my vaio-p.... doesnt look like 3d works properly for me tho, and occasionally X will just hang..... either a hard freeze (no response from mouse etc) or the interface just freezes but i can still move the mouse (no response from mouseclicks) and ctrl+alt+f[x] to drop to a console doesnt work.

Any ideas on how to stop the freezing? this, and useable 3D with composite etc, is the ONLY thing in my way to having a perfect Vaio-P!! grrrr

Grub kernel line is:

```
kernel          /boot/vmlinuz-2.6.28-13-generic root=UUID=c35d1d57-59d3-4611-acb4-fa4d81fa3acc ro quiet nosplash mem=1500MB
```

---

### Post by optimistique1 on 2009-08-04
Hi All

Can anyone advise me how to do the following two commands in Ubuntu :

(4a.) Add the line 'psb' to /etc/modules

5. Modify/add to the parameters of kernel 2.6.28-13 in /boot/grub/menu.lst: nosplash mem=1500MB

Many thanks

Garry

---

