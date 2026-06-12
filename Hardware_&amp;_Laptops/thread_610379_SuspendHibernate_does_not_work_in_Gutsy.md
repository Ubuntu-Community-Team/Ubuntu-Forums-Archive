---
title: "Suspend/Hibernate does not work in Gutsy"
date: 2007-11-11
forum: Hardware &amp; Laptops
---

### Post by ZManODS on 2007-11-11
I have an nvidia geforce 6800 card and a dell inspiron 9300. 

When i close my laptop it goes it to supsend mode but whenever i reopen it does not ever resume. The screen looks really weird and fades from black to white kind of and it just sits there. It takes me forever to restart my computer by holding down the power button.

Please help me with this.

p.s. I tried following the instructions from this post but it did not work: [http://ubuntuforums.org/showthread.php?t=589794](http://ubuntuforums.org/showthread.php?t=589794)

Let me know if you need anymore information.

---

### Post by ZManODS on 2007-11-11
I have an nvidia geforce 6800 card and a dell inspiron 9300. 

When i close my laptop it goes it to supsend mode but whenever i reopen it does not ever resume. The screen looks really weird and fades from black to white kind of and it just sits there. It takes me forever to restart my computer by holding down the power button.

Please help me with this.

p.s. I tried following the instructions from this post but it did not work: [http://ubuntuforums.org/showthread.php?t=589794](http://ubuntuforums.org/showthread.php?t=589794)

Let me know if you need anymore information.

---

### Post by ZManODS on 2007-11-12
Anyone?

---

### Post by ZManODS on 2007-11-12
After suspending my computer will not resume! Im running a Dell Insipiron 9300.

Is there anything i can do?

---

### Post by Don9307 on 2007-11-12
I'm running Gusty Gibbon on a Compaq Presario V5000 laptop myself and I have the same issue.  Not at all sure how to fix the issue.

---

### Post by ZManODS on 2007-11-14
?????????????

---

### Post by ZManODS on 2007-11-14
Resume/Suspend does not work on my Dell Inspirion 9300 and no one seems to know why. I'll get 100 page views but no one knows what the f is the problem!

Any ideas!!!!!

---

### Post by jflaker on 2007-11-14
please tell us more details.

Errors?  It JUST doesn't suspend........etc

Thanks

---

### Post by overdrank on 2007-11-14
> **ZManODS said:**
> Resume/Suspend does not work on my Dell Inspirion 9300 and no one seems to know why. I'll get 100 page views but no one knows what the f is the problem!

Any ideas!!!!!

If that is all it takes you to stop using ubuntu then good luck in whatever OS you choose.

---

### Post by romeyde on 2007-11-14
There are actually lots of threads on this issue.   Also lots of suggestions on what to try.   No one seems to be having any luck actually fixing the issue.  Also, there doesn't seem to be any common factors hardware wise with the people having issues, at least none found yet.

Guessing he is having the same issue I have.   The PC will suspend just fine, but then it won't wake back up.   The HD light will show a bit of activity then just shuts back down.  Screen stays dark.  I end up having completely restart the PC to get it back.   PC suspends just fine in XP.

This issue won't get me to go back to XP but it is annoying and the only real problem I continue to have with Gutsy.

---

### Post by ricanelite on 2007-11-14
yeah because my Gatway Desktop does not do it either but i so far i have been loving it. Even though I have been a member in the forums for a long time. But a week ago I finally made the move and I'm sticking it to it and love it.

---

### Post by mikewhatever on 2007-11-14
Not every forum member is an expert with linux. Have you considered it possible you have a problem 100 people do not know the solution to? What's the deal with goodbye threads anyway?

---

### Post by Inxsible on 2007-11-14
> **mikewhatever said:**
> Not every forum member is an expert with linux. Have you considered it possible you have a problem 100 people do not know the solution to? What's the deal with goodbye threads anyway?I have seen a couple of those today.

But yeah, is that all it takes for you to switch? Having said that, Suspend and hibernate didnt work for me in Feisty -32 bit, when i switched to Gutsy-64bit OS, everything worked out of the box.

Good Luck with whatever OS you choose.

---

### Post by barney385 on 2007-11-14
These types of threads seem to be rehearsed...or is it just me?

Oh, good luck with your new XP spyware/OS

---

### Post by anemptygun on 2007-11-14
lol, if you don't help me i'm going back to windoze!!! arg! ;)

---

### Post by dpar on 2007-11-14
I'd quit too, but my dog at the Windows cd,got a virus, and died:(

---

### Post by erfahren on 2007-11-14
I'm having trouble with my suspend/resume with Gutsy as well, and it worked with Feisty. Having an ATI video card using the proprietary fglrx driver I've grown used to the odd issues. I know they'll get worked out eventually and either a fix or a workaround will come around.

What I don't understand is why those who are trying to migrate to Linux from Windows consider it an "one-or-the-other" scenario. What's wrong with dual-booting? 

I don't feel any shame for still having Windows. It's kind of difficult to give "tech support" over the phone to friends/relatives who use Windows when you have no idea what they're lookng at.

Give it time ZManODS.

---

### Post by ZManODS on 2007-11-14
Ha.. I actually dual boot but it seems like threads like those get the most answers :)

Looks like it worked :lolflag:

---

### Post by awong on 2007-11-14
having this issue on my thinkpad, it was working on gusty for a while too, not sure how it broke,  but I'll wait it out, since everything else wors

---

### Post by erfahren on 2007-11-15
> **ZManODS said:**
> Ha.. I actually dual boot but it seems like threads like those get the most answers :)
yeah, they're also annoying

try not to forget that you're using a free open-source OS, and those who try to help here do so on their own time.

noticed you changed the thread title.

one hint (I'm not saying this to be a jerk, just for your info): sometimes you can get better/different results searching the forums using Google as opposed to using the forum's own search tool.
for example use:
gutsy 7.10 nvidia suspend resume site:ubuntuforums.org

---

### Post by ZManODS on 2007-11-15
Thanks.

Fixed: [https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend)

---

### Post by romeyde on 2007-11-16
> **ZManODS said:**
> Thanks.

Fixed: [https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend)

"Note: enabling TwinView breaks suspend-to-ram (..."

I have a nvidia card but on a PC and don't use TwinView...  Any idea if this fix is really just limited to TwinView users?   My suspend to ram hasn't been broken by something, it just has never worked in the first place.

---

### Post by slanbarn on 2007-11-16
Hi, yeah I had problems with hibernate/suspend too while using fglrx ati driver, but changing it to "radeon"(the open-source atri graphics driver), it "just works". Although i have other problems related to my lid-switch, but the function of hibernate is ok :)

---

### Post by erfahren on 2007-11-16
> **slanbarn said:**
> Hi, yeah I had problems with hibernate/suspend too while using fglrx ati driver, but changing it to "radeon"(the open-source atri graphics driver), it "just works". Although i have other problems related to my lid-switch, but the function of hibernate is ok :)
the dektop effects (Compiz Fusion) don't work with it though, do they?

---

### Post by DanaG on 2007-11-16
Here's something useful: dig around in /etc/default/acpi-support for video-related options.  Here's how I have mine set:  

```

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=false # was true

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
# POST_VIDEO=true
POST_VIDEO=false # was true

# Save and restore video state?
SAVE_VIDEO_PCI_STATE=true # was false

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=false # was true
```


EDIT: note that this is not the entire file; it's just what I've changed.

---

### Post by kay_rus on 2007-11-16
> **DanaG said:**
> Here's something useful: dig around in /etc/default/acpi-support for video-related options.  Here's how I have mine set:  


EDIT: note that this is not the entire file; it's just what I've changed.

you rocks! your solution did the trick for my acer 6292! thank you:)

---

### Post by romeyde on 2007-11-17
> **DanaG said:**
> Here's something useful: dig around in /etc/default/acpi-support for video-related options.  Here's how I have mine set:  



woohoo, worked for me to.    thanks a ton.   that was my last issue with gutsy.   still won't wake up via keyboard or mouse, but just had to hit the power button to wake it back up.  i can live with that.

thanks again

---

### Post by romeyde on 2007-11-18
well it worked the 1st time but woke up this morning and had issues again.  argh.  kinda sort of woke up but just had the mouse cursor on the screen and the screen was just blank with the background color.   had to reset.
i have faith that someone will patch/fix it soon since it seems to be such a wide spread issue.

---

### Post by Jamie Jackson on 2007-11-20
> **DanaG said:**
> Here's something useful: dig around in /etc/default/acpi-support for video-related options.  Here's how I have mine set:  

```

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=false # was true

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
# POST_VIDEO=true
POST_VIDEO=false # was true

# Save and restore video state?
SAVE_VIDEO_PCI_STATE=true # was false

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=false # was true
```


EDIT: note that this is not the entire file; it's just what I've changed.

Works for me on a Dell D620 with an integrated Intel card. 

Since upgrading to Gutsy, but before editing this file, uspend took forever (or froze Gnome) and wouldn't wake back up. Two minutes after editing, I've successfully suspended and awakened.

---

### Post by Auslegung on 2007-12-03
Only problem is when I try to edit that document it says:

"You do not have the permissions necessary to save the file.
Please check that you typed the location correctly and try again."

I don't know how to give myself permission (temporarily of course) to edit the file.  I tried running a sudo in my terminal just so it'd prompt me to enter my pw, but it didn't work.  What do I do?

---

### Post by erfahren on 2007-12-03
> **Auslegung said:**
> Only problem is when I try to edit that document it says:

"You do not have the permissions necessary to save the file.
Please check that you typed the location correctly and try again."

I don't know how to give myself permission (temporarily of course) to edit the file.  I tried running a sudo in my terminal just so it'd prompt me to enter my pw, but it didn't work.  What do I do?
```

gksudo gedit /etc/default/acpi-support

```
note: "sudo" would work as well there but gksudo is really supposed to be used with GUI apps (gedit is a GUI based text editor)

---

### Post by Languid on 2007-12-08
Editing the /etc/defaults/acpi-support file as suggested worked perfectly for me, too.  Thanks a bunch! :)

---

### Post by mwacky on 2007-12-16
> **DanaG said:**
> Here's something useful: dig around in /etc/default/acpi-support for video-related options.  Here's how I have mine set:  

```

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=false # was true

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
# POST_VIDEO=true
POST_VIDEO=false # was true

# Save and restore video state?
SAVE_VIDEO_PCI_STATE=true # was false

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=false # was true
```


EDIT: note that this is not the entire file; it's just what I've changed.

What hardware is this on?  ATI/Nvidia?

---

### Post by scottym on 2007-12-29
Code did not work on my G40 Thinkpad.

---

