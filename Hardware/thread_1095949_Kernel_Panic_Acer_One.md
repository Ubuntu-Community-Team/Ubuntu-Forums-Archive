---
title: "Kernel Panic Acer One"
date: 2009-03-14
forum: Hardware
---

### Post by *oPI* on 2009-03-14
Hi guys,

I ran into a really odd problem concerning Ubuntu 8.10 with the kernel 2.6.27-7 and the Acer Aspire One 150.
I bought a Ubuntu USB-stick from the web and installed Ubuntu from it. The Live-Cd (or USB) and installation went just fine.
Then I tried to start Ubuntu and it said:

Kernel Panic: unable to mount root on fs on unknown block (3,2)

I don't know how to solve this and I looked into several forums but there was never the same problem described like mine.
I didn't make the partions myself, btw. I used the "guided partion manager".

I think it has something to do with the kernel and/or my Acer Aspire One Netbook but I'm new to Linux and therefore any help would be appreciated.
Thank you

---

### Post by drlmg on 2009-03-14
I have had the same problem.... many times over the last few months. What caused my Aspire One to crash is the kernel update. Did the install work until you updated? If so then I would bet the kernel update did it.....There are many solutions in the forums and some work some don't. I about drove myself insane trying to recover my OS. If it is a fresh install I would definitely recommend a fresh install. Totally remove everything on the linux partition. Re-install but DO NOT update. Go to this site and there is a very easy solution for many problems. The fix is in a *.deb package, install the package and then you can update your system. I am not sure if you can update the kernel or not after this, I am still afraid to. I had my AAO crashed by the kernel update months ago. I recently updated it thinking that it would certainly be fixed by now, but NO it wasn't and it crashed my OS again. I was reading somewhere that a new kernel update is supposed to work but someone testing it said that it still did not.

[http://aspireonekernel.com/](http://aspireonekernel.com/)

The packages to stay away from.... rather, the ones I skipped and my system keeps working until I update to one of these.

linux-image-*******
linux-restricted-modules-***** (I think last time I was able to update these with no problem but I am not taking any chances)
linux-modules-******
linux-headers-******

Basically anything to do with updating the kernel. 


I fixed my wireless and a lot of other problems in seconds instead of hours by installing the first two packages from the above site.

I don't know how familiar you are with linux but in case you don't know, to install a *.deb package just download it and double click on it. The package installer will open up and install it for you.

I hope this helps.

---

### Post by *oPI* on 2009-03-15
Hi

Ok, first off, thank you for your reply! =D>

Well, the main problem is that i don't even have the change to start ubuntu. The installation went all smooth but after i tried to actually boot ubuntu it say "kernel panic...." and then i shuts down. 
I have a usb stick with the 'not working' kernel on it and my Internet connection is too slow to download the hole .iso Ubuntu image again and again, therefore i bought the usb-stick with ubuntu on it. But the kernel isn't working.
So my question now is, can you "update" or change the kernel on a .iso image or usb-stick? The live 'mode' is working fine and therefore i wonder if it's possible.

Thanks in advance!

---

### Post by *oPI* on 2009-03-17
Hi!

Thank you for you reply! I fixed it myself now but you lead me the right way! Thank you! :popcorn:

---

