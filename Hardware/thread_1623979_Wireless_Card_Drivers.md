---
title: "Wireless Card Drivers"
date: 2010-11-17
forum: Hardware
---

### Post by ReeO on 2010-11-17
Hello everyone,

New to these forums and new to Ubuntu. Never touched a Linux OS before and am hoping for a smooth experience. I'm a Windows-fanatic but want something new to play with.

I decided to install Ubuntu Studio because of my multimedia needs, but unfortunately, can't get the Wi-Fi working.

Ubuntu detects my wireless card and displays it in the Network Manager. I have enabled it and entered details as required, but I can't seem to get any internet or an actual connection. Net works fine when used wired networking.

I've read around and established that it could be because I haven't installed the driver. I read around further to find out my wireless card is an Intel 3945 so I downloaded the driver from the Intel Linux site.

Problem I have now is that I have a tgz containing a ucode file, a license and a readme. None of the readme makes sense and have never heard of a ucode file before.

Could anyone point me in the right direction of getting everything set up and running? Am I on the right track? How do I use this ucode file to install the driver?

If it's any use, the card is PCI (iwpci or whatever it is :P)

Any help would be much appreciated!
ReeO

---

### Post by cchhrriiss121212 on 2010-11-17
Have you installed a network manager? I know you mention one but studio does not come with one installed. If you do you will see an indicator applet on the taskbar next to the clock.

If you still have a wired connection handy, open synaptic and install gnome-network-manager. You don't need to worry about installing any drivers from source, Ubuntu is supposed to be the opposite of that kind of approach.

---

### Post by ReeO on 2010-11-17
Oh, okay, thanks.

I was going to System -> Administration  -> Network and messing around in there.

Will check that out.

---

