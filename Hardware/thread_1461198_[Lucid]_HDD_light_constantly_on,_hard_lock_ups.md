---
title: "[Lucid] HDD light constantly on, hard lock ups"
date: 2010-04-23
forum: Hardware
---

### Post by humphreybc on 2010-04-23
Hi guys,

Here's the story. I've been running Lucid since late alphas on my Toshiba A200 Satellite. It's been going fine.

Yesterday, I installed [Granola.]("http://www.omgubuntu.co.uk/2010/04/save-power-save-money-save-planet.html")

Last night, I was using my Laptop in bed, and, as usual it got pretty hot. I know I shouldn't be using it in bed but I just had to watch one last episode of Firefly!

So that was alright. Then, my laptop started behaving strange and locked up when I tried to make Firefly fullscreen in VLC as well as the HDD activity light being on all the time. Fullscreen usually works perfectly. I am aware of [this bug]("https://bugs.edge.launchpad.net/ubuntu/+source/xorg-server/+bug/565981") and thought all my RAM might have run out.

So, I had to hard-reset the computer by holding down power. I booted back up again, found the same issues. HDD activity light was constantly on, this time Ubuntu locked up about 10 seconds after I logged in. I rebooted again, same thing. I thought it may have been something to do with the heat, so I placed it on my desk, opened a window to let some fresh air in and left it on overnight to see if the HDD light was off in the morning.

10 hours later and I notice the HDD light is normal (activity once every few seconds) but the computer was locked up. Reboot, locks up again, HDD activity light comes on again.

So, by this time I booted off a Karmic LiveCD and ran some file system checks on the drives, reported it to be fine. Palimpset also said the drives were healthy. And here I am.

What gives? I'm thinking I'll take the laptop to bits and clean out some dust, check the cabling. Then if that doesn't work, I'll download the latest Lucid RC and re-install it on my / partition (I've got a separate home partition). If I *still* have problems I guess one the hard drives is failing, and I'll have to buy a new one.

Thoughts?

---

### Post by Ayuthia on 2010-04-23
Have you looked at /var/log/messages to see if anything shows up in there?

---

### Post by humphreybc on 2010-04-24
> **Ayuthia said:**
> Have you looked at /var/log/messages to see if anything shows up in there?

Nope, but I fixed it. Pulled the laptop apart, removed a lot of dust that probably wasn't helping. Then I purged the xorg-edgers PPA, ran update and upgrade and then found that the ubuntuone daemon was using the hard drive all the time, so I just removed Ubuntu One because I don't use it.

Problem solved!

---

