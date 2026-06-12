---
title: "Graphics problem giving periodic blank screen on boot"
date: 2012-04-11
forum: Hardware
---

### Post by Blue Rabbit on 2012-04-11
Hello all, 

I have an issue with graphics that I can't solve myself. 
I am running Ubuntu 11.04 at the moment, but I have experienced the issue with 11.10 also. 

The problem is that when I boot my machine, nothing is shown on the screen. However, from the sounds the system makes I know that the system is otherwise up and running. Working headless, I can log in, use gnome-do to start a terminal and issue a reboot-command to reboot the system.

Having rebooted anywhere between 1 and 4 times, the system comes up correctly and I can use it without any significant problems. I do notice some very minor graphics-glitches when using e.g. eclipse, but nothing that bothers me. 

I have no idea of how to start fixing this problem, so I hope that someone can understand what is going on. I have collected the following log files that contains some errors that are present only when I get a blank screen. 

[http://lindbergonline.dk/attachments/syslog.txt](http://lindbergonline.dk/attachments/syslog.txt)
[http://lindbergonline.dk/attachments/dmesg.txt](http://lindbergonline.dk/attachments/dmesg.txt)
[http://lindbergonline.dk/attachments/boot.log.txt](http://lindbergonline.dk/attachments/boot.log.txt)  (Included for completeness, but I doubt these errors are relevant to my problem)

I am not sure which system information is relevant, but ask for it and I will provide it. 
I am guessing that you would like to see this: 
[http://lindbergonline.dk/attachments/lspci.txt](http://lindbergonline.dk/attachments/lspci.txt)

Thank you in advance

---

### Post by oldfred on 2012-04-11
Welcome to the forums.

I think the important part is this, but I do not know Radeon video as I have nVidia. This repeats many times in your dmesg. You can try the Radeon or generic setting I think.

```
[   14.898784] WARNING: at /build/buildd/linux-2.6.38/drivers/gpu/drm/radeon/radeon_gart.c:176 radeon_gart_bind+0x1ab/0x1c0 [radeon]()
 [   14.898786] Hardware name: System Product Name
 [   14.898787] trying to bind memory to unitialized GART ! 
[   14.898788] Modules linked in: nfsd exportfs nfs lockd fscache nfs_acl auth_rpcgss sunrpc snd_hda_codec_realtek ppdev radeon snd_hda_intel(+) snd_seq_midi snd_rawmidi snd_hda_codec
   snd_hwdep snd_seq_midi_event snd_pcm asus_atk0110 ttm psmouse snd_seq parport_pc serio_raw snd_seq_device drm_kms_helper snd_timer drm snd i2c_algo_bit soundcore snd_page_alloc lp parport hid_logitech ff_memless usbhid hid atl1c
 [   14.898809] Pid: 237, comm: plymouthd Tainted: G        W   2.6.38-13-generic #57-Ubuntu 
```
Have you tried mode settings?

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

---

### Post by 2F4U on 2012-04-11
Well I can't give much help, but I found a bug report and the errors look similar to yours:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/580918](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/580918)

Unfortunately, the bug is still unresolved.

---

### Post by oldfred on 2012-04-11
at the bottom of that bug it says it is a duplicate of this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/656486](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/656486)

And that only shows fixed in Oneirec & Precise.

---

### Post by Blue Rabbit on 2012-04-12
Thank you for your responses.

I have added the NOMODESET option to my grub configuration and I will see if that solves my issue. However, as the issue is periodic, I will need time to evaluate the effect. If necessary I will look at the other suggestions next. 

As far as the bug-reports go, they may have been given a status of fixed, but their comments sadly suggest otherwise.

I'll report back when I find out what works for me. 

Thanks

---

