---
title: "Install 8.04 without cd no usb have network"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by gpgp on 2009-05-07
I broke my 8.04 install trying to upgrade to 8.10. the cd drive has had physical problems for a while and now no longer functions. I am hoping someone can help me do a network install so i dont have to put another cd drive in the machine. the bios does not allow boot from usb. although it may if i upgrade it. but i dont have another machine with a floppy drive.  I have several other machines, 2 with 8.10, an xp machine and 2 puppy linux. i think there is a way to install from the image from a networked machine but i dont know how to go about it. i can get to a root prompt and even login on alternate consoles. i haven't tried but i can probably ssh into it as well. 
I think i need  a tftp server, right ?
So i am looking for a way to do a local network install. Any suggestions greatly appreciated.
Thank you
gpgp

---

### Post by HyRax on 2009-05-07
You will need to set up a PXE boot server, but this obviously requires your desktop PC to have the PXE boot functionality on board to be able to boot from such a server in the first place.

Check the BIOS settings to see what boot options are available to you and then Google up how to build an Ubuntu PXE server.

Oh, and since you broke your install - skip over and install 9.04 instead.

---

### Post by gpgp on 2009-05-08
Thank you
I guess i had pretty much found my answer but it seems a little more complicated than, for me at least just swapping the cd drive. I found lots of stuff about network install here [https://help.ubuntu.com/community/Installation#Minimal%20installations]("https://help.ubuntu.com/community/Installation#Minimal%20installations").
it looks as though i have some pxe functionality in bios but not an explicit setting boot from pxe or anything like that i could find.
I will go the hardware solution thank you for you input though.
gpgp

---

