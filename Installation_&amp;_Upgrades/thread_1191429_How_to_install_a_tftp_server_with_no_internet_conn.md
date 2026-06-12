---
title: "How to install a tftp server with no internet connection"
date: 2009-06-18
forum: Installation &amp; Upgrades
---

### Post by RosiCru on 2009-06-18
Hi all,
 
I've recently installed ubuntu server v9.04 on a virtual machine, (different PC then the one I'm posting on), and am trying to setup a tftp server on it. This is intended to allow network switches to backup their configurations to the tftp server and download new firmware images from the tftp server. I'm using the VM as a test platform at the moment, and then I'll re-build on a production server.
 
My problem is that this machine I've installed ubuntu on is not connected to the internet, nor can it be. The network it is connected to is an isolated and private one. Every guide/advice/hint/suggestions I've found while searching the internet uses the apt-get command to install the appropriate packages. 
 
Can someone instruct me on how to manually download these packages (where), what packages I'll need and how to manually install them on the ubuntu machine? 
 
Many Thanks,
R
 
PS. I'm relatively new to linux/ubuntu.

---

### Post by iponeverything on 2009-06-19
[http://packages.ubunut.com/en/jaunty/tftpd](http://packages.ubunut.com/en/jaunty/tftpd)

get it into the VM and do:

sudo dpkg -i package-name.deb

---

### Post by RosiCru on 2009-06-19
Thanks iponeverything, that helped alot. 
 
I downloaded that package and tried to install it. It came up with errors (dependencies). So I follow them through, it turned out to only be 1x other package required (openbsd-inetd). I sucessfully installed the required packages. I then stumbled through figuring out the configuration side of it for the following 20-30mins. Configuration file I had to change is (/etc/inetd.conf), and I had to (sudo /etc/init.d/openbsd-inetd restart). Managed to get it all working in the end. :p
 
Thanks again,
R

---

