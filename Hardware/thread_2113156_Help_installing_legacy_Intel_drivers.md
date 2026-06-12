---
title: "Help installing legacy Intel drivers"
date: 2013-02-06
forum: Hardware
---

### Post by patriot56 on 2013-02-06
Greetings Forum.
During a conversation in another Forum I was told that "there was a recent flurry of activity on the [Launchpad bug report]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/541492")".        

According to the information provided, Intel has finally fixed the driver for their legacy GPU  (in my case, for the **82845G/GL[Brookdale-G]/GE**) chipset.

I was told that I needed to install the xserver-xorg-video-intel-2.20.16 or newer, drivers.

As I understand, these drivers are not (at least as of the date of this post) in the Experimental repos., 

I was told that I can get the updated driver from the xorg-edgers PPA?  

When  I visited this site it all looked pretty confusing but I followed the  instructions to install the latest driver and everything seemed to go  well.

When I open a Terminal and enter the command ```
lspci -v  
``` I get the following: (*showing video output only*)
> [COLOR=RoyalBlue]00:02.0  VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE  Chipset Integrated Graphics Device (rev 01) (prog-if 00 [VGA  controller])
    Subsystem: IBM NetVista A30p
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at 88000000 (32-bit, prefetchable) [size=128M]
    Memory at 80000000 (32-bit, non-prefetchable) [size=512K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915[/COLOR]
I just don't have enough knowledge in this area to know if this is the most current driver.

I see that the Kernel driver in use is, **i915** but, because of my lack of knowledge in this area,  this output doesn't tell me anything more than I knew before.  
And isn't there a big difference between a Kernel driver and a Hardware driver?  Or are they the same thing in Linux?

**[COLOR=Red]Is there a way that I can see if the driver that the GPU is using *is* 2.20.16 or newer[/COLOR]**?

Obviously,  the easiest thing to do would be to visit Ebay and purchase a cheap  video card that will fix the problem.  Although that may be the easiest,  course of action, it isn't the cheapest when you have several of these  Intel machines that you are trying to update.  And in light of this new  information about Intel finally fixing their drivers, I have to attempt  to update the drivers first.

Thank your for your help and for your patience in this matter.
I really hope that this problem can be solved without spending any more money on these antiques.

*These computers are being prepared  for donation or to be sold at a  very low price to those that otherwise  would never own a computer due  to their financial status.*

---

### Post by MarcoDePollo on 2013-02-06
What does this command return:

```
sudo apt-cache policy xserver-xorg-video-intel
```

---

### Post by patriot56 on 2013-02-06
> **MarcoDePollo said:**
> What does this command return:

```
sudo apt-cache policy xserver-xorg-video-intel
```
Thank you for responding so quickly.

Here's the output of the command you suggested.

xserver-xorg-video-intel:
  Installed: 2:2.21.0+git20130204.9640640a-0ubuntu0ricotz~quantal
  Candidate: 2:2.21.0+git20130204.9640640a-0ubuntu0ricotz~quantal
  Version table:
 *** 2:2.21.0+git20130204.9640640a-0ubuntu0ricotz~quantal 0
        500 [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/) quantal/main i386 Packages
        100 /var/lib/dpkg/status
     2:2.20.9-0ubuntu2 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/main i386 Packages

---

### Post by patriot56 on 2013-02-06
At first glance I didn't think the drivers were up to date, but now that I look at it, it appears that they are current?

Does that look correct?

---

### Post by MarcoDePollo on 2013-02-06
> **patriot56 said:**
> At first glance I didn't think the drivers were up to date, but now that I look at it, it appears that they are current?

Does that look correct?

Yes, yes it does.

Looking at the git-string I'd say the drivers you have installed were built about two days ago.

---

### Post by patriot56 on 2013-02-06
Thank you MarcoDePollo.
Your help in this matter was greatly appreciated.

When I installed the drivers from the xorg-edgers PPA it was the first time I had tried anything like that and, well, to be honest, it was a little intimidating.  

Everything appeared to go smoothly but when you're not sure about what you are doing in the first place there is always doubt.  That's why I brought the question here.

Your suggestion to use the command that you offered was exactly what I was looking for.

It presented all of the information that I needed to identify the driver that the GPU is using.
At this point I am satisfied that the drivers are up-to-date.

So, thank you again.):P
I will mark this thread solved.

---

