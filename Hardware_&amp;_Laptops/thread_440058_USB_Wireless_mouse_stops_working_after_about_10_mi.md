---
title: "USB Wireless mouse stops working after about 10 minutes"
date: 2007-05-11
forum: Hardware &amp; Laptops
---

### Post by latex001 on 2007-05-11
Hi

I have a _Microsoft Wireless Notebook Optical Mouse 4000_ that normally works great but when using Ubuntu it works fine for about 10 minutes and then just stops working and the light on the dongle goes out.

I am very new to Ubuntu/Linux/this community so don't really know where to start or what type of information is important to help troubleshoot this issue. My windows background makes me think that the mouse is going into a power saving mode but don't really know where i can check this.

Any ideas or suggestions would very appreciated.

--LaTeX

---

### Post by octathlon on 2007-05-27
I have exactly the same problem, using a USB Logitech Trackman Wheel.  Works fine for a while, then suddenly the light goes out andit stops working.  

I'm using a Toshiba Satellite laptop with an ATI graphics card.   I noticed the same problem in the Mint Live CD, but it did not happen with the MEPIS 6.5 Live CD.

Any troubleshooting ideas appreciated.

---

### Post by gopoo on 2007-05-27
10 minutes is pretty long time for something to goes off......it might goes off in seconds , or it just wont....

can you figure out what exactly were you doing when it goes off ?

like starting a song ? , changing the resolution ? ,something related to hardware... ????


[SIZE="1"]I hope it is not an low battery problem.[/SIZE]

---

### Post by gridsleep on 2007-05-27
I am having this problem also, with 7.04 on a Satellite M45 with a Logitech V200 wireless USB mouse.  I haven't seen enough of a pattern so far, but I think it has something to do with Flash.  I have seen the mouse lose connection (device detached according to the system log) viewing an animation and passing the mouse cursor over a hot button or drop down menu on the web screen.  Also it has locked up seconds before shutdown, while the shutdown screen is still up.  I have also seen a USB key get kicked off the system in the same way.  I don't think it is just the mouse, but any USB device.  I have also gone well over an hour without losing the mouse.  I will keep testing until I find the pattern.  This is the best Linux distro so far, with absolutely everything working perfectly including wireless, network printing, cd/dvd burning, browsing and email.  Ubuntu is the Windows killer.  Once this USB detaching problem is solved, it will be perfect.

---

### Post by gopoo on 2007-05-30
i think , the problem is with the graphics driver , try to change to vesa in device section in /etc/X11/xorg.conf ,

---

### Post by nquinnathome1 on 2007-06-01
Has anyone checked if this is a known bug? I'm experiencing the same problems; only with Feisty; installing Edgy on a Toshiba Satellite works fine.

---

### Post by robwhite1979 on 2007-06-24
I've been experiencing the same issue, it get's weirder for me tho...  I have 2 mice (one logitech wireless and one that was supplied with my dell system).  If the logitech stops responding, i can plug in the dell one and it will work ok for a while and vice versa.  Once they stop responding NOTHING will get them working again except a reboot.  Very frustrating...  Even the USB ports power seems to shut down.  Another thing, just unplugging/reconnecting the affected mouse has no effect at all, only switching to the other one...  Has anyone figured this one out yet?

---

### Post by mr_mister on 2007-07-16
this is my first post ever, so i hope i'm not stepping on any toes... hope this has not been answered somewhere else!

in any case:

i just got into linux three days ago, and everything is working great... except my wacom tablet. i am working on getting the wacom tools to pick up the tracking and pressure sensitivity, but as a mouse, i'm experiencing the same problems as you guys. from anywhere between a couple minutes to (probably max) an hour, the cursor stops responding to the mouse, though the tablet light stays on. unplugging and plugging it back in does not get the light to respond. no other usb devices will respond, either, until a reboot.

i am running ubuntu feisty on a toshiba satellite (with an ati card). so yeah, it's looking like there might be a trend.


cheers

j

---

### Post by happyisland on 2007-07-17
I'm having a similar problem with 6.10 and a logitech usb mouse. It always stops working after a minute or two, but can be reactivated with a replug. Anybody have any ideas about how to fix this? It's super annoying...

---

### Post by geraldm on 2007-07-18
I also have experiences the problem when the mouse just goes dead and no
longer responds.  The circumstances under which the problem occurs vary, and
I have not narrowed down the problem enough to file a bug report that I can be
certain conveys the problem.

I have two different mice, one logitech, one microsoft.  I also have three different
possible drivers: ohci-hcd, uhci-hcd, and ehci-hcd.

There are some websites I visit that seemed to produce problem in abundance, one of 
them is from ubuntu (do not recall whether ubuntu.com or ubuntuforums.org)
but these forums no longer continue to be a problem.  I am tending to believe that
I have just problems with my own hardware.
These are what I am looking into:
  -- my kernel does not use power-saving nor CONFIG_USB_SUSPEND.
  1) the website sends back a page that causes my mouse to go dead.  I am suspecting
  the webpage data because when the mouse goes dead, it can also take the keyboard
  out as well.  Only solution I know of is to use the big red button, restart.
  2) After monitoring the problem for awhile, it has appeared that the problem occurs only
  on the uhci-hcd, and is not known to be on ehci-hcd or ohci-hcd.  Sometimes it
  happens that the uhci-hcd mouse goes dead, but the other mouse on either of the
  other connectors can continue to function.  (still need more testing, though)
  The keyboards one AT, the other USB/PS/2 used as PS/2 have continued to work
  OK when uhci-hcd mouse dies.
I am continuing to look for a solution, but the problem has not happened often 
enough to pursue.

Gerald

---

### Post by mr_mister on 2007-07-20
hi guys,

i'm a writer, so my keyboard is important enough to me to warrant further investigation...

many people have reported various bugs, but i was able to solve the problem using the steps located here:

[http://ubuntuforums.org/showthread.php?t=75281&page=7](http://ubuntuforums.org/showthread.php?t=75281&page=7)

another place that might be useful if you are not having a clock speed problem is this page:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty/Hardware#Workaround_for_random_device_disconnections](http://ubuntuguide.org/wiki/Ubuntu:Feisty/Hardware#Workaround_for_random_device_disconnections)

which fixes a bug that appears to be caused by (excessive?) usb2 use. forcing usb1 on all ports might help you, too.

recall that i am having the trouble where one usb device (usually keyboard or mouse) will freeze, and soon after all other usb devices are disconnected. reconnecting the devices did not fix this. the only thing previously that fixed it was a reboot.

hope this helps other people!


cheers

j

---

### Post by octathlon on 2007-07-20
> **mr_mister said:**
> 
many people have reported various bugs, but i was able to solve the problem using the steps located here:

[http://ubuntuforums.org/showthread.php?t=75281&page=7](http://ubuntuforums.org/showthread.php?t=75281&page=7)

j

Thanks, but could you tell us the exact post number that contains the steps you are referring to?  There are several ideas mentioned on that page of the thread--which one worked for you?

Thanks,

---

### Post by geraldm on 2007-07-20
UPDATE my previous post:
When the mouse dies, the message in /var/log/syslog suggests one solution,
to add "irqpoll" to the kernel options line.  I will test that, too.
The main problem is that this computer only had UHCI and EHCI hardware, but
ohci_hcd module drives the mouse.  /proc/interrupts shows that there are interrupts
assigned for uhci and different ones for ohci.  The interrupts go unattended, and 
soon the kernel kills the hub. 
Getting assigned interrupts to the right hardware looks like a workable solution also.
I have blacklist options also, so I will test until something works.

Gerald

---

### Post by mr_mister on 2007-07-24
> **octathlon said:**
> Thanks, but could you tell us the exact post number that contains the steps you are referring to?  There are several ideas mentioned on that page of the thread--which one worked for you?

Thanks,


Oh, woops, I'm sorry! The link was supposed to go to the first/top post of the thread:

[http://ubuntuforums.org/showthread.php?t=75281](http://ubuntuforums.org/showthread.php?t=75281)

...not to the 7th page of it.

As for my personal situation, adding just "noapic" worked. Apparently it may differ depending on your system.

---

### Post by octathlon on 2007-07-25
Thanks, Mr mister, but the bug we are talking about here doesn't have any relation to a clock speed issue, just the USB issue.  It may be that the noapic works for both problems, though.  I wonder what all features get turned off by using the noapic option, and what other problems may be caused by doing this.

---

### Post by geraldm on 2007-07-25
octathlon:
APIC is for power.  There are power-saving modes that can be enabled/disabled, 
One of them is CONFIG_USB_SUSPEND.  The power-conservation portion apps
would force the USB subsystem to suspend, even when a device required continuing
use of the subsystem.   The initiation of the suspend is from a suspend button on a 
notebook, for instance.  Initiation of the suspend state can cause loss of data, and
loss of the use of the device, temporarily, (longer if it is a bug).
More information on the suspend is in the linux kernel sources Documentation/power/swsusp.txt 
(and other files in that directory)

Gerald

---

### Post by octathlon on 2007-07-25
Thanks for the info, Gerald.  Looking at some other threads about it here and at several bug reports on it in Launchpad (e.g. #41272, #43305, #84762), it looks like no one has found a real solution yet.  Until they do ('cause I sure can't), I just won't be able to run Ubuntu on my laptop.  Fortunately it works fine on my desktop.

---

