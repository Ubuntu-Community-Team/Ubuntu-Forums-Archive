---
title: "3 Problems on upgraded 9.04 (Jaunty)."
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by LeviNelson on 2009-04-25
Hi, thanks for taking the time. 

I have three problems that cropped up after I upgraded (one might have been happening before/have nothing to do with, the upgrade). I have tried to make this brisk as possible. I would rank my knowledge of *nix in the moderate range, but I am having no luck with figuring this out. You guys/girls have always been so helpful in the past, I thought I would give it a go again.

Computer is a Dell Dimension E310 Tower with onboard videocard, and a P4 processor.

Alright then.

_**Problem 1**_

The most troublesome one, when trying to boot up Ubuntu, the display does not, well work (I have Ubuntu set to auto-login).

After the scrolling "starting up" screen disappears, I am greeted with this on my monitor.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=111077&stc=1&d=1240712573[/IMG]

I cannot CTRL+ALT F1 or F2 to switch to a different display, but I can SSH into my machine just fine. 

**_Problem 2_**

When attempting to start up 'hellahella' I discovered something was off with my Python, and since I know NOTHING of the inner workings of Python I have no idea what this error message is trying to tell me.

When I try and run 'paster serve hella.ini' (to start up hellahella) I get this error:

> Traceback (most recent call last):
  File "/usr/bin/paster", line 5, in <module>
    from pkg_resources import load_entry_point
  File "/usr/lib/python2.6/dist-packages/pkg_resources.py", line 2562, in <module>
    working_set.require(__requires__)
  File "/usr/lib/python2.6/dist-packages/pkg_resources.py", line 626, in require
    needed = self.resolve(parse_requirements(requirements))
  File "/usr/lib/python2.6/dist-packages/pkg_resources.py", line 524, in resolve
    raise DistributionNotFound(req)  # XXX put more info here
pkg_resources.DistributionNotFound: PasteScript==1.7.3

Any ideas?

**_Problem 3_**

The weirdest and least likely to have anything to do with the upgrade. 

Simply; when my Ubuntu machine is plugged into the router, nothing on my network can get out to the internet. Local connections between computers work fine. Sometimes it takes a few hours of the Ubuntu machine being hooked to the network to take it out, but it always does.

I am pretty sure this is some kind of hardware problem (and am looking into replacing NIC cards and routers, etc.). Just thought I would mention it here to see if anyone has heard of this kind of thing, and/or has any idea how to fix it.

---

### Post by cariboo on 2009-04-25
> 
When attempting to start up 'hellahella' I discovered something was off with my Python, and since I know NOTHING of the inner workings of Python I have no idea what this error message is trying to tell me.

When I try and run 'paster serve hella.ini' (to start up hellahella) I get this error:

Is it compatible with python 2.6, as that is the version Juanty is using.

> The weirdest and least likely to have anything to do with the upgrade.

Simply; when my Ubuntu machine is plugged into the router, nothing on my network can get out to the internet. Local connections between computers work fine. Sometimes it takes a few hours of the Ubuntu machine being hooked to the network to take it out, but it always does.

I am pretty sure this is some kind of hardware problem (and am looking into replacing NIC cards and routers, etc.). Just thought I would mention it here to see if anyone has heard of this kind of thing, and/or has any idea how to fix it.

It sounds like a dns problem, check /etc/reslov.conf and make sure it matches the dns nameserver addresses that your isp provides. If that doesn't work, try [Opendns]("http:///www.opendns.com/start/")

For the video problem start in recovery mode and at the menu  select drop to root prompt. then type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Wiebelhaus on 2009-04-25
Sorry if I sound like captain obvious , but has anyone ever had a upgraded OS of any kind (windows , Linux , Mac , BSD , DOS , Freedos) actually work without issues?

That one guy will say yes , but for real....

Install clean buddy , you know you should have listened to that little clean install voice.

Cheers.

---

### Post by LeviNelson on 2009-04-25
cariboo907,

About the hellahella, you are probably right, it seems to need version 2.5.

The DNS in resolv.conf was set to my local router, and generally seemed to work, but I changed it to OpenDNS to make sure, so far the internet is still working.

Unfortunately the 'sudo dpkg-reconfigure -phigh xserver-xorg' did not alleviate the problem, as I am getting the same screen (although I noticed that it blinks on and off a few times, then just stays solid).

Perhaps as sx66gns said, I need to listen to the voice telling me to do the fresh install?

Thanks for your quick responses.

---

### Post by jrifkin on 2009-05-09
I solved Problem 2 on my machine by doing the following

1)  Removed the existing script /usr/bin/paster

2)  Used Synaptic to install python-pastescript.


The version of /usr/bin/paster that I had did not belong to a Ubuntu package, but was install manaully.

The new Ubuntu pacakge python-pastscript includes a new version of paster
which ran correctly (the package also installs with a long list of other
needed packages).

Hope that works for you.

---

