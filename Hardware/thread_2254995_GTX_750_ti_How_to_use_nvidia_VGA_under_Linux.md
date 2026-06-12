---
title: "GTX 750 ti: How to use nvidia VGA under Linux?"
date: 2014-12-01
forum: Hardware
---

### Post by tassadar2 on 2014-12-01
Hi all,
 
I've been using a computer with kubuntu during sometime, it is an Intel  with an Intel VGA graphics card and after some problems I could make it  work ok. (Kubuntu 14.10).
 
Now I've install a nvidia graphics card (GTX 750 ti) and it doesn't work  correctly, it is one of those lot of things that under Windows is  downloading a file and installing but with Linux it's a whole oddisey...
 
I tried to install drivers doing this:
 
 [B]sudo apt-get update
sudo apt-get install linux-source
sudo apt-get install linux-headers-generic
sudo apt-get install linux-image
sudo apt-get install nvidia-current[/B]
 
Result: after reboot I could'n even set native resolution of screen (full-HD). Then I remove drivers with:
 
 **sudo apt-get purge nvidia-current**
 
and then downloaded official drivers from nvidia website and installed them:
 
 [B]Hit CTRL+ALT+F1 and login using my credentials.
kill current X server session by typing sudo service lightdm stop
Enter runlevel 3 by typing sudo init 3 and install the*.run file.
Reboot
 [/B]
After reboot I can use full-HD resolution and 3d acceleration seems to  work, but I have a huge tearing problem playing videos, games and  anything.... I've change composition type from Xrender to OpenGL 3.1  since using Intel VGA I also had big tearing with xrender. But problem  is not solved (it worked with intel card).
 
Then I've check vsync is enabled in the OS, and it is "redraw all scene", and it's also enabled in XBMC.
 
I also installed anther nvidia card in other computer some time ago  (Kubuntu 13.04) and I had exactly the same problem. No talk about  AMD/ATI cards, I left them as impossible under linux long ago....
 
Mu question is.. How can I confugure this nvidia card to word as it  should? (it is, avoiding this huge tearing effect that makes impossible  watching a video).
 
Regards and thanks in advance.

---

### Post by oldfred on 2014-12-02
I always suggest installing from Ubuntu's repository, but you may be the exception. Very new hardware may need the newest video driver, support software & kernel.

I still better to use ppa, not a direct download from nVidia.
The ppa  usually is updated with latest kernels so best to check what it has and use newest.

 Maxwell 750 
[http://ubuntuforums.org/showthread.php?t=2214805](http://ubuntuforums.org/showthread.php?t=2214805)
[http://ubuntuforums.org/showthread.php?t=2252908](http://ubuntuforums.org/showthread.php?t=2252908)
[http://www.phoronix.com/scan.php?page=article&item=evga_geforce_gtx750&num=1](http://www.phoronix.com/scan.php?page=article&item=evga_geforce_gtx750&num=1)
[http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell_750linux&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell_750linux&num=1)

And with the new video driver, you usually need the support packages and perhaps even a newer kernel. 

I think even newer versions are now available, but process is the same.

 Install Nvidia 340.24 from ppa:xorg-edgers/ppa
[http://www.sysads.co.uk/2014/07/install-nvidia-340-24-driver-ubuntu-14-04/](http://www.sysads.co.uk/2014/07/install-nvidia-340-24-driver-ubuntu-14-04/)
All the current drivers xorg-edgers PPA
[https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa/+packages](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa/+packages)
Oibaf PPA discusion
 [http://www.phoronix.com/scan.php?page=article&item=ubuntu_1310_oibaf&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1310_oibaf&num=1)
New kernels ppa
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D](http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D)

---

