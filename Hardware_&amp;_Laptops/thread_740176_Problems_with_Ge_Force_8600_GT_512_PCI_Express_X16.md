---
title: "Problems with Ge Force 8600 GT 512 PCI Express X16"
date: 2008-03-30
forum: Hardware &amp; Laptops
---

### Post by dlovley on 2008-03-30
Hello All :)

I have a new computer running an intel quad processor and a PNY Verto GeForce 8600GT 512 MB video card. I'm running gutsy and after I select ubuntu in my grub menu I see a quick error for about 1 second or less saying something about pci failed memory blah blah blah numbers. The system then goes straight to login and runs fine.

I have nice graphics and compiz cube working like a charm with cube and 3d windows etc. When I tried  to run the newest Alien Arena game I ran into problems. It wont let me select full screen or any decent resolution at all, I just get a screen all in red listing features that did not work rendering graphics.

I used envy to install my nvidia drivers and it seems to have worked fine. In researching  this problem I see that others have eperienced similar issues and have talked about kernel  errors etc. Is this something I can fix? I have XP pro and vista running on the machine as well with no graphics problems at all. 

I'm a total linux newbie but I love Ubuntu and plan on using it for a long time. Please answer this post including commands that I can paste into terminal as if I know nothing. Thank you in advance for any help, this is a great community.

Darrel

---

### Post by dlovley on 2008-03-31
Well,

I guess it was a mystery lol. I upgraded to Hardy Heron and it solved the problem somehow. I now have a 100 percent functioning graphics card :). The error at startup is gone and things look much better overall and I think I can use  the alien arena game without too many issues. 

Now I just need to wait for the xgl-server bugs to get ironed out along with a temperamental firefox upgrade hehe.  Just thought I would post this solution for anyone else having  this error. 

Could it have been the kernel upgrade that helped my card to be fully seen and functional?

Darrel

---

### Post by nickdngr on 2008-03-31
I just built my system with the Nvidia 9600. I couldn't get Gutsy to install to save my life, so I figured I'd wait it out and see if there was an improvement with Hardy. Well, out of boredom I went ahead and downloaded it (and the 32-bit version b/c I wasn't thinking and it was the one on the site instead of the 64-bit) and Hardy worked perfectly. Completely let me use my flatscreen via dvi instead of cutting to black, which was the issue I was having with Gutsy. 

Upgrading worked for me, but I'm on a barebones system with nothing to lose.

---

### Post by stchman on 2008-03-31
> **dlovley said:**
> Hello All :)

I have a new computer running an intel quad processor and a PNY Verto GeForce 8600GT 512 MB video card. I'm running gutsy and after I select ubuntu in my grub menu I see a quick error for about 1 second or less saying something about pci failed memory blah blah blah numbers. The system then goes straight to login and runs fine.

I have nice graphics and compiz cube working like a charm with cube and 3d windows etc. When I tried  to run the newest Alien Arena game I ran into problems. It wont let me select full screen or any decent resolution at all, I just get a screen all in red listing features that did not work rendering graphics.

I used envy to install my nvidia drivers and it seems to have worked fine. In researching  this problem I see that others have eperienced similar issues and have talked about kernel  errors etc. Is this something I can fix? I have XP pro and vista running on the machine as well with no graphics problems at all. 

I'm a total linux newbie but I love Ubuntu and plan on using it for a long time. Please answer this post including commands that I can paste into terminal as if I know nothing. Thank you in advance for any help, this is a great community.

Darrel

Use Envy 0.9.10 to install the 169.12 drivers.  I have an 8800GT and it works great in Ubuntu.

First uninstall the nivdia driver then select to install the nvidia driver manually and select the 169.12 driver.

---

