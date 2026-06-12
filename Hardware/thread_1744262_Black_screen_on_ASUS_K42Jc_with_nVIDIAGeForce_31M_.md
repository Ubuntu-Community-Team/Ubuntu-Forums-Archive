---
title: "Black screen on ASUS K42Jc with nVIDIAGeForce 31M  after loading 'recommended' driver"
date: 2011-04-30
forum: Hardware
---

### Post by Ceriyx on 2011-04-30
Hi,
My problem is as described above, I have 10.04 32-bit Wubi installed, which was running fine until I decided to install the proprietary driver. Looking through the other threads I can see that maybe this wasn't such a good idea. I get Windows boot menu, then Grub2 menu showing kernels etc, then system prompt, then black screen. I have a LiveCD. Can someone tell me what I should do to activate the new driver or restore my system?
Best regards...

---

### Post by Ceriyx on 2011-05-06
Hi all,

I'm calling this "solved' even though I don't really understand what's going on, so if anyone feels they can add some tips or advice, very much appreciated. suffice to say that I have my screen back.

First bit was booting from LiveCD and mounting my file system using instructions given in the wubimegathread:

```

sudo mkdir /media/win  
sudo mount /dev/sda5 /media/win 
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt 

```Then accessing my installation with 'chroot'

```

sudo chroot /mnt

```I found some instructions for installing nVIDIA drivers manually at 

[www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx]("http:////www.ubuntugeek.com/how-to-install-nvidia-drivers-manually-on-Ubuntu-10.04-%28Lucid-Lynx%29")

which told me how to manipulate the module blacklist:

> 
Open module blacklist as admin
```

gksudo gedit /etc/modprobe.d/blacklist.conf

```Add these lines and save
```

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

```I ran the following instruction, to delete existing nvidia components, just to see what was there but took the "N" option:
```

sudo apt-get --purge remove nvidia-*

```Specifically, I ran this command from the LiveCD and found 4 packages; I then did the mount etc as described above and found 6 packages listed, which includes the ones I downloaded when I attempted the installation in the first place. My reasoning is that recovering my previous configuration was my priority and getting a working nVIDIA installation is secondary. I have the manual-install driver and may have a go at this later.

I then logged out, shut down, and rebooted through the hard drive.

I got a message box in very simple-form telling me that my drivers were missing and asking me what I would like to do, offering viewing Xorg config, troubleshooting etc. I can't be more specific, unfortunately, because I clicked on boxes and let it do what it wanted, but I did get a rather lengthy log file of errors, which I copied but was unable to paste anywhere. Eventually it told me it would load in "low-graphics mode", which it did, judging by the size of the text elements. 

I now had my system back, opened some programs, everything seemed fine, no obvious signs of low graphics rendering, text elements usual size etc.

I shut down, rebooted. This time the system went up as normal, no messages about lost drivers, everything normal, so it seems the system repaired itself second time round.

As I said earlier, I really don't understand why this has worked, although I notice that dropping out nouveau and tv services is consistent with some of the instructions given in other cases. I'll try and tune up the system as I go, so any hints will be much appreciated. On the other hand I'm a bit disappointed that I've had to do it all myself - I'm pretty new to Ubuntu and I had hoped for some help along the way.

Cheers, Ceriyx:smile:

---

### Post by FariAzz on 2011-05-27
The NVIDIA Optimus technology of your laptop is not supported in Linux, some advances have been done, but it's not solved yet.

[https://github.com/MrMEEE/bumblebee](https://github.com/MrMEEE/bumblebee)
[https://github.com/MrMEEE/bumblebee/issues/111](https://github.com/MrMEEE/bumblebee/issues/111)
[http://linux-hybrid-graphics.blogspot.com/](http://linux-hybrid-graphics.blogspot.com/)
[http://www.martin-juhl.dk/2011/05/optimus-on-linux-problem-solved/](http://www.martin-juhl.dk/2011/05/optimus-on-linux-problem-solved/)
[http://forum.notebookreview.com/linux-compatibility-software/473915-no-support-nvidia-optimus-linux.html](http://forum.notebookreview.com/linux-compatibility-software/473915-no-support-nvidia-optimus-linux.html)
[http://www.nvnews.net/vbulletin/showthread.php?t=144750&page=2](http://www.nvnews.net/vbulletin/showthread.php?t=144750&page=2)
[https://launchpad.net/~hybrid-graphics-linux](https://launchpad.net/~hybrid-graphics-linux)

---

### Post by Ceriyx on 2011-06-30
Hi FariAzz,
Thanks for this, I've been using the system as it runs from the above  and searching around for some guidance that seems to match what I can  find on my installation, so various things with hwinfo, cvt, xrandr,  xorg.conf, none of which quite matches. Searching around for advice re  Optimus produced pretty much what you say: "Optimus technology in your  laptop is not supported in Linux", which has left me very wary of  fiddling 'til I know what burns, as they say. My remaining present  current usage issue is, not surprisingly, the loss of OpenGL. I'll have a  go with the bumblebee script, hoping it's a one-click fix, although I  have to note that my wubi is 32-bit, it's reassuring that it's worked on  some other ASUS K42Js.
Thanks again...

---

