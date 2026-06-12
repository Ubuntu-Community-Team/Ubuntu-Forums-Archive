---
title: "screen black after installing nvida drivers"
date: 2007-05-04
forum: Hardware &amp; Laptops
---

### Post by venkman on 2007-05-04
I installed ubuntu 7.04 today on my dell Latitude D620 with a 1440x800 screen and a nvidia quadro nvs 110m, I just had a screen resolution of 1280x800, so i activated the driver icon for the binary drivers (are they called like that? )  the one for my intel wireless adapter was already activated, the one for my graphics card wasn't

after a reboot i only saw and see the boot screen and than it turns black, i can login with my username and password because i can see my hdd light flickering if I enter them, but the screen is like switched off. When I switch to a console witch ctrl alt F1 I can login onto the console.

Which steps can I take to make the GUI work again? Googling hasn't really helped me so far.

I didn't install anything else before, so it was a completely fresh installation and there is no hardware problem with my notebook, in windows everything works fine, so this problem probably occurs to everyone with that notebook and configuration.

thanks in advance

venkman

---

### Post by rutsche123 on 2007-05-04
Hi,

I have the same problem with my notebook... so far i found out that instead of the notebook display, the external vga output is used... if i plugin an external lcd, i have my desktop there... 
any idea how to change the monitor output to the notebook screen?

---

### Post by marquarc on 2007-05-04
I'm having the exact same problem, also on a Dell Latitude. Would love to see a workaround/fix for this.

---

### Post by rutsche123 on 2007-05-05
try to add the following to your Screen section:
    Option         "TwinView" "True"
    Option	   "TwinViewOrientation" "Clone"

this worked for me :)

---

