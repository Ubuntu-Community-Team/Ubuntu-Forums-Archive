---
title: "kvm switch madness"
date: 2005-07-14
forum: Hardware &amp; Laptops
---

### Post by zue on 2005-07-14
So I once again showed how green I am at this Linux stuff by buying yet another piece of hardware without checking if there were any known problems with it in Linux.  And of course there are, that's Murphy's law.  The hardware I'm reffering to is a two port kvm switch.  The monitor and keyboard work just fine, but the ps2 mouse jumps around all over the place, opening and closing programs and moving the panel around as it goes.  Sometimes it stops on its own, and sometimes I have to do ctr-alt-backspace (that's all I know to do to stop it) because it's gone and opened like 100 instances of firefox or something.  It doesn't do it constantly, but it does it ofen enough to make the system pretty much unusable.  It especially likes to do it right after I start a program (any program will do).  I've read in some old threads that some people had this problem with Warty, but only immediately after switching from one computer to the other with the kvm.  Mine seems to do it whenever it wants.  And it's definitelly getting worse the longer I go without restarting.  I've tried the following to fix the problem:

I edited the /etc/modules file like so:

```
ide-cd
ide-disk
ide-generic
lp
mousedev
**psmouse proto=exps**
rtc
sbp2
sr_mod
```

and like this:

```
ide-cd
ide-disk
ide-generic
lp
mousedev
**psmouse proto=bare**
rtc
sbp2
sr_mod
```

I read in other places that these things fixed similar problems for others.  However, for me the first thing actually seemed to make it worse and the second change didn't help much either.  It may have made the problem milder but that's probably my imagination.  I also read that I could try unloading and reloading my mouse driver module, but I compiled the mouse drivers into the kernel (I'm a newbie and I wasn't sure I'd be able to load them as a module when I compiled my kernel).  Could that also be why the above fixes didn't work for me?  Is there anything else I can try to get this working or should I totally give up on the whole 2 computers, 1 monitor, mouse and keyboard thing?

---

### Post by Bob D. on 2005-07-14
I'll assume that this issue doesn't show up when this PS2 mouse is hooked up directly to one computer without the KVM? So we can safely assume something with the KVM is the problem then?

The reason I ask is I used a 2-port KVM in Ubuntu and now Kubuntu without any issues. I recall having the exact same problem you describe when I was using Fedora Core 3 with my KVM. My recollection is that the "fix" involved slowing down the mouse pointer acceleration. I must admit I cannot find that I keep any notes on this and my searching of my posts on FedoraForums and UbuntuForums didn't turn anything up.

All I can suggest is trying to slow down the poiter acceleration and see if that helps. Its been too long, too many other problems have come and gone to remember.

Good luck!

Bob

---

### Post by zue on 2005-07-14
[QUOTE=Bob D.]I'll assume that this issue doesn't show up when this PS2 mouse is hooked up directly to one computer without the KVM? So we can safely assume something with the KVM is the problem then?[/QUOTE]

No, it doesn't happen when the mouse is directly hooked to one computer.  I ended up having to do that, the problem was getting too frustrating.  What's worse, this particular kvm doesn't alow me to just use the monitor and keyboard switching feature (and use 2 mice as they don't take up so much room.)  The way it's wired requires all three things to be plugged through the kvm.  Argh.

[QUOTE=Bob D.]All I can suggest is trying to slow down the poiter acceleration and see if that helps.[/QUOTE]

Ok.  I'll try to find out how that's done.  

[QUOTE=Bob D.] too many other problems have come and gone to remember.[/QUOTE]

Speaking as a Linux newbie, that's not all that encouraging.   ;-) 
Thanks though. 
Zue

---

### Post by steevc on 2005-07-14
I had the same problem with my KVM. I thought it was the wireless mouse I was using, but it now seems it was the switch. Luckily mine would let you use it without plugging in a mouse, so I did that directly to the PC. As of now I am not using the KVM anyway.

I suspect that it's a hardware problem in the KVM and so any changes on the PC will not help much, but I may be wrong.

This is the model I was using [KVM](http://www.ebuyer.com/customer/products/index.html?action=c2hvd19wcm9kdWN0X292ZXJ2aWV3&product_uid=46424)

-- 
Steve
[www.bagofspoons.net](http://www.bagofspoons.net)

---

### Post by springshades on 2005-07-14
I also have a very similar problem using my KVM and Mandrake Linux. The KVM switch claimed to work with linux, but it still has this bug. With mine, it is a random bug that doesnt happen everytime, maybe 50% of the times I start up the computer. Once the computer is started I can flip back and forth with no problems. I'm able to fix it when it occurs by simply unplugging the mouse from the switch and plugging it back in again. Not sure if that would help you at all.

---

### Post by zue on 2005-07-14
[QUOTE=springshades]I'm able to fix it when it occurs by simply unplugging the mouse from the switch and plugging it back in again. Not sure if that would help you at all.[/QUOTE]


Oddly enough, it doens't fix it.  After I've gone long enough without restarting, it starts doing it almost constantly, probably once a minute or more, so even when I unplug it, and plug it back in, I'm only good for a few seconds.  Argh, this bites.   ](*,)

---

### Post by zue on 2005-07-14
[QUOTE=steevc]
I suspect that it's a hardware problem in the KVM and so any changes on the PC will not help much, but I may be wrong.
[/QUOTE]

I dunno.  If it's a hardware thing then it doesn't show up in Windoze.  I've read in a few different threads that it's a linux kernel thing, but the fixes that seemed to work for some other people didn't work for me.   :? 

I should probably include the model of my switch.  Here it is:
[http://www.geeks.com/details.asp?invtid=MPC-2000&cat=CBL](http://www.geeks.com/details.asp?invtid=MPC-2000&cat=CBL)

---

