---
title: "mce remote not working after harware upgrade"
date: 2015-11-29
forum: Hardware
---

### Post by sailingboyLLB on 2015-11-29
i have a mce usb remote that has been working wonderfully for about 5   years, but can't get it to work on a new system.  i just built a new   computer with a B150 motherboard and i3-6100.  i installed ubuntu 15.10,   installed lirc, selected the correct conf.  irw shows nothing.    ir-keytable shows some intermittent and random and wrong data, it   doesn't respond to every press and multiple presses of the same key may   result in different codes and different keys may have the same code as   another button did previously. irrecord acts similarly to ir-keytable.   i  compared conf files and what not with the old system they were all  the  same, unmodified default for mce.  the old system had a older  version of  linux mint on it so i wondered if lirc got changed or broken  in newer  updates.  i took the 15.10 iso and loaded it onto a thumb  drive, booted  the live usb on the old computer, installed lirc,  selected correct conf,  ran irw and it worked instantly and correctly.   on the new system, usb  seems to be working fine, mouse, keyboard, and a  thumb drive were used  for the os install.

so it seems:
remote is working
ubuntu 15.10 should work with remote easily
maybe some specific hardware interaction with new system or other config issue?
something to do with usb 2.0 device and skylake xHCI vs EHCI[IMG]http://forum.kodi.tv/images/smilies/question.png[/IMG]

help is appreciated, this is driving me crazy and i'm at my limit of understanding on the topic.

thanks.

---

### Post by TheFu on 2015-11-29
rc6 remote support is built into the kernel now. No need for lirc anymore.

My RC6 remote is not connected to an Ubuntu system, so I can't really comment, but with the Debian 4.2.x kernel (damn systemd), I had to manually wait 30 seconds for things to finish starting, then set a parameter in /sys/ to stop double-click for every button. .... 

BTW, for media PCs, staying LTS is important to me.  Don't want to be in the doghouse over a non-working player here.

Skylake?  New CPU with new support chips?  Could be anything.

That setting ... 

inside the /etc/rc.local:
```
#  disable kernel remote 
sleep 30
echo none +lirc > /sys/class/rc/rc0/protocols
```
Sleeping 15 seconds wasn't enough time. I hate systemd!

---

### Post by sailingboyLLB on 2015-12-01
thanks for the reply.  

from what i understand lirc is the only way to allow multiple programs to listen for remote events at the same time through a socket.  for me that means using the remote for kodi and then having a red button kill switch with irexec waiting to restart kodi if it freezes, or a another button if the ubuntu desktop crashes....

honestly though, at this point, i'd settle for working at all by any method....

[http://www.lirc.org/html/configuration-guide.html](http://www.lirc.org/html/configuration-guide.html)

i think it's an issue with something in the kernel, maybe the driver is busted, maybe it chose the wrong driver?  with lirc not installed ir-keytable doesn't work properly, and that's listening for the /dev/input/eventX.  also without either lirc or ir-keytable installed none of the buttons have any effect on the current program or desktop, like i thought it should with built in kernel support.

i agree with your LTS comment, but i'm in a bit of a bind.  i started with the latest LTS of mint, but that didn't have graphics support for my skylake chip, i moved to the 4.2 kernel, but realized i had more work to upgrade the entire graphics stack, particularly when intel's manual installer didn't support that edition.  so i decided to take the most current ubuntu, which still requires editing the startup options with i915.preliminary _hw_support=1.  i'll move to the 16.04 LTS (or more likely the mint equivalent) in july or so.

so what was happening in your case?  you were not using lirc, but were getting 2 key presses because the kernel had loaded the remote twice?  what does that command actually do?

---

### Post by TheFu on 2015-12-01
Don't run any "desktop" on the kodi machine here. If kodi dies, it restarts automatically. Since we don't run a desktop, mint wouldn't make any sense.  Watching normal TV records and h.264 media then Kodi is fairly stable.  It does lock up over flv stuff and can't handle vp8/vp9/webm at all.  xvid/avi is fine, if just played, don't ffwd or skip.  I have a script that will kill kodi. If kodi is locked up, can't send any remote events, so connecting to the box with a script that is on other machines here to kill kodi is needed.  No need to power off the machine if just kodi is locked up.  Saving that 10 sec startup makes it tolerable.  Kodi from June'15 was great.  Stable, solid, worked. Think that used the 3.18 kernel.  Then they pushed out a new version based on 4.2 and while some things are easier/better, the stability isn't the same.  

Should mention, my kodi box is a Raspberry Pi v2 and really runs a distro called "osmc" which is a minimal debian.  Also run Kodi on an intel ubuntu-server machine a few times weekly and even on Windows perhaps once a month. Because it sucks up my 2nd monitor (controlled by a KVM switch) sometimes using ubuntu and other times using Windows is easier.

lircd is run automatically ... handled by systemd ... I didn't need to do anything special except select the correct RC6 config file (already existed), and edit the skip-forward/back settings they screwed with in July to get the best settings to watch some football games.
In /etc/lirc - just pointed the lircd.conf at /etc/lirc/rc6-mce-lircd.conf - that was it.

I'd post my 'kodi-kill' script, but that netbook is in pieces awaiting a new keyboard (that wasn't just a trivial keyboard swap).  Some of these cheap/thin netbooks have keyboards that need a dremel and drill to replace. ;(
kodi-kill:
```
#!/bin/sh
sudo killall -s 9  kodi.bin

```
From any remote box, just run **ssh osmc bin/kodi-kill** and that will restart kodi.  osmc is the R-pi hostname/IP.

Can't imagine using a powerful computer just for a playback device.  The Plex server here only has a [$65 CPU]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819117374") and can transcode 2 1080p streams concurrently for the Pi and a chromecast without skipping anything.  For playback, a fanless device is required here. The "WAF" wouldn't allow anything else.

What was happening here?  Pressing a remote button caused kodi to see 2 of the same button presses.  That setting forces it to send 1 press for each button toggled. Basically, the remote works like it did with the 3.x kernels, as expected.

---

### Post by sailingboyLLB on 2015-12-01
i do other things besides kodi on this machine, i want the desktop.  i installed kodi like this ([http://kodi.wiki/view/HOW-TO:Install_Kodi_for_Linux](http://kodi.wiki/view/HOW-TO:Install_Kodi_for_Linux)), which i have done multiple times before over probably the last 6 years.  previously i had done it on a much more limited system, remember when nettops were cool?  it was an atom D510.

the problem at hand is that my remote will not work using the out of the box kernel support, lirc, ir-keytable, etc.  the issue is not double presses.

this is what cat /sys/class/rc/rc0/protocols looks like (after purging lirc and ir-keytable)
```
other unknown rc-5 nec [rc-6] jvc sony rc-5-sz sanyo sharp mce_kbd [lirc] xmp
```

what do the [] brackets mean around rc-6 and lirc?  does that mean they are enabled?

when you install lirc, it prompts you to select a config and then installs the matching file.  this worked for me on this same ubuntu version on my old hardware (same remote different computer)

any suggestions?

---

### Post by TheFu on 2015-12-02
Did you try the rc.local fix?
That is my only suggestion.

---

### Post by sailingboyLLB on 2015-12-13
no luck....

---

### Post by sailingboyLLB on 2016-05-16
update: upgraded to 16.04, same story, same problem.

---

### Post by sailingboyLLB on 2016-05-27
i installed a PCIe USB 2.0 card and plugged the remote into that, it worked instantly without issue.  it's not a fix, but it is a work around.  more good evidence for an issue with the XHCI driver...

---

