---
title: "Screen Tearing"
date: 2017-07-22
forum: Hardware
---

### Post by Richard_Romick on 2017-07-22
Greetings Ubuntu experts,

I am having some issues with Screen Tearing.  I have followed the advice of many forums on the issues and have enabled "Tear Free" in my intel config file, which I have in the attached file.  The only difference is my xorg.conf.d is in /usr/share/X11/ instead of /etc/X11/

I may have caused this issue myself when I installed the oibaf PPA for updated MESA driver.  I don't remember if I had this issue before then, but I uninstalled the PPA and reverted back just to make sure.  I included part of glxinfo in the file also.

I know just about enough in Ubuntu to get myself in trouble.  I really feel like I just need someone to point me in the right direction.  Any help you could provide would be greatly appreciated.

Edit: I've discovered that, even though I used ppa-purge on the oibaf PPA, I still am running Mesa.  

client glx vendor string: Mesa Project and SGI
OpenGL core profile version string: 3.3 (Core Profile) Mesa 17.2.0-devel
OpenGL version string: 3.0 Mesa 17.2.0-devel
OpenGL ES profile version string: OpenGL ES 3.0 Mesa 17.2.0-devel

Should I be running Mesa at this point, or did I not fully remove the oibaf Mesa drivers?  Could this be the problem.

---

