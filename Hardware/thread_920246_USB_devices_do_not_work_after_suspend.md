---
title: "USB devices do not work after suspend"
date: 2008-09-15
forum: Hardware
---

### Post by Vitamin_A on 2008-09-15
Hi all

About two weeks ago, I installed Ubuntu 8.04 onto my Gateway T-6842 Laptop, and I had just noticed this problem.  After my laptop wakes up from suspend, none of the USB ports work.  I searched the forums for support, but all the fixes that worked for others before me fail to solve my problem.

Can someone help me?

Thanks

---

### Post by DoctorMO on 2008-09-15
Can you get your lshw and dmesg logs? otherwise we can't help you.

> 
cp /var/log/dmesg ~/Desktop/dmesg.log
sudo lshw > ~/Desktop/lshw.log


then attach the two files on your desktop.

---

### Post by Vitamin_A on 2008-09-16
> **DoctorMO said:**
> Can you get your lshw and dmesg logs? otherwise we can't help you.



then attach the two files on your desktop.



Sorry about that, here they are, it'd only let me attach them as an archive.

---

### Post by DoctorMO on 2008-09-16
Interesting, there are no logs about suspending in that dmesg output. Did you do the suspend before taking the logs?

---

### Post by Vitamin_A on 2008-09-16
> **DoctorMO said:**
> Interesting, there are no logs about suspending in that dmesg output. Did you do the suspend before taking the logs?

was I supposed to?
Sorry again.  Pulling up those logs now

---

### Post by DoctorMO on 2008-09-16
OK I can't see anything wrong yet, can you get the syslog next:

> cat /var/log/syslog > ~/Desktop/syslog.log

---

### Post by Vitamin_A on 2008-09-16
Alright, here it is.

---

### Post by DoctorMO on 2008-09-16
According to syslog, your webcam and other usb devices came back online as expected.

the only problem is that your hard drive (hdb) or what ever it is can't get the capacity and is causing rather a lot of sys activity. Perhaps it would be worth finding out why that is causing a problem?

Otherwise there is no reason for your usb to not work coming out of suspend. I've looked for your usb chipsets online and no one else has reported this same problem with this chipset. And the syslog pretty much shows each of the devices it's bringing online on the usb bus including all the hubs.

Thoughts?

---

### Post by Vitamin_A on 2008-09-16
Yeah, I just checked my webcam, it does work (it wasn't really my primary concern to begin with, so I never really checked it.)
As for that capacity issue, yeah, I really should check it out...

Its odd that it shows all my USB reactivating, but nothing plugged in works... and plugging into a different port yields no positive results.

Is it possible I had a messy install?

---

### Post by DoctorMO on 2008-09-16
It's possible.

You can do a few things though to see what is happening. Go to a terminal and use the following command:

> sudo udevmonitor

Now plug one of your usb devices in, if it starts giving you output then paste it back here. If not then unplug the device again and do this:

> tail -f /var/log/syslog

Now plug it back in and see what the results are, if you get more log entries then paste them back here. Try and cut out the CAPACITY errors though, they will keep on appearing.

You might have better luck using the live cd and seeing if the same problem happens when booted up into the live cd.

Try all these things and let me know how it goes.

---

### Post by pqrs541 on 2008-09-16
The Weather:[buy wow gold](http://www.mmoinn.com)  It's so dry, the trees are bribing the dogs. It's been hitter?s a goat's butt in a pepper patch.  Wintry roads are said to be "slicker than otter snot. [wow gold](http://wowus.mmoinn.com/index.do?PageModule=OrderForm_new)[wow gold](http://woweu.mmoinn.com/index.do?PageModule=OrderForm_new) [World of warcraft Gold](http://www.mmoinn.com)[wow gold](http://www.mmoinn.com)

---

### Post by Vitamin_A on 2008-09-16
well, the first command showed no output, and the second command only gave me the capacity errors. That, or I missed a change in the output.

I;ll try booting the live CD when I get home tonight.

---

### Post by DoctorMO on 2008-09-16
that's bad, that means the usb is either being flooded or has crashed at some point. Getting rid of those capacity errors is your first job. Use the commands above when you boot'en into the live environment to test is it's still a problem.

And let me know if your using 8.04.1 or plain old 8.04

---

### Post by Vitamin_A on 2008-09-17
Alright.  I booted into the live CD, and suspended there, and woke mhy laptop back again.  The USB devices were read (in the sense that the lights on my tablet lit up).
forgot to plug in those commands... sorry, will get on that soon.

and i;m on 8.04.1

One more thing, when I woke my system from suspend (installed version, not live cd), i noticed that is said "over current on USB port 4" or something along those lines.

---

### Post by DoctorMO on 2008-09-17
An over current problem can cause the usb to shut down. very bad.

I look forward to seeing your log results for the live cd. I suspect a reinstall may help now.

---

### Post by Vitamin_A on 2008-09-18
Well, I can't really get logs of the live cd, because when my computer wakes up from suspend, it doesnt really lod the dekstop... at all.  I can see the mouse cursor moving, though.

actually, jsut got 'em (Ctrl-Alt-F1 does the same thing as terminal, right?).  Capacity errors are still there.

For a re-install, do i have to format the partition?  Or can I jsut install over my current installation.
And should I wait for 8.10?

One more thing:
The actual error message that came up when waking up said "over-current change on USB port 4".
I did a quick search here, and there's no fix for that.

---

### Post by DoctorMO on 2008-09-18
Time to report a bug on launchpad me thinks. Sorry I couldn't have been more helpful in this case, but it looks like there is either some hardware failure or there is an odd kernel bug which may or may not be fixed in later releases.

Try an older live cd, perhaps on of fiesty or gutsy and try it and see if you get the same errors in the same manner. If so then it probably is a hardware fault. If not then it's probably a kernel bug and you should report it in launchpad.

---

### Post by IntuitiveNipple on 2008-09-18
How many devices are connected to the PC's external ports?

Is an external USB hub connected to the PC? If so, is it self-powered or drawing power from the PC bus?

Have you tried systematic suspend/resume cycles whilst removing one device at a time? If one of the external devices is causing the issue this will help determine which one.

---

### Post by Vitamin_A on 2008-09-19
@ DoctorMO:
Well, I poped in a gutsy Live CD, and suspended it, and woke it up, and this time, my USB was working, and there were no capacity errors, so, my next question would be how exaclty do I report things in launchpad?

@ IntuitiveNipple:
I have two devices connected to the external ports, and no USB hub.  I have tried resuming with all combinations of devices (including none), but after waking up, USB still doesn't work.

Looks like its either a kernel bug as DoctroMO suggested, or a messy install.
Either way, 8.10 doesn;t look to be too far away, so I can wait a bit.

---

### Post by DoctorMO on 2008-09-19
go to [http://bugs.launchpad.net](http://bugs.launchpad.net) We still need people to submit bugs so that the issue becomes known, make sure to search to see if someone has reported it already.

---

### Post by Vitamin_A on 2008-09-20
I did a quick search there, and it looks like someone had the same problem with 6.06.
However, one of the comments said to try the alpha on Intrepid, and so I decided to give it a shot too, and I found that I don't get those errors in Intrepid.  Should I still report it?  It looks like its fixed.

---

### Post by DoctorMO on 2008-09-20
No, see if you can find the existing bug and add a me too so devs can see it's fixed.

---

