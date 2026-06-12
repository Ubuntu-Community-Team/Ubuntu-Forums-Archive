---
title: "remote management device"
date: 2010-03-17
forum: Hardware
---

### Post by fiftyfour123 on 2010-03-17
I've been researching this for a while. I have a server at my house that I need to be able to monitor while i'm away for extended periods of time. VNC works great when the machine is working. But occasionally the server will lose internet connect or I will reboot it and it will get stuck on the boot loader screen. The perfect solution seems to be KVM over IP. However, I don't have $300 to spend. I have an old PPC Mac Mini lying around that I could use, if that could help in some way. I just want an affordable way to access the computer when it is either off, on the boot loader screen, or cannot connect to the internet.

Thanks

---

### Post by fiftyfour123 on 2010-03-19
anyone?

---

### Post by IcarusR on 2010-03-20
At least one box on your site has to have internet access to do this. 
If none has internet access it is impossible to access it remotely over internet.
KVM over IP needs internet connection.
Is it networked ? How does it connect to internet ?

> access the computer when it is either off, on the boot loader screen
You can not access any box in this state.

Maybe you should go back a stage & prevent the need to access under these conditions. 

Set bios to 'last state on power off' so it reboots on power failure.
Resolve issue of 'getting stuck' on bootloader screen.

---

