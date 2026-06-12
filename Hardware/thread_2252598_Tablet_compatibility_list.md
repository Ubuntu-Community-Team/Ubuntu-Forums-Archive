---
title: "Tablet compatibility list"
date: 2014-11-13
forum: Hardware
---

### Post by opensas on 2014-11-13
I was wondering if there's an intel tablet compatibility list for Ubuntu (not Ubuntu touch, but the plain ubuntu for desktops)

I'm looking for a 10" intel tablet to use with linux, adding a keyboard. I saw several tablets but all of them seem to have some trouble installing and/or running ubuntu.

Microsoft surface seems to work rather ok 
[http://www.reddit.com/r/SurfaceLinux/comments/2b1hf6/running_ubuntu_1404_on_surface_pro_1_full_time/](http://www.reddit.com/r/SurfaceLinux/comments/2b1hf6/running_ubuntu_1404_on_surface_pro_1_full_time/)
[http://www.omgubuntu.co.uk/2013/05/how-to-install-ubuntu-on-surface-pro](http://www.omgubuntu.co.uk/2013/05/how-to-install-ubuntu-on-surface-pro)
[http://ubuntuforums.org/showthread.php?t=2231207](http://ubuntuforums.org/showthread.php?t=2231207)

Asus T100 transformer seems more problematic
[http://www.jfwhome.com/2014/03/07/perfect-ubuntu-or-other-linux-on-the-asus-transformer-book-t100/](http://www.jfwhome.com/2014/03/07/perfect-ubuntu-or-other-linux-on-the-asus-transformer-book-t100/)

According to this article Acer Iconia W50 seems to work ok: [http://www.techradar.com/news/software/operating-systems/install-linux-on-your-x86-tablet-five-distros-to-choose-from-1162825](http://www.techradar.com/news/software/operating-systems/install-linux-on-your-x86-tablet-five-distros-to-choose-from-1162825)

Atom based Intel tablets seems to have some problem with 32 bits UEFI (has it been addressed by now?) 
[http://geardiary.com/2014/01/17/can-new-intel-based-tablets-run-linux/](http://geardiary.com/2014/01/17/can-new-intel-based-tablets-run-linux/)
[http://askubuntu.com/questions/392719/32-bit-uefi-boot-support](http://askubuntu.com/questions/392719/32-bit-uefi-boot-support)

Nexus 7 used to be officially supported, but seems to be discontinued: [https://wiki.ubuntu.com/Nexus7/Installation](https://wiki.ubuntu.com/Nexus7/Installation)

And someone seems to have luck with a Dell Venue 8 Pro: [http://askubuntu.com/questions/392719/32-bit-uefi-boot-support](http://askubuntu.com/questions/392719/32-bit-uefi-boot-support)

In other words, there are lots of articles an tips to make Ubuntu run on Intel tablets, but I think that a community mantained compatibility list would be very welcome.

On the other hand, I'd just like someone to recommend a troubleless intel tablet to install regular ubuntu on it.

Here's a similar question: [http://ubuntuforums.org/showthread.php?t=2230434](http://ubuntuforums.org/showthread.php?t=2230434)

Another similar question: [http://askubuntu.com/questions/163755/what-are-some-tablets-that-can-run-ubuntu](http://askubuntu.com/questions/163755/what-are-some-tablets-that-can-run-ubuntu)

---

### Post by TheFu on 2014-11-13
I have a 10" android tablet and tried to get any Linux working on it.  Got an Ubuntu working inside a chroot with a USB keyboard, however, the keymap was totally screwed, it was accessed thru VNC, so it was even slower than normal. Took this setup on a 2 week trip overseas - nothing tests a solution like travel.  About 75% of the location I couldn't get the networking working because hotels were blocking ssh and openvpn back to my home network.  I didn't have access to normal networking tools - that was partially my fault for not pre-loading them.

So ... I acquired a used Asus Eee netbook - with a crappy CPU, 2G of RAM (soldered in), 500G HDD and terrible resolution and just a few hours of battery. Ran Ubuntu on it for 2 yrs before the performance drove me nuts.  Last Feb, picked up an 11" chromebook Acer C720 - and loaded Ubuntu on it.  8 hrs of battery is awesome, fast GPU, fast CPU, 2G of RAM soldered in, $200. There is much to like and much to dislike in the chromebook line. Do some research.  I wish that I'd bought a $280 Dell 11inch notebook, I really do.  Full keyboard, 500G HDD, same CPU, RAM that can be upgraded, 8+ hrs of battery.  With the C720, I had to spend $130 to upgrade stuff and get attachments to make it useful - but that doesn't correct the terrible keyboard which misses a DEL, PgUp, PgDn, Home, End keys and puts the power button where the DEL key should be. I still hit the power button thinking it is a DEL occasionally.

So ... as much as you want a tablet, there are many issues with those still - you'll pay $600+ to get one that doesn't suck. Better to just get a $300 Dell 11inch notebook, IMHO.  BTW, I've used Toshiba, Panasonic, Dell, HP, Compaq, SONY, IBM and a few other vendors over the years. They all suck in different ways. The price/performance/weight/options for me goes to the cheap Dells. If I need something fast, I can remote into a a core i7 desktop over the internet. A cheap netbook is just a display device for email, surfing, watching videos and giving presentations, it is not a powerful workhorse for CAD, FE or CFD programs.

I hope things have changed and I'm wrong. Just wanted to share the limitations of my attempts at solving the same issue as you.

---

### Post by opensas on 2014-11-13
Thanks a los for your reply, I have a dell xps 13inch and it works marvellously well, but I want something smaller (and cheaper) to carry around. I was thinking to use sublime to develop web sites with js and node.js. It' s a pretty lightweight stack. I was thinking about installing elementary or crunchbang, and ideally I would like a tablet that I could attach a keyboard to it. Do you have any experience with any Inter tablet? I heard the surface series work pretty well. 
On the other hand, I'd like to stay away from arm arch, sometimes I use binary programas (node, for example, ans sublime too) and I'm not pretty sure how well they are supported for the arm cpus.

---

