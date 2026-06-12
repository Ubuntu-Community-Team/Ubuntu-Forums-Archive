---
title: "xen and smoothwall on Ubuntu"
date: 2008-07-11
forum: General Help
---

### Post by headnoodle on 2008-07-11
I have just bought myself a small cube pc for playing around with and have set up xen succesfully.  I have been using xen-create-image to create domu machines with LVM but now want to play around with smoothwall.  I have got a VT enabled processor so I guess I wont have any probmlems if the smoothwall kernel isnt patched.

My question is how do I create a xen domu that is based on an iso so it installs as if it was a physical machine.  In Vmware workstation this is easy It presents a dummy bios and can boot from a virtual cd drive connected to the ISO, but is there a similar way to do this on ubuntu and xen.  I am using xen 3.2 btw with hardy heron.



thanks in advance for your help...

---

### Post by helisandro on 2008-11-19
Hi.

I've installed smoothwall in my PC, but I'm still having problems with network connection, it was pretty unstable.

I've tried to do it as a windows install. 

What you need to do is install xenman package that provides interface to xen and a screen for each vm, then with this screen all you have to do is follow the install steps.

If you have any doubts just ask me, my friend.


P.S. sorry about terrible english.

---

