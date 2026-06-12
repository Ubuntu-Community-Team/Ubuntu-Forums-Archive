---
title: "pci error assigning properties"
date: 2021-03-21
forum: Hardware
---

### Post by pulp157 on 2021-03-21
Hi, 

I am new to the community and new to using ubuntu.

I installed UBUNTU on an old Mac (A1225) and it worked pretty good. But here is the problem: After using it for about a day, several power cycles and restarts, it just stopped booting. 
It will start and then stop at a black screen saying " [0.537245] pci 0000:03:00.0: error -61 assigning properties" .
No matter what I do, it will always stop right there. I am not seeing any graphics or anything resembling UBUNTU. 

I tried booting from a USB, which will get me in the GRUB. But again, no matter what option I choose, it will go right to the above mentioned error message. 

Since I've been using this just for a day, I can totally wipe the whole thing no problem. I just don't know how I can get anywhere if the bootable USB isn't even doing anything. 
HELP !

What can I try ?

---

### Post by gnuzi14 on 2021-04-18
I have seen this error as well - happened on al older MacBook Pro late 2008.
I thinking it is this one:
[https://everymac.com/systems/apple/macbook_pro/specs/macbook-pro-core-2-duo-2.4-aluminum-15-late-2008-unibody-specs.html](https://everymac.com/systems/apple/macbook_pro/specs/macbook-pro-core-2-duo-2.4-aluminum-15-late-2008-unibody-specs.html)

It wouldn’t come up by itself with an Ubuntu (elementary 5) and also wouldn’t start on a rescue system.
I got a bit further when starting the computer and having the PRAM / NVRAM resetted by pressing the [COLOR=#333333][FONT=&quot]Option-Command-P-RCombo[/FONT][/COLOR]

Next step. I will try is to a chroot installation of an updated Kernel (later that 4.19) and see how this turns out.
Will add a remark if this did the trick.

---

