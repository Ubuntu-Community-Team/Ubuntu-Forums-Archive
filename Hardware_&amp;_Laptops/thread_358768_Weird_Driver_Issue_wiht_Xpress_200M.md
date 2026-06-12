---
title: "Weird Driver Issue wiht Xpress 200M"
date: 2007-02-11
forum: Hardware &amp; Laptops
---

### Post by packoman on 2007-02-11
Hi.
Not sure if this belong in the hardware-section of the 3D-desktop-section...

I have a weird issue with my ATI Xpress 200M of my Toshiba Laptopa and Ubuntu Edgy 6.10.
I'm using the fglrx-driver version 8.28.8 from the official ubuntu-repo together with XGL and beryl.
The problem I have is that, when I start up ubuntu, my PC crashes completely at the login-screen (i.e.: I get to see a white screen with the mouse-coursor and three grey dots where the login-prompt should be.... and I can't even switch to tty1 anymore...).
Strangely this is NOT the case, when I start WindowsXP before. After that the system boots into ubuntu perfectly and I have Xgl, Beryl and Eye-Candy galour...

The weird thing is that up to the beginning of January everything worked fine until I ran a standard upgrade of the Ubuntu and Beryl repos... :mad: 
I been trying to fix this ever since. 
Like I already said above, I'm not sure whether this is an issue with beryl or the fglrx-drivers, but I suspect the latter.

On a note:
I'd like to stick with the 8.28.8 drivers or others that are available from a repo, since don't really enjoy the hassle of the command-line installation of the fglrx-drivers.

I'd be greatefull for an suggestions or ideas, since I do feel quite helpless. And waisted vast amounts of time on this. :( 
Thanks,
            Michael

---

### Post by uberbrodt on 2007-02-22
Hmm, I've had pretty good luck with getting the fglrx drivers under Debian and Ubuntu.  It's strange that you have luck after booting into winxp first.  Did you have any special GRUB settings in place before you upgraded?

I have a Toshiba laptop that I'm trying to get Suspend to work on right now.  Once I get that out of the way I'll look into the Beryl/XGL issue.  BTW, were you able to use suspend on your Toshiba?  I have a M45-s165.

---

### Post by defishguy on 2007-03-20
For installing ATI drivers I accidentally discovered [[COLOR="Blue"]Envy[/COLOR]]("http://albertomilone.com/nvidia_scripts1.html") and it is chocked full of easy to do yet still works driver goodness.  You could give the latest drivers a try without going through any cli voodoo.

As far as suspending or hibernating I haven't figured that one out.  I did actually get it to hibernate once successfully but I strongly suspect that it was an accident.  I have an Acer 5100 that hibernates and suspends great just as long as I'm not using XGL.

---

