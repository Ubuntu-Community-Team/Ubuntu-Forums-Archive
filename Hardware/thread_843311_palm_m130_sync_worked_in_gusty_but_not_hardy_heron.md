---
title: "palm m130 sync worked in gusty but not hardy heron"
date: 2008-06-28
forum: Hardware
---

### Post by donniep152 on 2008-06-28
Has anyone else experienced difficulty syncing a palm via usb on hardy heron?
I had it syncing fine with evolution on gutsy, but after a fresh install of hardy and loading the visor module, I cannot get a sync using any of the usb ports.
I've followed pretty much every "how to" I've found in these forums, but to no avail. Including these:

[https://help.ubuntu.com/community/PalmDeviceSetup](https://help.ubuntu.com/community/PalmDeviceSetup)

[https://help.ubuntu.com/community/Po...Devices/PalmOS](https://help.ubuntu.com/community/Po...Devices/PalmOS)

I've also tried jpilot and it doesn't work.

a lsusb when syncing shows my palm so I know the usb port is being seen.

Any help in this most frustrating issue would be greatly appreciated.

---

### Post by danbodoh on 2008-06-29
Did you try to

1. Get rid of visor

2. Chose 'usb:' (no quotes, but with colon) instead of /dev/pilot?

Dan Bodoh

---

### Post by donniep152 on 2008-06-30
yes, I did try it first without visor.  I tried usb:, usb0, usb1, all with no luck.  Then I loaded visor and tried again.
Right now, I'm using just my calendar and evolution on my old gutsy box while I wait to figure out why it's not working with hardy.

Thanks,

---

### Post by donniep152 on 2008-07-11
well I've discovered a couple of things that are interesting, but my non-sync in hardy still exists.
I'm no where near being anything but a newbie, but when I booted off of the gutsy live cd and installed palm device using usb:  it never found it.  when I used usb:0 it told me I needed the visor module loaded.  Once I did a sudo modprobe visor, synced using usb:0, it worked flawlessly and instantly.

Then I booted the hardy heron live cd.  went to install palm, using usb: and it never found it.  Tried usb:any with no luck.  tried usb:0 and was told I needed to load the visor module.  did sudo modprobe visor, tried again using usb:0 (which worked in gutsy) no luck.  didn't work with usb:, usb:0, usb:1 or dev pilot either with or without the visor module loaded.

I can't believe I'm the only one having this issue.

Anyone with any help would be greatly appreciated.

Thanks in advance.

---

### Post by Paddy Landau on 2008-07-16
> **donniep152 said:**
> I can't believe I'm the only one having this issue.
There are many posts from people having problems. I'm completely unable to sync, too.

Here are two links that I found, which seemed to work for some people but (sadly) not for me:

[How to link USB and Linux to your Palm]("http://www.pilot-link.org/README.usb")
[USB Cradle not syncing to computer [Archive] - Ubuntu Forums]("http://ubuntuforums.org/archive/index.php/t-351029.html")

Perhaps you can find something.

---

### Post by donniep152 on 2008-07-16
Appreciate the thought, but both of those posts pertained to a gutsy distro.  My palm syncs fine with gutsy but not hardy heron.  I found one post in another forum that claims it's a kernel issue so I guess I'll wait till a kernel upgrade and try anew.

thanks,

---

### Post by Paddy Landau on 2008-07-17
Thanks for that new info.

New kernel, then, perhaps!

What puzzles me is that some people have got it working on Hardy.

---

### Post by DJ_Peng on 2008-07-18
I'm actually having intermittent issues with syncing in Hardy but it turns out to be a connection issue with my dropped-too-many-times PDA. I'm getting a new(-er one for me) any day now and hopefully the new cradle will get rid of the issues I'm having with my PEG-SJ20. My new one is a T615 and has an actual cradle rather than just a cable that plugs into the bottom so I'm expecting it to work better for me.

I did look at the Gutsy posts while I was fighting with syncing mine and all of the info for Gutsy  translates easily to Hardy, in fact now I can sync much more reliably when I get visual confirmation on my SJ20 that it's plugged in correctly.

---

