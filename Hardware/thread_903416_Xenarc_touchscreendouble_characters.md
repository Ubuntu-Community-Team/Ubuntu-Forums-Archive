---
title: "Xenarc touchscreen/double characters"
date: 2008-08-28
forum: Hardware
---

### Post by pmgeahan on 2008-08-28
Folks - 

Ubuntu Hardy install here, kernel 2.6.24-19-generic on an Intel Mini-ITX motherboard.  I've attached to this a Xenarc 7000 touchscreen monitor.  I'm driving the monitor with drivers from EETI([http://home.eeti.com.tw/web20/eg/drivers.htm](http://home.eeti.com.tw/web20/eg/drivers.htm)).  The drivers seem to work fine, with one notably ugly exception - every click on the screen seems to be two clicks.  It seems that there will be one 'click' for press and one 'click' for release.  

I've been struggling with this for the last few days, because this makes the use of the on-screen keyboard(gtkeyboard) impossible.  Does anyone have any idea what the problem might be?  

Thanks, in advance, for any help.

---

### Post by SRamsesIV on 2008-09-13
Thanks for this thread - I used your link to get the eGalax driver to work under Hardy (Xorg 1.4).  But then I also had the double click problem.

I finally found the answer here:
[http://gentoo-wiki.com/HOWTO_Car_Computer#evtouch_Driver](http://gentoo-wiki.com/HOWTO_Car_Computer#evtouch_Driver)

It was a matter of changing the "Configured Mouse" input device to use the specific device rather than the generic '/dev/input/mice'.  That is edit xorg.conf (within the Section "InputDevice" Identifier "Configured Mouse") and change the line
```
Option "Device" "/dev/input/mice"
```
to something like
```
Option "Device" "/dev/input/mouse1"
```
Which specific device to use will depend on your setup (might be mouse0, mouse1, etc.).

Hope this helps.  That link also has instructions on using the evtouch driver instead, but I found the EETI setup far easier.

---

### Post by pmgeahan on 2008-09-15
> **SRamsesIV said:**
> 
It was a matter of changing the "Configured Mouse" input device to use the specific device rather than the generic '/dev/input/mice'.  That is edit xorg.conf (within the Section "InputDevice" Identifier "Configured Mouse") and change the line
```
Option "Device" "/dev/input/mice"
```
to something like
```
Option "Device" "/dev/input/mouse1"
```
Which specific device to use will depend on your setup (might be mouse0, mouse1, etc.).


SRamses:

Thanks for the followup.  Unfortunately, I was already doing that(using a specific mouse device instead of the generic)  and I'm still getting the double-click issue.  

WOuld you mind posting your xorg.conf?  It might help for me to see if there are any other differences between ours.  

Thanks(to both of you) for your help.

---

### Post by pmgeahan on 2008-09-15
> **pmgeahan said:**
>   

Thanks(to both of you) for your help.

Especially as, after a few more minutes of figuring, I got it.

The problem was that I was using a "Dummy" driver entry for the mouse; this was something that was specified in another FAQ for getting a touchscreen to work.  To the best I can tell, however, xorg now picks up things like mouses automatically; so the "dummy" entry was being ignored, and the mouse automatically picked up and driven with the IMPS/2 driver.

The solution, in my case, was to explicitly name the IMPS/2 driver in the mouse entry, which prevented the 'ghost' mouse from double-tapping the keys

Thanks to both for your help.

---

### Post by SRamsesIV on 2008-09-18
I actually found that once I disconnected the real mouse I had the double-click problem come back.  To solve that, I had to remove the mouse device from my xorg.conf and set the touchscreen to be the core pointer.

Now, of course, I can't plug in a mouse and use that if I want.

Anyone know how to enable both the touchscreen and an optional mouse?  So that xorg will use the touchscreen by default but also pick up the USB or PS/2 mouse if it is plugged in - and not have it do the double-clicking ...

---

### Post by pmgeahan on 2008-09-18
> **SRamsesIV said:**
> 
Anyone know how to enable both the touchscreen and an optional mouse?  So that xorg will use the touchscreen by default but also pick up the USB or PS/2 mouse if it is plugged in - and not have it do the double-clicking ...

I just checked with my box here and I do not have that problem.  When the mouse is unplugged, the touchscreen still works fine.  

Maybe post your xorg.conf for us to take a look at?

---

