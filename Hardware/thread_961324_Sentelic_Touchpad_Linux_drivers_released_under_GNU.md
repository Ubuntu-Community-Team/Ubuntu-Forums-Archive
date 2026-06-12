---
title: "Sentelic Touchpad Linux drivers released under GNU GPL!"
date: 2008-10-28
forum: Hardware
---

### Post by flummoxed on 2008-10-28
Users of the MSI Wind have been frustrated with the Sentelic touchpad, mainly because of the inability to disable to the tap-to-click. Sentelic has released their linux driver, in open source form.

Here is the link:

[http://sourceforge.net/projects/fsp-lnxdrv/](http://sourceforge.net/projects/fsp-lnxdrv/)

I haven't tried them out yet, but it's promising that they've been released under the GPL!

---

### Post by phil02 on 2008-12-31
Just in case some one with a Sentelic touchpad using Ubuntu comes across this thread, there is a discussion at this [[COLOR="Red"]thread[/COLOR]]("http://forums.msiwind.net/default-msiwind/sentelic-linux-drivers-released-under-gnu-gpl-t4828.html") at the MSI wind forums about compiling and using the drivers on Ubuntu.  There is also a [[COLOR="Red"]bug[/COLOR]]("https://bugs.launchpad.net/bugs/311869") opened to request the patch be added to Ubuntu's kernel.

---

### Post by dash86no on 2010-03-22
The sentelic driver is already in 10.04 lucid. 
The problem, is that for whatever reason the "touchpad" tab does not appear on the mouse configuration menu. 

The easiest way to disable tap to click using lucid, is to do the following:

sudo su
echo -n c > /sys/devices/platform/i8042/serio1/flags 


tap to click will now be disabled. For some reason, this did not work for me when I tried sudo, hence the sudo su before executing the echo command. 

Also, before running this command, it may be a good idea to run:

cat /sys/devices/platform/i8042/serio1/flags 

and double check that all that's in there is a single "C". The capital C means tap to click is enabled, and a small "c" indicates that the tap to click feature is disabled. 

The same principle can be applied to disable vertical scroll:

sudo su
echo -n 0 > /sys/devices/platform/i8042/serio1/vscroll

In this case, "1" means that vertical scroll is enabled, and "0" means disabled. 

All this information can be found in the launchpad link above, but I wanted to add some details here in the hope that it may save somebody some time if they happen to come to this page when looking to turn off "tap to click" with a sentelic mousepad. 

Cheers, 

DA

---

### Post by phil02 on 2010-05-24
I just upgraded to Lucid after a brief stop in Karmic.  I had been holding off on Karmic because of the backlight cycling problem on the Wind.

fspc doesn't seem to work anymore.  It gives errors about being able to load and save the configuration.

Your instructions on setting flags in /sys/devices/platform/i8042/serio1/ works but I can't figure out how to automate this since it needs sudo.

---

### Post by sduensin on 2010-06-11
Toss the commands in /etc/rc.local and they'll be executed on startup.

(Thanks for the information in this thread - I was going insane with the hscroll enabled!)

Scott

---

### Post by mzecher on 2010-06-13
Thanks a lot.

This information should be more documented and easier to find, such as in the wiki.

---

### Post by CBR_Rob on 2010-12-18
I just stumbled upon this after searching for quite a while to turn off the tap to click and to turn on the vertical scroll on my netbook. It sure has been a pain not having those changed over.

---

### Post by Dawudd on 2010-12-21
The Sentelic touchpad should be able to use the synaptics driver for all the features it provides: edge scrolling, disabling tapping while typing, and possibly even two-finger scrolling. This requires that the Sentelic driver be fixed. Sentelic caused this bad situation by removing support for absolute positioning from their driver. For anyone comfortable with compiling the kernel, adding this code back in and testing it is *relatively* easy. That is not I, but I thought I’d mention this on here, where there might be someone more capable than I. If anyone wants to help, users of Sentelic touchpads everywhere will be very grateful. See [this bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/311869/comments/71") on Launchpad and [this thread]("http://lists.freedesktop.org/archives/xorg/2010-July/thread.html#50726") on the X.org support list.

Anyone want to help?

Thanks!

---

### Post by Brett Lyons on 2010-12-30
I've got sentelic touchpad hardware, and I am currently running a custom kernel I compiled myself sooo . . . Where would I find the code that needs to be tested?

~Brett

---

### Post by Dawudd on 2010-12-30
> **Brett Lyons said:**
> I've got sentelic touchpad hardware, and I am currently running a custom kernel I compiled myself sooo . . . Where would I find the code that needs to be tested?
See Éric’s comments in the [short thread]("http://lists.freedesktop.org/archives/xorg/2010-July/thread.html#50726") that I linked to before. He links to their source repository and tells you which file needs to be modified. Beyond that, I have no more information. You could also try e-mailing him yourself. He was extremely nice and helpful.

---

### Post by greghk on 2011-02-05
> **phil02 said:**
> I just upgraded to Lucid after a brief stop in Karmic.  I had been holding off on Karmic because of the backlight cycling problem on the Wind.

fspc doesn't seem to work anymore.  It gives errors about being able to load and save the configuration.

Your instructions on setting flags in /sys/devices/platform/i8042/serio1/ works but I can't figure out how to automate this since it needs sudo.
I was able to toggle the write bit on flags using 

chmod o+w flags 

from a root prompt. 

Then update flags from a user prompt. This should allow me to write a script to toggle settings.

---

### Post by Temuss on 2011-02-27
> **flummoxed said:**
> Users of the MSI Wind have been frustrated with the Sentelic touchpad, mainly because of the inability to disable to the tap-to-click. Sentelic has released their linux driver, in open source form.

Here is the link:

[http://sourceforge.net/projects/fsp-lnxdrv/](http://sourceforge.net/projects/fsp-lnxdrv/)

I haven't tried them out yet, but it's promising that they've been released under the GPL!


I just installed this and it worked perfectly to disable the Tap to Click.  That was driving me crazy as my touchpad is so sensitive.  I didn't get the scrolling to work though.

---

### Post by Me Mechant on 2011-10-23
> **dash86no said:**
> 

The easiest way to disable tap to click using lucid, is to do the following:

sudo su
echo -n c > /sys/devices/platform/i8042/serio1/flags 


Sorry to wake up the dead, but this command for disabling the click on tap works for me and i'm very happy to have found it. I try what others have suggest about putting this command on startup but so far nothing works. The fspc driver doesn't work at all for me (unable to save). Any advise?

I'm running lubuntu 11.10

---

### Post by Carleas on 2012-12-16
How can this change be made permanent?  After running 

```
echo -n c > /sys/devices/platform/i8042/serio1/flags 
```

the settings change back every time the computer is restarted or suspended.  Can that behavior be disabled?  I've tried writing a script, but I've never been able to get it to work (I tried using fspc).

What prompts the flags file to be reset?  It seems inefficient to have the solution be to undo the behavior that resets the file, rather than to disable that behavior in the first place.  Or is it possible to change the information from which the flags file is reset?

I apologize if I'm missing something, I know I'm out of my depth, but I've been putting up with this for a year now and after upgrading to 12.10, I'm raring to find a permanent fix :mad:

---

