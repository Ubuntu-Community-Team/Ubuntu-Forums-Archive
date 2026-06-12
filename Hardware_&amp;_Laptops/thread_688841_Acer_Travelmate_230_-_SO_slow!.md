---
title: "Acer Travelmate 230 - SO slow!"
date: 2008-02-05
forum: Hardware &amp; Laptops
---

### Post by mwanstall on 2008-02-05
I've just installed Ubuntu on a stock standard Travelmate 230 (1.7ghz processor, 128mb ram) and it is impossibly slow. I was thinking that it may be a little chunky but was never expecting it to be as bad as it currently is (loading x seems to take around 1 - 2 minutes, same as loading OOo.

I suppose this old laptop would probably be more suited to Xubuntu but what is holding me back here? Would upgrading the RAM help significantly or is something wrong with the setup? I have done ZERO config so far (simply because trying to work through the GUI is soooo slow) so I'm not sure whether some xorg.conf tweaks or something similar would make the difference. Never having loaded linux on an old laptop I honestly don't know where to start (I've googled but to no avail).

Any tips? Specs of the lappy can be found here: [http://www.acersupport.com/notebook/html/tm230x_specs.html](http://www.acersupport.com/notebook/html/tm230x_specs.html)

EDIT: I also had to run an external monitor so I could actually get X to load at all so any help with the xorg.conf configuration would be tops too!

Thanks,
-Mal

---

### Post by Yellow Pasque on 2008-02-05
Xubuntu and/or more RAM would help significantly. Also, Ubuntu's 32-bit distros aren't optimized for 686 processors, but instead are meant to run on 386's. I would highly recommend Arch Linux (in addition to more RAM), because it's 686-optimized and you can choose whatever desktop you want. It may be a bit difficult to configure at first, but just follow the excellent guides/howto's/wiki and you should be okay. Arch Linux is also a great learning experience without being as time-consuming as Gentoo.

---

### Post by mwanstall on 2008-02-05
Thanks, I've downloaded the Xubuntu alternate ISO so I'll give it a whirl first and if it's still unbearable I'll give Arch Linux a go. Time restraints at the moment probably stop me from having the time to setup an Arch Linux install.

Would the tailoring to the specific architecture (686) make that much of a difference? Just wondering whether it's worth missing some sleep for the gains or whether I just try Xubuntu.

---

### Post by kerry_s on 2008-02-05
128 is nowhere near enough to run a standard install. if you can get more ram it would be better. for now you might try a custom install-> [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
or
you can try 1 of the many distro's that are made for low resource systems.
[http://damnsmalllinux.org/](http://damnsmalllinux.org/)
[http://www.puppylinux.org/user/viewpage.php?page_id=1](http://www.puppylinux.org/user/viewpage.php?page_id=1)
[http://fluxbuntu.org/js.html#](http://fluxbuntu.org/js.html#)

i'm using a 450mhz 256mb ram laptop running a debian custom install, so you should be able to do something. just a matter of how bad you want it.

---

### Post by daller on 2008-02-16
How do you even install it? With the alternate CD?

On my 230, hardy simply never reaches the GUI (nor does gutsy, for that matter!)

---

### Post by mwanstall on 2008-02-24
Oh yep, I had to install via the alternate CD. I've gone with Xubuntu though, the speed is fantastic. It's all running like a charm now (I also doubled the RAM which sure would've helped).

---

