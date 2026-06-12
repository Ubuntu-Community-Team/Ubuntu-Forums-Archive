---
title: "Chaintech 6600Gt and xorg config"
date: 2005-07-18
forum: Hardware &amp; Laptops
---

### Post by inbrednedd on 2005-07-18
Hey all,
I am using a Chaintech 6600Gt, and when I enter into Xorg upon login, it seems as if there are four individual displays laid overtop each other.
Needless to say, this makes xorg unusable. 
I am trying hard to determine whether it is a problem with the monitor that I am using, or with the card. My previous computer under this monitor suffered under all debian distros with the same problem, however Red Hat worked. 
I managed to get KNoppix to work(same problem) by using the cheatcode
fb800x600   which means it uses a fixed  framebuffer size. 
by using grub prompt, I enttered the boot option vga=789 which means a fixed framebuffer size of 800x600. This noticeably alters the display of the non X text in the login (the text displayed fine to begin with), but when x initializes, the problem resumes. 

The monitor im using requires a refresh of 60hz, and 800x600 or else it does not display correctly. 
Can someone post a working xorg file for a Nvidia 6600Gt? Please help me configure the xorg config through command line.

Thanks
Pat Mahoney

---

