---
title: "Multi Monitor doesn't work after 16.04 upgrade"
date: 2016-05-12
forum: Hardware
---

### Post by colby8 on 2016-05-12
I upgraded my workstation from 15.10 to 16.04 and lost the ability to use multiple monitors.  I used to be able to use 3 monitors, the built in display on my thinkpad w530, and 2 external monitors connected by mini Display Port and VGA.  I used to use the x.org driver on 15.10, because the nvidia one didn't work with all 3 monitors.  

I have tried the nvidia and x.org drivers with 16.04 neither work.  With x.org now it only detects 2 displays and when I enable both it seems to combine them into one desktop (scretches it across both displays) which I can't use until it times out and sets it back to what it was before.  I tried Nvidia's drivers and settings utility and can't get it to work either.  At first I could get it to work with 2 displays (but only one of the external displays) with 16.04 but not now.  

I am wanted to get all 3 displays working again.   

Is there a way to use the old x.org driver?  reset the builtin display settings app so I can get it to work with the 2 displays again. I don't want to have to reinstall 15.10.

Thanks

---

### Post by QIII on 2016-05-12
Hello!

It would be very helpful if you would give the exact model of the graphics adapter and the exact driver you are using.

Cheers!

---

### Post by colby8 on 2016-05-17
Thanks for replying,

I have a nvidia K1000M

the x.org driver is called nouveau display adapater driver from xserver-xorg-video-nouveau. 

The nvidia drivers I tried were 361.42 and 304.131.

---

### Post by colby8 on 2016-05-28
Anyone have some ideas?  I ran the 15.10 live and was able to get 3 monitors again. The name of the driver is the same.  I don't know if the driver is updated, can anyone tell me how to tell? I expect x.org was updated.  16.04 is supposed to have hardware support for 5 years but it doesn't seem to support my hardware.  Is there a way to bring this to the developers to see if they can fix it?   I know this laptop isn't very new but it is a pretty good machine and I would like to use the current ubuntu release, especially since 15.10 will be end of life soon.

---

