---
title: "Flat Screen Says &quot;Out of Range&quot; during bootup"
date: 2008-10-17
forum: Hardware
---

### Post by krt on 2008-10-17
How do I fix the fact that during bootup, and shutdown, the screen goes blank on my flat screen monitor with an "Out of Range" notice on it?  

I have done a terminal command "sudo displayconfig-gtk" and selected my monitor and rebooted, but it still does it.

Also, if I were to change to another monitor, what is to prevent it from not working at all?

Thanks,

krt

---

### Post by benny bronx on 2008-10-17
If it is only affecting startup and shutdown screens, then you could add "startup manager" from synaptic.  It has an option of changing the resolution for those screens.

---

### Post by mjpatey on 2008-10-17
Benny is correct... I was just going to add that if you're worried about the message, dont' be; during the various stages of booting, the computer switches to resolutions that may not be supported by your monitor, and that's normal, especially with LCD screens.  If you're making it to the Desktop, you can just disregard the message.

---

### Post by krt on 2008-10-18
Well, thank you for the startup manager tip, but that did not work because the drive for this flat screen is still out of range.

The fact that it is blank (during startup and shutdown) does not worry me so much as the fact that it says "out of range" and my concern is that if the computer cannot set the frequency(s) correctly for this monitor during bootup and shut down, suppose this monitor dies, and I get a different monitor and connect it and can see nothing after it boots up?

In other words, **how does one set the monitor in an emergency without having to do a complete re-install**?

Thanks,

krt

---

