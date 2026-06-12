---
title: "Camera and other removable media problem."
date: 2006-10-29
forum: Hardware &amp; Laptops
---

### Post by cmavr8 on 2006-10-29
I am using UBuntu linux for about 4 months now. I was using Dapper on my new laptop (Lenovo 3000 V100) and after lots of googling and hours modifying files I had about 60% of the hardware working.

Yesterday I upgraded to Edgy. I have booted the live cd twice, and the sd reader of the laptop was working PERFECTLY (something not true in dapper). 

When I updated to edgy, neither the sd reader, nor my usb-connected camera works.

The camera used to work with dapper (no modifications needed). A window poped up and I could download the pics. Now I need ot execute "gnome-volume-manager-gthumb %h" and the app starts properly.

The SD problem is that when I insert it, the SD led lights on (that was not happening in dapper) but the computer starts freezing. First the bars, then the desktop, finally the mouse. 

Control-alt-del, control-alt-backspace, control-alt-F1, alt-prtsc-S-U-B won't work.

HARD (poweroff) reset is required.

What more info should I give you? Kernel used? The 3000 V100 notebook is a dual core one, so I use the generic kernel Inot the one named xxxxx-386) so that both proccessors are recognized. (from the two EDGY installed)

I'll get the exact version.

Thanks for reading!

---

### Post by cmavr8 on 2006-10-29
Ok, I have the kernel versions.

Booting the 2.6.15.26-686 or the 2.6.15.27-686 kernels will start ubuntu as before (dapper days. I think Upstart is not used) and no SD-Card led is lit when I insert it.

Booting the 2.6.17.10-386 or 2.6.17.10-generic will do what I described before. Complete system freeze. (although I managed to restart using alt-prtsc-s-u-b once...)

Hope this helps...

---

### Post by cmavr8 on 2006-10-30
I have also found out that my suspend (to ram) does not work (black screen after resuming, then only cursor showing, finally freeze [alt-prtsc-s-u-b works here, though]) (sometimes it will freeze during trying to suspend), when I use the new kernels (after 2.6.15.27. This kernel ALSO had problems with suspend).

Also, my sound works once in a blue moon (once every 2-3 reboots). If I don't hear the sound calling me to enter username, I won't have sound at all until I reboot again...

Anybody? Please help...

---

### Post by mercmobily on 2006-12-12
Hi,

I am not sure this will help. I didn't even know things used to work with Dapper!
I installed edgy, and esperienced the same stuff as you: SD card doesn't wor, suspend OFTEN freezes the machine, sound on time out of three.

I upgraded to feisty (yeah, scary...).

Well:

* The sound always works
* THe freezing when resuling is quite rare
* No sign of the SD card working at all. I don't even know what it would look like if it worked...

So, I'd upgrade to feisty, at least you'll see an improvement.

I am amazed to hear that things were actually better with Dapper... Maybe downgrading would be better? :-?

Merc.

Free Software Magazine
[http://www.freesoftwaremagazine.com](http://www.freesoftwaremagazine.com)

---

### Post by cmavr8 on 2006-12-12
What problems did you experience with sound?
My SD now works ok but not with 2gb SD. 1gb works fine...

---

### Post by mercmobily on 2006-12-12
Nevermind that idea.

I rebooted my V100 with Feisty, and guess what, there's no sound what so ever.

Very disappointing.

I will reboot and cross my fingers.

Merc.

---

### Post by cmavr8 on 2006-12-12
Ok, keep us posted

---

### Post by david2b on 2007-03-04
> **cmavr8 said:**
> Ok, keep us posted
same issue here : 
[http://www.ubuntuforums.org/showthread.php?t=369423&highlight=lenovo+3000+v100](http://www.ubuntuforums.org/showthread.php?t=369423&highlight=lenovo+3000+v100)

---

