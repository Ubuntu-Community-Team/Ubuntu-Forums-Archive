---
title: "Linux Newbie Help?"
date: 2008-10-20
forum: Hardware
---

### Post by hightimesx420 on 2008-10-20
I have a HPDV6449US and i recently installed Ubuntu Intrepid 8.10. Everything works fine, except that the wireless adapter does not install... 
The Adapter is a Broadcom 4321AG Wireless a/b/g/n. 

Any suggestion on how i can fix this please?? i tried to follow the instructions on another post, and it worked up to the part where i should have the "wl.ko" file. 

Help?!

---

### Post by phidia on 2008-10-20
Have you installed ndiswrapper and tried to load the windows .inf file?

Keep in mind you are using a testing release and that means it's expected to have bugs-right up to the release date.

You may want to search or ask this at the development forum.

---

### Post by Ayuthia on 2008-10-20
Did you go to System->Administration->Hardware Drivers and enable the Broadcom STA option?  You will also need to disable the b43 version or else they will conflict.

If you have done this, please go into the Terminal and post the results of lshw -C network.

---

### Post by hightimesx420 on 2008-10-20
i have not tried ndiswrapper, because i heard that the system sometimes crashes...

Went to The Hardware Devices window, there's only the Nvidia Driver which if for my graphics card or either my chipset im guessing....

---

### Post by phidia on 2008-10-20
> **hightimesx420 said:**
> i have not tried ndiswrapper, because i heard that the system sometimes crashes...

Went to The Hardware Devices window, there's only the Nvidia Driver which if for my graphics card or either my chipset im guessing....

I dom't think you can get that card working in hardy without ndiswrapper.

---

