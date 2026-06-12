---
title: "Firewire raw1394 problems/plugreport shows no nodes"
date: 2007-05-23
forum: Hardware &amp; Laptops
---

### Post by LeftShift on 2007-05-23
Hi.

I'm somewhat new to linux. I've been having trouble getting a response from my PCI firewire card.

The full story goes...
I had sucessfully set up a MythTv configuration on my old junker computer, using firewire to communicate with the set top box. 

Recently a friend of mine offered up their old computer for use. Seeing as how it was a good deal newer and faster I decided to scrap the old one. I set up a brand new Ubuntu install on this new donor machine. However I transfered my old firewire card to the new motherboard.

I downloaded the nesseary packages and ran plugreport to see if I could get a connect to the set top box, but I recieved the "cannot create raw1394 handle" error message, which is very well documented and tried the appropriate fixes. 

When I type

# sudo modprobe raw1394

The node gets created but when I run plugreport again. Plugreport shows host controller 0 with no nodes. (looks something like this)

Host Adapter 0
=========

I don't really know what to make of that. This is all very strange to me considering this same card worked on a different motherboard.


Any help would certainly be appreciated. I'd really rather not have to set up my old box again, it barely did the job.

-Jonathan

---

### Post by newlinux on 2007-05-23
just a shot in the dark (as I go a different error than you once, but this did solve my problem)

try 

```

sudo chmod a+rw /dev/raw1394

```
Don't think it will work, but it's worth a try.

---

### Post by LeftShift on 2007-05-23
I just gave it a shot. Changing permissions on the device doesn't seem to remedy the poblem. Plugreport shows the same thing, a host adapter with 0 nodes.

Thanks, Jonathan

---

### Post by mozetti on 2007-05-23
I also had trouble with getting my firewire card to work correctly with my dv video camera. Try searching for "firewire dv" -- there should be about a dozen threads that show up with a few different solutions in them. Basically, there's a bug in how Ubuntu (or the Linux kernel, i forget) is handling the raw1394 permissions and that causes problems with accessing devices connected to firewire ports.

I'm at work and can't do the leg work for you, but hope this helps.

---

### Post by LeftShift on 2007-06-05
Problem Solved.

Tried all the usual fixes. but as it turns out, there appears to have been some sort of IRQ conflict with my Radeon 9800 graphics card. Swtiching from the default vesa driver to the fglrx one seems to have fixed the conflict. Both nodes of the firewire card now show up in plugreport. 

However, this card continues to cause bizzare errors and conflicts in other parts of the system:
1.) Problems issuing proper screen refreshes over a VNC connection and 
2.) Ubuntu wont resume from a hibernate or suspend now. I've tried a few of the recommended fixes, but none have worked.

While there seem to be hacks and fixes for each of these problems, this card is just way too buggy for me to continue using. I've got a spare card laying around, I'm ready to just swap it in.

---

