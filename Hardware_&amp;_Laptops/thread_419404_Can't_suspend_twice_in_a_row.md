---
title: "Can't suspend twice in a row"
date: 2007-04-23
forum: Hardware &amp; Laptops
---

### Post by insyzygy on 2007-04-23
I have an Dell inspiron 8500 which I've upgraded to Feisty. I have a strange problem, I can't suspend twice.
Once I boot up, I can suspend and resume fine. But then if I try to suspend a second time, it tries to go to sleep then comes back with the error
```
ata1: ACPI get timing mode failed.
ata2: ACPI get timing mode failed.
```
After that it just hangs and is totally unresponsive and I have to do a hard power down.  Suspend worked fine in dapper.


                                                                                                                                                        Josh

---

### Post by insyzygy on 2007-04-25
Additionally I believe that this is related to the fact that my hard drive is now viewed as a scsi drive (sda)  in feisty whereas in dapper it was hda.  This is supported by the fact that this error message 
appears in the source code for the new ata drivers that are now handling the hard drive.

[http://lkml.org/lkml/2007/2/20/223]("http://lkml.org/lkml/2007/2/20/223")

---

### Post by mrfuzzemz on 2007-04-28
What video card do you have and what do you use for drivers?  I, too, can only suspend once.  This is on a laptop with an NVidia GeForce Go 7700 512MB using the 1.0.9755 NVidia drivers included with Ubuntu.

---

### Post by insyzygy on 2007-04-28
Good to finally find someone having the same problem (though it be better if neither of us were having the problem.)

I have a nvidia geforce 4 4200 graphics card with 64 mb of ram, and am using the ubuntu nvidia drivers. Do you get the same ata error message as I do when you suspend the second time.
They show up on screen and in /var/log/kern.log

 I had assumed that this was the cause of the problem  as I also get some weird ata errors at boot 
and my hard drive is now sda when it used to be hda.

Also in dapper I was able to suspend fine also using the nvidia drivers (though that was a different version I suppose.) Have you tried using the unaccelerated nv drivers ( I have not tried though maybe I should).

                                                                                                                                        Josh

---

### Post by mrfuzzemz on 2007-04-28
My hard disk is SATA so it is correct that it uses sda.

I have not noticed the ata1 and ata2 errors that you receive--what happens on my attempt to suspend again is my screensaver starts, but the system does not go to sleep.  If I move the cursor I am asked for password again, but my keyboard is completely unresponsive.

---

### Post by insyzygy on 2007-04-28
I believe you are correct this is a problem with the new nvidia drivers. I switched to the nvidia-legacy drivers and suspended three times in a row successfully. 
Unfortunately it appears you can't use desktop effects with the legacy drivers.

                                                                                                                                         Josh

---

### Post by insyzygy on 2007-04-29
I had started a bug report. Unfortunately after switching to the nvidia-glx-legacy I'm having problems switching to nvidia-glx again to provide log files output. I started a bug report, maybe you can respond to the request for log files if you are still using the nvidia-glx drivers.

[https://bugs.launchpad.net/bugs/109529 ]("https://bugs.launchpad.net/bugs/109529")

---

### Post by insyzygy on 2007-05-01
I was able to give all the information so ignore the previous comment. You may want to post to the bug report that you also have the same proglem just to indicate that I'm not the only one. 


[https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/109529]("https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/109529")

---

### Post by Immolatus on 2007-05-01
I had the same problem (suspend once per boot only) graphics: intel 82852/855GM integrated.
I don't think it has to do with the drivers, however after installing the 915resolution package from synaptic my machine will suspend but not resume (instead it just powers off poof!).

---

### Post by insyzygy on 2007-05-02
In my case I'm pretty sure it is due to the drivers. I found I could suspend with the nvidia-legacy as well as with the open source nv drivers but not the newer nvidia drivers.  However, in all cases I needed  /etc/default/acpi-support and xorg.conf to be set correctly (and these were different for nv or nvidia) in order for suspend to work.

---

### Post by Immolatus on 2007-05-03
> **insyzygy said:**
> In my case I'm pretty sure it is due to the drivers. I found I could suspend with the nvidia-legacy as well as with the open source nv drivers but not the newer nvidia drivers.  However, in all cases I needed  /etc/default/acpi-support and xorg.conf to be set correctly (and these were different for nv or nvidia) in order for suspend to work.

What changes need to be made??

---

### Post by insyzygy on 2007-05-13
Sorry I was away for a bit.
To suspend with the nvidia drivers follow  this  guide
[https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend]("https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend")

If you are using the nv drivers you want the default acpi-support file. Using the default with the nvidia drivers and suspend won't work, and using modified one with the nv drivers and suspend won't work (in my experience).

---

### Post by mrfuzzemz on 2007-05-14
Are you then able to suspend as many times as you want with this modification and using the nvidi-glx drivers?
thanks

---

### Post by Immolatus on 2007-05-14
I'm having this problem without the use of any restricted drivers at all.

---

### Post by insyzygy on 2007-05-14
With the modifications I linked to and using the nvidial-glx-legacy drivers, i can suspend as many times as I want. (With the nvidia-glx drivers I can suspend and resume once). 

Sometimes on resume I get a white screen but if I do 
ctrl-alt f1 and then ctrl-alt-f7 
I have the log in screen and it works fine (this switches to a virtual terminal and back to X windows which seems to wake the monitor up).

  
 Immolatus: can you suspend and resume once, or not at all.

---

### Post by Immolatus on 2007-05-14
once

---

### Post by frogotronic on 2007-05-15
Same problem here.

I'm going to try compiling the vanilla nVIDIA drivers from nvidia's site (the 9631 drivers) and let you guy know how that works.

maybe it's an ubuntu specific nvidia-glx build problem

- CH

---

### Post by frogotronic on 2007-05-15
no difference.

this problem is recent, within the last two or three weeks

I remeber an ACPI update, and then a HAL update (a few days ago).  I think the ACPI update was the source of the problem.

---

### Post by Immolatus on 2007-05-15
[http://www.suspend2.net/downloads/](http://www.suspend2.net/downloads/)

So I found this in my travels today but I can't figure out how to install it to try it out.
Maybe one of you can figure it out.

Notice that there is a patch specifically for feisty. This download is also linked to the official docs.

---

### Post by frogotronic on 2007-05-15
cool.

I tried to use this a while ago, but a special fiesty patch is pretty good.

I'll post the link to the instructions

---

### Post by mrfuzzemz on 2007-05-15
> **cement_head said:**
> cool.

I tried to use this a while ago, but a special fiesty patch is pretty good.

I'll post the link to the instructions

Please let us know how it turns out if you try it.  Great thanks!

---

### Post by frogotronic on 2007-05-16
> **mrfuzzemz said:**
> Please let us know how it turns out if you try it.  Great thanks!


Okay.

You have to download the source kernel, patch it, and recompile the patched kernel and install it.  Additionally, if you use restricted modules (nVIDIA, ATI or WiFi proprietary drivers) you have to compile those into the kernel as well.

Here's a Kernel HOWTO:

[http://doc.gwos.org/index.php/Kernel_Compilation_Dapper](http://doc.gwos.org/index.php/Kernel_Compilation_Dapper)

Here's a Feisty HOWTO for Suspend2:

[http://ubuntuforums.org/showthread.php?t=418375&highlight=suspend2+feisty](http://ubuntuforums.org/showthread.php?t=418375&highlight=suspend2+feisty)

I haven't tried this - but I might.

- CH

---

### Post by insyzygy on 2007-05-16
cement_head: What type of graphics card do you have. Also, did you try using nvidia-glx-legacy
(if you have an nvidia card).  I found that suspend works with that driver,  though desktop effects don't ( but then again I don't think anything will suspend with desktop effects on  anyway.)

I think the ata timing error may be a different issue as I can suspend with the nvidia-glx-legacy even though I still get that error showing up in my logs. I wonder if we should file a separate bug report on the ata timing errors.

---

### Post by frogotronic on 2007-05-16
nVIDIA GeForceGo2 (16 MB).

Using the 9631 drivers up until about a month ago I could suspend multiple times in a row.  I like this driver as opposed to the legacy driver because I use the XServer Settings Panel for Twinview (Impress slideshows).


I think it is a driver related ACPI issue.  I've filed a bug report on the suspend issue in the ACPI bug thread.


- CH

---

### Post by frogotronic on 2007-05-17
Hi,

Got an interesting error message this AM when I re-animated my laptop from SUSPEND.  The gnome-power-manager said that Suspend had failed.  The FAQ for gpm has some really helpfull pointers which I'm going to work through.

- CH

---

### Post by frogotronic on 2007-05-18
PROBLEM IS FIXED - WORKAROUND:

Use Synaptic to force a downgrade of the recent HAL update:

[http://ubuntuforums.org/showpost.php?p=2663042&postcount=10](http://ubuntuforums.org/showpost.php?p=2663042&postcount=10)

A bug Report has been filed:

[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/114595](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/114595)

Rolling back to the previous version of HAL solved the SUSPEND problem.

Just remember NOT to update HAL.

- CH


:guitar:

---

### Post by mrfuzzemz on 2007-05-18
Wow.  That's what it has been all along?  I'll have to give it a whirl.  I'm just curious as to what bug-fixes and features we might be missing out on using the older version?
Also, would anyone happen to know if Ubuntu developers plan to release a new version any time soon with this bug fixed?

Thanks

---

### Post by mrfuzzemz on 2007-05-18
I wanted to update and say that I've been using version 0.5.8.1-4ubuntu12 of hal all along (I'm not subscribed to backports or prereleases).  There must be some other reason for this problem, then.

---

### Post by Immolatus on 2007-05-18
> **mrfuzzemz said:**
> I wanted to update and say that I've been using version 0.5.8.1-4ubuntu12 of hal all along (I'm not subscribed to backports or prereleases).  There must be some other reason for this problem, then.

:confused:same here, plus no restricted drivers.

---

### Post by frogotronic on 2007-05-18
hmmmm........


well, this fixed it for me.

maybe it's a combination of this HAL update and the recent acpi update.

- CH

---

### Post by Immolatus on 2007-05-19
Update: So I just installed fedora c6 again in hopes of chainloading it with feisty (fc6 has a working suspend) however, fedora apear:mad:s also to suffer from the HAL update as the function is no longer in any menu anywhere. 
Moral of the story, it's all about HAL.......grrrrrr.

---

### Post by matteo.collina on 2007-05-20
Hi, 
I have the same problem with an Asus A8JS laptop, with a GeForce Go 7700. I'm using nvidia-glx-new.

I can't suspend (or standby) twice in a row. 

EDIT: 
After a tail -f /var/log/messages after calling suspend it gives me this error:

gnome-power-manager: (matteo) DBUS timed out, but recovering

however if I log out the system magically suspend. So the problem isn't in any driver but in dbus, hal and gnome-power-manager.

Can I help doing some other tests or whatever to fix this?

The bug reported above was about nvidia drivers, it's the case to open a new bug for this?

---

### Post by frogotronic on 2007-05-20
> **matteo.collina said:**
> Hi, 
I have the same problem with an Asus A8JS laptop, with a GeForce Go 7700. I'm using nvidia-glx-new.

I can't suspend (or standby) twice in a row. 

EDIT: 
After a tail -f /var/log/messages after calling suspend it gives me this error:

gnome-power-manager: (matteo) DBUS timed out, but recovering

however if I log out the system magically suspend. So the problem isn't in any driver but in dbus, hal and gnome-power-manager.

Can I help doing some other tests or whatever to fix this?

The bug reported above was about nvidia drivers, it's the case to open a new bug for this?


Try cross-posting this as a bug report in gnome-power-manager mailing list:

[http://www.gnome.org/projects/gnome-power-manager/](http://www.gnome.org/projects/gnome-power-manager/)

[http://bugzilla.gnome.org/](http://bugzilla.gnome.org/)

They're usually really good about patching gpm.

- CH

---

### Post by matteo.collina on 2007-05-21
I've done some more tests.
I can suspend only once from the login screen. It's exactly the same behaviour I got if I was logged in. So it might be HAL that hangs after a first suspend.

I'm quite sure, it's an HAL problem. If I kill HAL (which doesn't stop with a /etc/dbus-1/event.d/20hal stop) and restart it everything works fine.

Can someone else try this?

---

### Post by mrfuzzemz on 2007-08-02
I just wanted to say that with NVidia's latest driver (100.14.11) I've just successfully suspended twice in a row!  I have trouble if I am running any compositing, but with plain old metacity it works perfectly!

---

