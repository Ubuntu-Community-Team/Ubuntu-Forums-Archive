---
title: "been trying for months to get video card to work"
date: 2009-04-19
forum: Hardware
---

### Post by Slenkar on 2009-04-19
I have a intel 945 graphics card

Ive tried reconfiguring the xorg xserver pacakge but it only gives options to configure my keyboard even with the -phigh argument
 Ive also tried manually changing xorg to 'intel' and 'i810' and ive also installed every intel driver i know of: 'mesa' and the one from the intel website wouldnt install

---

### Post by DJonsson2008 on 2009-04-19
I've been struggling with getting my xubuntu/ubuntu to work with my nvidia. i picked up an old 10$ 40 gig at the flea market just to 
make a test. 

A clean install of 8.10 recognized the card right away, with
the default restricted drivers and enabled me to configure it.

It really seems there is a breaking point with driver installs
on Ubuntu, with some hardware at which point in time a fresh
reinstall may be the fastest and best fix.

I wish I understood how modules and kernels work better as the
secret is I suspect in debris left by subsequent installs of
drivers. Whatever the case you might consider a re-install 
as it is could be more effective and faster than attempting for
hours to determine what the previous installs of drivers have
done to the machine that are disabling the capacity to get 
new or even old drivers to work.

You should get a second opinion, I'm not an expert but this is
what I'm experiencing.

---

### Post by Slenkar on 2009-04-20
thanks for the info

---

### Post by Slenkar on 2009-04-21
reinstalling 8.04 fixed it thanks!

---

