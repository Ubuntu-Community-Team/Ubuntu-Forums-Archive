---
title: "Getting an Opteron Kernel to work..."
date: 2005-11-07
forum: General Help
---

### Post by BIGtrouble77 on 2005-11-07
I'm having a heck of a time getting my dual opteron machine up and running.  None of the default smp Ubuntu kernels work, nor do Fedora's or SuSe's.

I most recently compiled the 2.6.14 kernal and get a panic when it tries to load.  This is basically what happens with every smp enabled kernel that i've tried so far... Except for the default Debian kernel.  That one seems to work.  

So my question is... How can I get the config file for the debian kernel without reinstalling debian?  I think it's simply a setting that's causing the panics.  The only way I know to get the config file is to be actually running that kernel and do a "sudo cp /boot/config-2.6.8-14-amd64 .config".  The deb for this kernel, i found, is not compatible with ubuntu.  I'm afraid if I try and compile the source for this kernel it won't work because I'll have to use the config file from the kernel that's screwing up.  

Also, if anyone know's what the setting is that's causing the kernel panic, that would be most helpful.  I hope I made sense.  I'm very new to all of this, but i'm making progress I think. :rolleyes: 

-BT

---

