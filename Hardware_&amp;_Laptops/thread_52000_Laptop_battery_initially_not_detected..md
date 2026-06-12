---
title: "Laptop battery initially not detected."
date: 2005-07-26
forum: Hardware &amp; Laptops
---

### Post by naomarik on 2005-07-26
Hi. I don't know why but when I boot up into Ubuntu 5.04 it does not detect a battery. After removing and reinserting the battery it gets detected and shows me all the information perfectly. How would I avoid doing this and configure it so it detects it immediately?

My second question involves the laptop's FN keys. I noticed that when I shut my laptop's lid, the screen goes completely blank. Ubuntu is the only distribution I've seen that does that with my laptop. Dmesg says that agpgart is responsible for this. I'm wondering if I can make it so I can dim my laptop's screen with the FN buttons like I can in Windows. My laptop is a Sony PCG-K23.

Any help would be greatly appreciated.

---

### Post by madchicken on 2005-07-26
I've the same problem with a Vaio PCG-K195HP.
You can also make a:

```

sudo modprobe -r battery
sudo modprobe battery
killall gnome-panel

```

to avoid to unplug-plug the battery (because you can't unplug the battery when you are using it  :smile: ).
Someone told me to recompile the kernel with module battery built-in to avoid this problem. I tryed this solution without success.  ](*,) 

For Fn buttons...no way to make them work for me: it seems that no char codes are detected by pressing them.
The only thing I could make work is changing brightness of the screen using the sony_acpi driver. You can find it here:

[http://www.popies.net/sonypi/sony_acpi.tar.gz](http://www.popies.net/sonypi/sony_acpi.tar.gz)

bye

--Pierpaolo

---

### Post by naomarik on 2005-07-27
Thanks for the reply. Your method for getting the battery works! I haven't yet tried the dimming the screen but I'll let you know how that works out.

---

