---
title: "NVIDIA GeForce 7300 GT won't boot"
date: 2007-12-04
forum: Hardware &amp; Laptops
---

### Post by boogie606 on 2007-12-04
I dual boot Vista and &.10 Gutsy Gibson.  I just installed the above mentioned graphics card and now cannot boot into ubuntu.  When I try booting normally, I get the ubuntu logo with the progress bar, but then I get a screen with different things its' loaded all ok and the a blinking hash.
everything i try to type just comes up weird symbols.

When I try to boot into protected mode, it seems to load everything fine and then comes to a command line and I don't know how to continue.  I believe that I should be able to load the drivers at this point but I have no idea how to go about it.  I am a nub to linux.

Please Help.  Thank You.

[EMAIL="boogie606@yahoo.com"]boogie606@yahoo.com[/EMAIL]

---

### Post by marpstar on 2007-12-04
from my experience, Linux isn't real friendly with a video card swap.  You should be able to load the driver by booting into the Protected mode and reconfiguring the xserver by logging in and typing:

```
sudo dpkg-reconfigure xserver-xorg
```

and following through.  You machine should have the 'nv' driver preinstalled.  From there, you can get the rest of xorg set up and you should be able to boot into a regular mode.  

I've had this problem before and this seemed to fix it.  Good Luck.

---

### Post by boogie606 on 2007-12-04
that did it.  thank you very much.  i owe you a cup of coffee.....

---

