---
title: "Sleep, suspend, and hibernation on IBM ThinkPad T22"
date: 2005-08-02
forum: Hardware &amp; Laptops
---

### Post by timelord726 on 2005-08-02
Hi everyone!  I just got a new laptop, an IBM ThinkPad T22, and I was eager to install Ubuntu on it and have now done so.  I even got my Broadcom wireless card working so I'm good to go with Linux on the go.

However, I am wondering about sleep, suspend, and hibernation.  My laptop has three different modes -- Fn+F3 turns off the monitor but leaves the system running at full power, Fn+F4 puts the system into suspend mode, and Fn+F12 puts the system into hibernation.  I'm not too picky about the keys working or the lid closing or anything, but I am curious as to how I can make all of these functions work like they should in Ubuntu.

As I said in the subject, my laptop is an IBM ThinkPad T22.

Thanks for any assistance offered!

---

### Post by shrimphead on 2005-08-02
I managed to get these working on my IBM THinkpad X21 (P3700, 256Mb, 20Gb) by simply adding

```
acpi=off apm=on
```

to the kernel boot string in grub's menu.lst file

hope it works for you and welcome to Ubuntu!  :razz:

---

### Post by timelord726 on 2005-08-02
[QUOTE=shrimphead]I managed to get these working on my IBM THinkpad X21 (P3700, 256Mb, 20Gb) by simply adding

```
acpi=off apm=on
```

to the kernel boot string in grub's menu.lst file

hope it works for you and welcome to Ubuntu!  :razz:[/QUOTE]
 Thanks for the tip!  I just added it to my menu.lst and I'll let you know how it works.

How does the actual "entering those modes" work?  Just press the Fn key combinations?  Or some kind of menu?

---

### Post by Lambert on 2005-08-02
[QUOTE=timelord726]Thanks for the tip!  I just added it to my menu.lst and I'll let you know how it works.

How does the actual "entering those modes" work?  Just press the Fn key combinations?  Or some kind of menu?[/QUOTE]
 I'm fairly new to linux also using an ibm a31. The linux kernel 2.6.10 and after has an ibm-acpi function builtin so these functions using the fn key should work out of the box on ubuntu.

fn-f3 just turns off monitor
fn-f4 suspends the system and should save everything to ram so when you restart it reads ram and returns to the state you were in (I've found this buggy though)
fn-f12 is the same as f4 except it saves to the hard drive (usually the swap partition if that's how it's configured) and it just reads and restarts from that. this one works best for me.

For more on linux and a thinkpad go to [www.thinkwiki.org](www.thinkwiki.org). It's a wiki dediacated for thinkpad users running linux.

---

### Post by timelord726 on 2005-09-05
Thanks for all the help, guys.  I've experimented with recompiling the kernel but that didn't really get me anywhere.  So far, the keys don't actually help me that much.  The only one that works at all, and even that with limited success, is hibernation.  Does anyone have some tips to offer about this?

Thanks!

---

### Post by thin_king on 2005-09-06
I have a T23 and both standby and suspend work with the key combos Fn + F3/F4. I never bother with hibernation, I don't think it's useful. I can leave this T23 in suspend for a couple days on battery power and long as needed on AC. That's enough for me. 

The only thing I did was make sure on install I had these in the boot string: 

noacpi acpi=off apm=on 

Also if you have a USB mouse it might freeze coming back from suspend. If it does, a PS/2 connector-converter (usually included) will solve the problem.

---

### Post by timelord726 on 2005-09-06
[QUOTE=thin_king]I have a T23 and both standby and suspend work with the key combos Fn + F3/F4. I never bother with hibernation, I don't think it's useful. I can leave this T23 in suspend for a couple days on battery power and long as needed on AC. That's enough for me. 

The only thing I did was make sure on install I had these in the boot string: 

noacpi acpi=off apm=on 

Also if you have a USB mouse it might freeze coming back from suspend. If it does, a PS/2 connector-converter (usually included) will solve the problem.[/QUOTE]
 Thank you, thin_king, that helps a lot.  However, Fn+F12 seems to do nothing at all (but perhaps a System > Log Out > Hibernate will do the trick), and Fn+F4 does not seem to suspend, but instead does the same thing as Fn+F3, which is turn off the monitor.  Is that normal or is something not configured correctly?

---

### Post by thin_king on 2005-09-07
Fn+F12 doesn't do anything but yeah, System -> Log Out -> Hibernate the Computer works. It shuts it down completely. You have to press the power button, choose OS (I have Debian also) and login with your password to get back.

Fn+F4 should suspend, not just standby like F3. I use suspend all the time. When you do Fn+F4 it should beep once, the crescent moon LED blinks and comes on to show it's in suspend mode and the laptop quickly cools down. Press Fn to get back and it beeps once, then twice quickly when the monitor comes back on. That's how it works on mine.

So something probably isn't configured right yet on yours.

---

### Post by timelord726 on 2005-09-07
[QUOTE=thin_king]Fn+F12 doesn't do anything but yeah, System -> Log Out -> Hibernate the Computer works. It shuts it down completely. You have to press the power button, choose OS (I have Debian also) and login with your password to get back.[/QUOTE]
Okay, cool, thanks.

[QUOTE=thin_king] Fn+F4 should suspend, not just standby like F3. I use suspend all the time. When you do Fn+F4 it should beep once, the crescent moon LED blinks and comes on to show it's in suspend mode and the laptop quickly cools down. Press Fn to get back and it beeps once, then twice quickly when the monitor comes back on. That's how it works on mine.[/QUOTE]
That's how I assumed it was supposed to work, I'm used to the little crescent moon.  :)  It doesn't do that on mine, though, I waited for the crescent moon to come on and it never did, just turned the monitor off and looked a lot like standby.

[QUOTE=thin_king] So something probably isn't configured right yet on yours.[/QUOTE]
Any ideas?

Thanks very much for the help!

---

### Post by thin_king on 2005-09-09
Only a few ideas since mine works with just those boot parameters. Only thing I can think of is throw out some questions, maybe spot a difference in our systems. Might not lead to anything. But we can go through them at least. 

Are you running on AC power or battery normally?

Does the panel battery monitor work correctly?

Just to make sure, are apmd amd libapmd packages installed?
Do you have an apmd in /usr/sbin and /usr/share directories? 

What do you have in your /etc/apm directory, especially in the supend.d folder?

When you do an Fn+F4 what shows in your syslog? "apmd(the process #) Suspending now" is what mine shows.

With F4 is it actually standby or suspend but just no moon? You come out of standby just moving the mouse, but suspend needs Fn to come back.

With F4 does it make any beeps at all, like maybe 4 strange beeps? 
Does it do the same plugged in and on battery?

Did you try hibernate? Did it work? 
Do you have a "sleep" binary in your /bin directory?

Are you running in laptop mode?

Do you have power management enabled in screensaver preferences?

That's all I can think of for now. 

Did you try this? Download one of the Ubuntu LiveCDs, like Gnoppix, Gnome 2.12 or the Ubuntu Breezy preview and put those boot parameters in, probably "live acpi=off noacpi apm=on". See if standby, suspend and hibernation work then.  

If they do then that might mean you had to put those boot parameters in when installing.

---

### Post by timelord726 on 2005-09-10
Sorry for the delay, and thank you for continuing to help me!  I will try to answer your questions as best I can.

[QUOTE=thin_king]Are you running on AC power or battery normally?
**Most of the time, I just use AC power.**

Does the panel battery monitor work correctly?
**I haven't done any in-depth testing, but it seems to work well.**

Just to make sure, are apmd amd libapmd packages installed?
Do you have an apmd in /usr/sbin and /usr/share directories? 
[b]apmd is already the newest version.
E: Couldn't find package libapmd

I have apmd in /usr/sbin but all I have is apmd_proxy.conf in /usr/share.
[/b] 
What do you have in your /etc/apm directory, especially in the supend.d folder?
[b]apmd_proxy  event.d  other.d  resume.d  scripts.d  suspend.d

In suspend.d:
80alsa  99hwclock[/b]

When you do an Fn+F4 what shows in your syslog? "apmd(the process #) Suspending now" is what mine shows.
**It doesn't actually appear that *anything* shows up in there.  Is "auth.log" the right place to be looking?**

With F4 is it actually standby or suspend but just no moon? You come out of standby just moving the mouse, but suspend needs Fn to come back.
**Moving the mouse is what brings it back, so it's standby and not suspend.**

With F4 does it make any beeps at all, like maybe 4 strange beeps? 
**I just tested it and it *does* make beeps -- I never noticed this before. When pressing Fn+F4, it does a high beep then a low beep in rapid succession, like BEEP-boop. When you move the mouse to wake it up, it does a single, short beep. This does not happen with standby (Fn+F3), only suspend (Fn+F4) even though it looks the same.**

Does it do the same plugged in and on battery?
**Yes, it appears to do the same thing both ways.**

Did you try hibernate? Did it work? 
[b]I just tried hibernation and it doesn't work correctly. The screen goes black and the computer becomes unresponsive and seems to stop working. I had to turn it off and back on to bring it back.

[/b] Do you have a "sleep" binary in your /bin directory?
**Yes, I do.**

Are you running in laptop mode?
**Uh, I would assume so.  How can I be sure?**

Do you have power management enabled in screensaver preferences?
[b]Yes, apparently I do.  Standby = 30 minutes, suspend = 45 minutes, off = 60 minutes.

[/b]Did you try this? Download one of the Ubuntu LiveCDs, like Gnoppix, Gnome 2.12 or the Ubuntu Breezy preview and put those boot parameters in, probably "live acpi=off noacpi apm=on". See if standby, suspend and hibernation work then. 

If they do then that might mean you had to put those boot parameters in when installing.
**I'll give this a shot a little later on.**[/QUOTE]
Thanks very much for your help!  I hope we can get this sorted together!

**UPDATE:** My laptop is exhibiting some ***very*** strange behavior lately. I upgraded from Hoary to Breezy and the upgrade went flawlessly -- everything worked perfectly immediately after the upgrade. However, I just noticed that I had forgotten to re-add the "noacpi acpi=off apm=on" to the GRUB menu. I did that just now, and ever since, my laptop has successfully gone into suspend mode *without me telling it to* (Fn+F4 still does not produce that result), as well as sleep mode, again without my instruction. In two extreme cases, the machine powered down completely without any involvement from me -- I was editing this very post and the machine turned off in the middle of it! I'm rather worried about this behavior now...

Thanks again for helping me, and I hope we can work this out!

---

### Post by thin_king on 2005-09-10
Uh-oh. You did the one thing that will keep me from helping you now. With Breezy there's no way to know what's going on. Breezy is a month away from release and is still beta. Even with my Debian experience I wouldn't upgrade before official release, for exactly what you're experiencing now.

Wish I could be more optimistic but you'll probably need to reinstall (hopefully you have a persistant home) or wait a month and hope Breezy gets sorted in a way that will maybe fix your system. At least you know your laptop will suspend now, just not when you want!

Too bad because there were clues in your answers, like missing files and the four strange beeps. I've heard those before. "Laptop-mode" is a special protocol for laptops. It's off by default. I enabled mine "sudo laptop-mode start". I don't know if it would make a difference here.    

But now with Breezy all bets are off, sorry. Hope you understand.

What I recommend is a Hoary reinstall with the boot parameters. You might try Kubuntu instead of Ubuntu. KDE has special "IBM Thinkpad Laptop" and "APM Config" GUI interfaces. You can try the LiveCD first to see if it works. Remember the boot parameters "live noacpi acpi=off apm=on. I just tried the Kubuntu Breezy LiveCD (a LiveCD is as far as I go into betas, for good reason as you see now) and it works.

Hopefully a fresh Hoary install will work with those parameters without any other trouble. Good luck.

---

### Post by timelord726 on 2005-09-10
I think I'll just deal with the situation as I have it right now. I can just shut down and bring it back up for the time being instead of suspend or hibernation. It's just that my installation worked so perfectly immediately after upgrading and it would be a shame to lose it all now only to downgrade to an operating system I'll only end up upgrading again in a month anyway.

Thank you very much for the help!  Talk to you in a month perhaps?  ;-)

---

### Post by timelord726 on 2005-09-11
An update for anyone interested.  I switched to laptop mode in Breezy.  I don't know whether or not it's related, but the problems seem to have stopped and Fn+F4 has begun working *on battery power only*.  Not the absolute best, but very very good.  :)

---

