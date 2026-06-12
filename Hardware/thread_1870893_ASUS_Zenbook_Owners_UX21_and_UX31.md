---
title: "ASUS Zenbook Owners UX21 and UX31"
date: 2011-10-28
forum: Hardware
---

### Post by shakabra on 2011-10-28
[SIZE="3"]**[CENTER]ASUS ZENBOOK UX21/31 OWNERS[/CENTER]**[/SIZE]
We need to combine forces to get the problems with the Zenbook under Linux solved in a logical and efficient way. To date the problems are:
[LIST]
[*]Sentelic touchpad doesn't get recognized as a touchpad
[*]Sleep freezes the computer
[*]Battery life is awful. (I'm getting about 2 hours).
[/LIST]

Is there anything else to gripe about?

Anyone know somebody who is knowledgeable enough to fix something like this?

Where do we start to get this fixed?

Here's the other threads that have been started
[SIZE="3"][http://ubuntuforums.org/showthread.php?t=1862078]("http://ubuntuforums.org/showthread.php?t=1862078")[/SIZE]
[SIZE="3"][http://ubuntuforums.org/showthread.php?p=11374684]("http://ubuntuforums.org/showthread.php?p=11374684")[/SIZE]

Let's fix this.

---

### Post by shakabra on 2011-10-29
bump

---

### Post by renselu on 2011-10-31
Bluetooth is not working either (pairing).

---

### Post by greenhat on 2011-10-31
I installed this app to improve battery performance.  [http://www.jupiterapplet.org/](http://www.jupiterapplet.org/) 

It seems to be working well, but i haven't done extensive tests between the battery life on Win 7 vs Ubuntu 11.10.

---

### Post by ironmantis7x on 2011-11-02
Hey peeps ... I will be joining this fine group soon as I will be purchasing a ZenBook 13.3 inch in a few days.

I have been looking at this forum for Linux on a UX31...
I found this on Asus's website for a bios update to fix the touch pad issue... I am just wondering if this is for Linux as the OS that is listed is other(??)??  Here is the link:

[http://support.asus.com/download.aspx?SLanguage=en&m=UX31E&p=3&s=369&os=8&hashedid=okyFhGJT4AM8jMkZ](http://support.asus.com/download.aspx?SLanguage=en&m=UX31E&p=3&s=369&os=8&hashedid=okyFhGJT4AM8jMkZ)


Let me know if this works ...

ironmantis7x

---

### Post by shakabra on 2011-11-02
I just updated the BIOS (which is really easy BTW. Just download to .zip file from ASUS extract it and put the extracted file onto a freshly usb drive freshly formatted as FAT. Then just boot into the BIOS and go to "advanced" tab and you should see the file and be able to update). It didn't seem to help anything however.

---

### Post by Galdrapiu on 2011-11-09
Hi I'm an UX21 owner and installed Ubuntu 11.10 (32bit):

The following additional problem occures:
- Ubuntu does not recognice the usb-ethernet-adapter of the UX21


Has anybody an idea?

---

### Post by shakabra on 2011-11-10
I think we fixed the suspend problem check out

[http://ubuntuforums.org/showthread.php?p=11442819#post11442819]("http://ubuntuforums.org/showthread.php?p=11442819#post11442819")

Also I read somewhere about compiling the driver for the ethernet adapter. I never use it so I can't remember the link. I will post it if I come across it again.

Now I would love to get the touchpad working properly. Any ideas?

---

### Post by GodzillaMonster on 2011-11-11
> **shakabra said:**
> I think we fixed the suspend problem check out

[http://ubuntuforums.org/showthread.php?p=11442819#post11442819]("http://ubuntuforums.org/showthread.php?p=11442819#post11442819")

Also I read somewhere about compiling the driver for the ethernet adapter. I never use it so I can't remember the link. I will post it if I come across it again.

Now I would love to get the touchpad working properly. Any ideas?

There's a few threads about getting the Sentelic driver working properly.. one approach seems to enabling absolute positioning and then wrapping it in the synaptics driver code - its a bit hard to figure out if there is any progress there though.

I have another issue when running on battery - the display brightness pops up to full brightness intermittently. So if I turn the brightness down, type/mouse for a bit, it pops back up to full brightness. Anyone else have this?

---

### Post by shakabra on 2011-11-11
I would be interested to see those links. I have googled everything imaginable. It's my biggest issue.

---

### Post by GodzillaMonster on 2011-11-11
> **shakabra said:**
> I would be interested to see those links. I have googled everything imaginable. It's my biggest issue.

I think the ideas here [http://lists.freedesktop.org/archives/xorg/2010-July/050726.html]("http://lists.freedesktop.org/archives/xorg/2010-July/050726.html") are in the right sort of area for us.

Sounds a little tricky - might have a peek at the open source driver code to see what's there that didn't make the kernel driver.

---

### Post by shakabra on 2011-11-11
Yeah I saw that already. I am really not too familiar with that sot of thing. 

On another note...

GodzillaMonster had question about screen brightness. I did notice that ubuntu took away the setting for screen brightness on battery and while plugged. This maybe it keeps going back to full bright.

---

### Post by GodzillaMonster on 2011-11-12
> **shakabra said:**
> Yeah I saw that already. I am really not too familiar with that sot of thing. 

On another note...

GodzillaMonster had question about screen brightness. I did notice that ubuntu took away the setting for screen brightness on battery and while plugged. This maybe it keeps going back to full bright.

Yeah - good call. I think that is pretty much it.

If you leave things by default, the Screen system settings widget has full brightness plus "dim screen to save power".

This sets up a condition where after a few seconds the screen dims, and when you interact with the machine, it sets full brightness again - or whatever you've set the brightness slider to.

This only appears to happen on battery, and is reasonable and good.

The issue would appear to be if you manually adjust your brightness with fn-f5/fn-f6, you aren't affecting the limit imposed by the slider on the widget. So when it dims again, and  then you interact with the machine, it restores the brightness to whatever the slider is set to, rather than the brightness level you manually set.

The fix is simply to disable "dim screen to save power".

---

### Post by GodzillaMonster on 2011-11-12
With respect to the touch pad issues, the current state of play is:

[LIST]
[*]The people at Sentelic have released an open source driver
[*]Parts of the driver are in the current kernels which is why the trackpad functions
[*]That driver doesn't expose multitouch, and Sentelic have patent concerns about putting it in the driver they have released
[*]The hardware is actually internally interpreting multitouch, since the mouse doesn't move when you use more than one finger (compare this behaviour to a non-multitouch-aware-trackpad).
[*]The driver code, and device directory, and control panel (fspc, on sourceforge), all indicate the driver should do side scrolling. I can't get that to work on the ux31 though
[/LIST]

Any other info to add to this summary?

---

### Post by yodogg on 2011-11-13
> **GodzillaMonster said:**
> 
The fix is simply to disable "dim screen to save power".


Thanks for the info. I found the screen going back to full brightness after a reboot, which isn't all that annoying. Nonetheless, I added the following line to my /etc/rc.local file before "exit 0".
```
echo 3 > /sys/class/backlight/acpi_video0/brightness

```

The computer now starts with 30% brightness at each reboot. In the line; 0 instead of 3 would be minimum brightness and 10 would be maximum. After that, one can adjust the brightness with the fn keys as needed.

Cheers,

---

### Post by GodzillaMonster on 2011-11-13
Thanks for the tip, yodogg.. haven't rebooted for 3.5 days, so haven't noticed as yet.. will pop your line in my rc.local :)

---

### Post by spedsal on 2011-11-15
> **GodzillaMonster said:**
> With respect to the touch pad issues, the current state of play is:

[LIST]
[*]The people at Sentelic have released an open source driver
[*]Parts of the driver are in the current kernels which is why the trackpad functions
[*]That driver doesn't expose multitouch, and Sentelic have patent concerns about putting it in the driver they have released
[*]The hardware is actually internally interpreting multitouch, since the mouse doesn't move when you use more than one finger (compare this behaviour to a non-multitouch-aware-trackpad).
[*]The driver code, and device directory, and control panel (fspc, on sourceforge), all indicate the driver should do side scrolling. I can't get that to work on the ux31 though
[/LIST]

Any other info to add to this summary?

I have an MSI x370 notebook and it has the same Sentelic touchpad problem.  It sucks that it affects these new ultrabook computers, though hopefully they'll be popular enough that someone will notice and care enough to fix the problem.  I try to keep tabs on the situation, but I haven't seen any progress in the 6 months or so I've had this problem.

---

### Post by jonah1980 on 2012-02-14
Hi sorry if this is a repeated post but there is a zenbook wiki for ubuntu installation here:

[https://help.ubuntu.com/community/AsusZenbook]("https://help.ubuntu.com/community/AsusZenbook")

Hopefully this can be updated and referenced to get everyone's zenbooks working correctly!

---

### Post by Flaburgan on 2012-11-07
Hi guys,

The touchpad problem is fixed with the 12.10 version.

However, there still is a battery issue, have you tips about it ? I have only 3 hours of power..

---

### Post by maze2 on 2012-12-12
For those of you who have a Sentelic touchpad on their zenbook, you may be interested to look at this thread:

[http://ubuntuforums.org/showthread.php?t=2093793](http://ubuntuforums.org/showthread.php?t=2093793)

I've made horizontal two-finger scrolling work.

---

### Post by sh0ckfile on 2013-07-31
Its about 3.5 to 4.5 hours working on battery on ux21a with u13.04 for me. Pretty nice for laptop that small as for me.

---

