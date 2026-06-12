---
title: "nvidia 7600 not displaying tty"
date: 2007-01-18
forum: Hardware &amp; Laptops
---

### Post by niemand on 2007-01-18
I have my new laptop and this has been the easiest install yet. It is an MSI 171772-2 with a TL-60 and nearly everything is working with 6.06 LTS right out of the box.

The only problem that I am having is with the display. When I do a ctrl-alt-F1 I see nothing when I should see tty1. I log in anyway and do a 'cat > /tmp/t.t' and type some line. I then log out and go back to X11 (ctrl-alt-F7) and check for the file. Sure it enough it is there with the line I just typed. So, what in my xorg.conf do I need to add or remove to fix this? I have checked my /var/log/Xorg.0.log and there are no errors. If people have questions I will do my best to answer them and post more information as requested. I do not want to post my xorg.conf or Xorg.0.log without prompting because it is a lot of information.

I want to say thanks for any and all help in advance.

---

### Post by malachias on 2007-02-20
I've had the identical problem.
There are basically three ways to fix it.

1) use the nvidia legacy drivers - worked for me, but you may have issues if you try to run compiz or beryl or other brand-new eyecandy stuff
2) wait until feisty comes out or upgrade now. Apparently they fixed the problem in the new kernel
3) recompile the kernel without vesafb; ([http://www.nvnews.net/vbulletin/showthread.php?t=81256](http://www.nvnews.net/vbulletin/showthread.php?t=81256))

You're not alone with this problem =P Heh I know it can be hard to search for it though ;)

---

