---
title: "Today's 12.04LTS &quot;hardware update&quot; breaks display"
date: 2014-07-27
forum: Hardware
---

### Post by justtryit on 2014-07-27
Running Ubuntu 12.04 on HP laptop dv6105us.  AMD Turion64 mk36, GeForce 6150LE (VESA crush50 c51m)

Display has been working acceptably okay, for several months now, with Nvidia 304 driver installed via 'additional hardware drivers'.  

Today's incoming "hardware update", applied from ubuntu apparently has removed the Nvidia-recommended 304 driver, replaced it with something which doesn't work, and no longer seems to offer any 'additional drivers' to fix the problem.  Now getting nothing but black screen with white arrow cursor.  Up until an hour ago or so today, this Ubuntu 12.04 laptop has actually been running more smoothly than the 14.04 desktop has.  No longer.

Can still ctl-alt-F1 for command line.

Can still obtain low-res desktop via 'recovery-mode' + 'return-to-normal-boot'

Have now begun the search for a fix, if there is one.  Any tips or links toward resolution, which anyone might wish to share, will certainly be appreciated.

Thank you!

---

### Post by Yellow Pasque on 2014-07-27
I think the 304.xx driver is in the proposed repo right now: [https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1259237/comments/20](https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1259237/comments/20)

---

### Post by justtryit on 2014-07-27
Thanks for your help, Temujin.  

I went in through recovery>normal boot and checked the "proposed" updates section (which I did not have checked before in an attempt to remain 'vanilla', but the 304  driver is still not showing up in 'additional hardware drivers' yet.  The machine is now recommending a boat-load of software updates as well, so I am letting it do those, hoping that the proprietary display drivers will show up after the software updates finish.

---

### Post by Yellow Pasque on 2014-07-27
You could just install the driver the "old school" way through apt or Synaptic. The "additional drivers" utility is not infallible...

---

### Post by kansasnoob on 2014-07-27
I spent several hours today trying to get the nVidia drivers working again after a similar HWE upgrade with this graphics chip:

> nVidia C61 [GeForce 7025 / nForce 630a] (rev a2)

As far as I could tell what had previously existed in /etc/X11 has now moved to /usr/bin :confused:

So I opened System Settings > Software & Updates, clicked on the Additional Drivers tab and it showed the recommended driver still being installed so I tried disabling the driver, re-enabling the driver, etc, etc using the Additional Drivers UI with no success.

Next I opened Synaptic, searched for 'nvidia', then marked all of the currently installed 'nvidia' packages for complete removal and clicked on Apply.

Then I rebooted, opened the Additional Driver UI again, reinstalled the recommended driver, and on reboot it was working again!

Sort of rough going - I made sure to make a list of all the packages I removed just in case - but all seems well ATM so I have my fingers crossed.

---

### Post by justtryit on 2014-07-28
We must just be in the *'wrong time zone'*.  ...SIX DAYS AGO, on another thread, it was revealed (LTS be darned) that we 12.04 users really need to UPGRADE our machines to 14.04 now... [http://ubuntuforums.org/showthread.php?t=2235698&highlight=HWE](http://ubuntuforums.org/showthread.php?t=2235698&highlight=HWE)

Thanks to all who responded here.  I have just downloaded 14.04.1 amd64 desktop to see if that will work reliably on this machine.
[IMG]http://seadogbytes.com/RelativeTerm.jpg[/IMG]

---

