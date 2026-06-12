---
title: "Problems with graphics, sound, and upgrading on Ubuntu 11.04"
date: 2012-01-10
forum: Hardware
---

### Post by cmoleary on 2012-01-10
Hello, 

I'm new to both Ubuntu and this forum so I apologize in advance if this has been solved already. 

I'm  using a Dell Inspiron 9300 running Ubuntu 11.04 (Natty) and I am  experiencing a few major problems with both hardware and software. 

Firstly,  after playing Grand Theft Auto III via Wine. My system began  experiencing 3D rendering problems including problems with the Unity  interface. To help explain what is happening, I have included  screen-shots with descriptions below ... 

   

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210598&stc=1&d=1326239014[/IMG]
This  is the Unity 3D interface on my system. As a work around I either use  the Ubuntu Classic (No Effects) or the Unity 2D options. 


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210562&stc=1&d=1326179459[/IMG][IMG]http://ubuntuforums.org/attachment.php?attachmentid=210599&stc=1&d=1326239014[/IMG]
Here, Google earth is having trouble rendering the globe. 


I  have taken a few steps to remedy this issue. First, I reinstalled the  X.Org driver. When the problem persisted, I removed the X.Org driver and  replaced it with fglrx, only to find that ATI dropped hardware  acceleration for my card (ATI Radeon Mobility X300). I reverted back to  X.Org then I tried backing up my system and reinstalling Ubuntu. Again,  the problem continued occurring. My guess is that it is something to do  with the firmware. If that is the case, how do I fix this? 


Another  problem I am having maybe related to the one above. When attempting to  upgrade to 11.10 (Oneiric), the install fails right before restarting,  leaving the system unusable. I've tried upgrading twice and the same  thing happened each time. I read that it could be related to the problem  I'm having with the graphics card as the installer may have trouble  communicating with it. 


Lastly, my computer is having some  latency issues with sound. I'm using a Sigmatel C-Major Audio card and  when I record or listen to certain files, like the Ubuntu logon sound,  it skips and distorts. This does not happen all the time and I have been  able to watch videos on YouTube without many issues. 


I  apologise for asking for help with so many things in one thread, but  I've tried browsing other forums for answers and I haven't found anyone  with these specific problems. 

Thanks in advance, 

Conor

---

### Post by Mark Phelps on 2012-01-11
Read through the info in the link, there may be some things you can try:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by cmoleary on 2012-01-11
Ok I tried getting some additional information by typing "LIBGL_DEBUG=verbose glxinfo" and I get this error ... 


> 
libGL: OpenDriver: trying /usr/lib/dri/tls/r300_dri.so
libGL: OpenDriver: trying /usr/lib/dri/r300_dri.so
libGL: Can't open configuration file /etc/drirc: No such file or directory.


---

### Post by MoreOrLess on 2012-01-11
Try the xorg-edgers ppa for updated video drivers. [https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")

For sound, post your alsa info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

