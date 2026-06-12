---
title: "Blank Toshiba Portege M200 help!"
date: 2007-11-21
forum: Hardware &amp; Laptops
---

### Post by venator260 on 2007-11-21
So I have in my possession a blank Toshiba Portege M200. 

Problem is that it has no operating system, no CD drive, and doesn't recognize the external CD-ROM drive that I have (Lite-on EZ-DUB).

I would like to install Gutsy Gibbon on this machine, but am confused as to how. 

Has anyone ever attempted this before, or does anyone have any ideas?

Thanks

---

### Post by Craigus on 2007-11-21
You can do a netboot install. Have a look here :

[http://yellowsub.wordpress.com/2007/06/30/i-want-to-install-linux-on-a-toshiba-portege-3490ct-but-dont-know-how/#comments]("http://yellowsub.wordpress.com/2007/06/30/i-want-to-install-linux-on-a-toshiba-portege-3490ct-but-dont-know-how/#comments")

and here:

[http://yellowsub.wordpress.com/2007/07/28/i-did-it-i-installed-ubuntu-linux-onto-the-toshiba-portege-3490ct/]("http://yellowsub.wordpress.com/2007/07/28/i-did-it-i-installed-ubuntu-linux-onto-the-toshiba-portege-3490ct/")

Edit: also have a look here:

[http://www.adebenham.com/laptop/toshiba_m200.html]("http://www.adebenham.com/laptop/toshiba_m200.html")

noting the comment about :
> Sadly the standard install images didn't include the driver for the onboard ethernet so instead I used the debian-installer images. Once I figured this out all went smooth.

This might be an issue with the Ubuntu netboot image, I'm not sure.

---

### Post by venator260 on 2007-11-22
Thanks, Craigus

Typing this from my new (to me) laptop. The netinstall described here: [http://ubuntuforums.org/showthread.php?t=327597](http://ubuntuforums.org/showthread.php?t=327597) worked rather well. I simply changed the url of the netinstall directory from edgy to gutsy and I now have a working Ubuntu install.

There are some things at the end of this that also helped: [http://yellowsub.wordpress.com/2007/07/28/i-did-it-i-installed-ubuntu-linux-onto-the-toshiba-portege-3490ct/](http://yellowsub.wordpress.com/2007/07/28/i-did-it-i-installed-ubuntu-linux-onto-the-toshiba-portege-3490ct/)

I had to do the apt-get install ubuntu-desktop after the base system was installed, just like the post said. I then just restarted from the command like (sudo shutdown -r now).

Edit: also, when I was assigning an IP adress in the tftpd tool, I had to fudge the IP adress a bit to get it to work. There were several computers assigned an IP adress on the network, and I think that I had to pick one that was unused.

---

### Post by Craigus on 2007-11-22
Excellent. I'm glad to see that it worked for you. I'm not sure what the issue is with having to separately install ubuntu-desktop, I've never had that issue.

---

