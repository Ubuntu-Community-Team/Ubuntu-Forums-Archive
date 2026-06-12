---
title: "Xubuntu 12.04 - Nvidia 96 drivers not installing"
date: 2012-05-02
forum: Hardware
---

### Post by Mr A on 2012-05-02
Hello, I hope to keep this issue as short as possible.

I did a clean install of Xubuntu 12.04 over a previous 11.10 install. 

With 11.10 I was easily able to install propriety drivers for my older Nvidia card with the "additional drivers" tool. In 11.10 it was automatically detected. This is not the case with 12.04 however. 12.04 does not detect anything. I then tried to install the propriety nvidia 96 driver with the software manager but I keep getting this error message:

[I][B]Package dependencies could not be resolved

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.[/B][/I]



It then lists older dependencies from 11.10 in the error message.

I then tried it with Synaptic package manager with similar results.

From what I can tell it seems to need dependencies that are no longer available in 12.04. Does this mean I have to wait for an update until this is resolved or or is a workaround required? It's important for me to have the propriety drivers. The first couple of updates have not solved the issue. The software manager states that this driver is supported by Ubuntu until 2013.

---

### Post by MoebusNet on 2012-05-03
Just in case you haven't found this:

Originally Posted by searchfgold6789
> The news is, apparently nVidia needs to update their driver so that it works with the latest release of the X.org window system.

[http://ubuntuforums.org/showthread.php?p=11891185](http://ubuntuforums.org/showthread.php?p=11891185)

Post #24 by zecoyote007 details his solution.

---

