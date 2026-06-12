---
title: "Specific FAI documentation"
date: 2009-09-25
forum: Installation &amp; Upgrades
---

### Post by louigi600 on 2009-09-25
Where can I get Ubuntu specific FAI (Fully Automated Install) documentation ?

---

### Post by Lars Noodén on 2009-09-25
There's not a whole lot, if anything, that deviates from either Debian or Red Hat / Fedora.  However, here is a pair of links:

[https://help.ubuntu.com/7.04/installation-guide/i386/automatic-install.html](https://help.ubuntu.com/7.04/installation-guide/i386/automatic-install.html)
[https://help.ubuntu.com/7.04/installation-guide/i386/appendix-preseed.html](https://help.ubuntu.com/7.04/installation-guide/i386/appendix-preseed.html)

I did a lot with Kick Start around 2001 and later 2007-2008.  Based on that, I would say start with pre-seed instead.  There are no built-in debugging tools, so errors will require a bit of skill to track down.  

If you have difficulties, you can also install packages after the first boot using a script.  The list of packages in kickstart cannot be very long:
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/135284](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/135284)
[https://bugs.launchpad.net/ubuntu/+source/kickseed/+bug/145162](https://bugs.launchpad.net/ubuntu/+source/kickseed/+bug/145162)

One thing to note is that the kick start configuration and IIRC the preseed can be served via http or anonymous ftp.  Either of these can be passed as kernel environment variables in Grub.  So you can burn a CD pointing to your web server or ftp server and then make the changes there.  That mean you only waste time rebooting between each iteration.  

Alternately, if the target machine is afflicted with netboot capabilities, then you could use pxe boot.  Do that only if you are  on your own separate LAN since it has the potential to disturb others.  [dnsmasq](http://packages.ubuntu.com/jaunty/dnsmasq) would be the package to look at to get started there for netboot.

---

### Post by louigi600 on 2009-09-25
Thanks for the hints ... I'll have a look bot un the mean time I've another urgent question:
How the hell do I make a local ubuntu release mirror ?

Looking at the FAI documentation they talk about mkdebmirror command that is not amongst the FAI ubuntu packages. So I guess there must be something ubuntu specific ?

---

### Post by louigi600 on 2009-09-26
Found some old documentation on mirroring ubuntu for version 7 ... I'm adjusting some things and hoping it's still working for 9 :-)

---

### Post by Lars Noodén on 2009-09-26
Mirroring is just making a set of directories and information files that conform to some specifications.  Once that is done, FTP or HTTP or RSYNC serves up the data as normal.  
[http://www.debian.org/doc/manuals/repository-howto/repository-howto](http://www.debian.org/doc/manuals/repository-howto/repository-howto)

apt-cacher is a quick way, do your install the first time with apt-cacher and then make the cache directory available via FTP or HTTP.

---

### Post by louigi600 on 2009-09-26
I'm not interested in making an official mirror ... but just a local mirror for local install purposes.
I found a lot of documentation that describe the process logically or from a debian point of view. I needed something that showed me the commands for doing it for Ubunto.
For example [http://www.ubuntu.com/getubuntu/mirror](http://www.ubuntu.com/getubuntu/mirror) was pretty useless


I've the link on the pc at work where I left the mirror process running last friday .... I'll see if it worked next monday.
I've been trying to search again to fint the notes I folowed but I was unable to find them again ....
I found this though that has a different approach: [http://ubuntuforums.org/showthread.php?t=599479](http://ubuntuforums.org/showthread.php?t=599479)
I think I was using the debmirror approach .... whatever if what I did friday failed I'll try this way.

Maybe this is what I used at work: [https://help.ubuntu.com/community/Debmirror](https://help.ubuntu.com/community/Debmirror)

---

### Post by louigi600 on 2009-09-28
I can confirm that I used the above debmirror notes and that with a little modification in order to mirror jaunty  this morinig I found something like 26Gb of stuff in /home/UbuntuMirror after the script terminated with:
```
Downloaded 26021 MiB in 13399s at 198.58 KiB/s
Everything OK. Moving meta files.
Cleanup mirror.
All done.
```

---

