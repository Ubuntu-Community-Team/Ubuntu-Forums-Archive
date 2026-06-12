---
title: "HP HDX18 - Is this laptop OK with (K)(X)Ubuntu?"
date: 2009-10-28
forum: Hardware
---

### Post by xiombarg on 2009-10-28
Hi Folks,

I've been using Ubuntu happliy on my desktop for a few years, and am about to buy my first laptop. I'm most likely going to buy online, and am trying to make sure my purchase will be OK for Ubuntu (I'll probably try Kubuntu on the machine, actually).

I currently have my sights on an HP HDX18. It features Nvidia 9600M GT, so that side of things should be fine. I'm not really sure of what else I should check, for compatibility.

Last week I was thinking of getting a Sony Vaio, though I learned a couple of things which turned me away from that option.

A Sony salesman told me Vaios are not a good option for Linux, as there are driver issues. He said there would probably be issue with the BlueRay drive, as well as the function keys, possibly couldn't use inbuilt Firewire for external drives, and maybe other issues. I don't know if all that is true or not.

I also read that Sony doesn't support the 64 bit virtualisation features of Intel's processors. I am likely going to run at least one virtual machine fairly regularly.

Anyway, the HP features look pretty good, so I'm trying to find out if there are any such issues to expect. Has anyone here used Ubuntu or other Linux variants with the HP HDX18?

I'm a bit lost with all of this. It is my first ever laptop, and I had originally expected everything would be of a similar standard to desktops.

Cheers folk. Any help would be much appreciated!

Xiombarg

---

### Post by Daemonmonkey on 2009-11-16
> **xiombarg said:**
> I currently have my sights on an HP HDX18. It features Nvidia 9600M GT, so that side of things should be fine. I'm not really sure of what else I should check, for compatibility.


I've installed Ubuntu under both WUBI and WMWare Player. Until now almost everything has worked pretty flawless, but I must say I haven't tried out special hardware as the card reader or the TV-tuner.

> I also read that Sony doesn't support the 64 bit virtualisation features of Intel's processors. I am likely going to run at least one virtual machine fairly regularly.


I have read that on a multiple-core machine you can use core dedication so that each VM uses its own core.

Haven't tried it yet though.

One problem is that most laptops processors don't support 64-bit virtualisation features so 64-bit OS in VM's doesn't work. But a real installation works, as with WUBI.

> Anyway, the HP features look pretty good, so I'm trying to find out if there are any such issues to expect. Has anyone here used Ubuntu or other Linux variants with the HP HDX18?

I'm running Mandriva Linux as a virtual machine andhave even tried to run both installations parallel side by side with no side effects yet.

> I'm a bit lost with all of this. It is my first ever laptop, and I had originally expected everything would be of a similar standard to desktops.

Cheers folk. Any help would be much appreciated!

Xiombarg

Laptops are very special and they mostly aim towards mobility, therefore they differ quite a bit from desktops. the HDX has surprised me by being quite power-user friendly, and with it's dual HD with a total of 1TB (as in mine) you can afford to have several OS installed at a time and still have plenty of space...

Nevertheless the HDX has the disadvantages of all lappies the non-virtualisation of 64-bit being one of them. Also the problem of special hardware is always present, but the community has succeeded to make it work quite beautiful with this machine. Unfortunately HP doesn't have drivers in their site, at least not what I've seen yet.

I say go for it, if you don't have issues with battery life then it's a good PC and you get a lot for the money.

Hope this helped (but please don't kill me if you feel tricked :D )

/DM

---

### Post by Trebaruna on 2009-11-16
> **xiombarg said:**
> 
I also read that Sony doesn't support the 64 bit virtualisation features of Intel's processors. I am likely going to run at least one virtual machine fairly regularly.
On this part at least I can comment.
There are two different things here: 64-bit support and virtualization support. Unfortunately I do not know whether Sony screws those up (ask the salesperson, send Support an email, use a search engine...) but you do not strictly need the virtualization support to use virtualization. You'll suffer a larger performance penalty (I don't know any numbers so no idea how much you should care) but it should run, depending on the software. Virtualbox will work, KVM not (?).

If you have access to a display model: check the Computer page in Windows: if it says it's running a 64 bit edition then you know that it at least supports that. Perhaps there's an easier way to check, too.

EDIT: Also, for virtualization you need to have the right processor. Intel likes to disable certain features on lower end models. Intels website and Wikipedia should help you figure out whether the CPU model your candidate comes with has the right support. AMD pretty much enables all features across the board I think, but don't quote me on that.

---

