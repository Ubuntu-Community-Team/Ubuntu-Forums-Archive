---
title: "Power Failure killed wireless connections, made USB sound fuzzy..."
date: 2007-12-30
forum: Hardware &amp; Laptops
---

### Post by stir-crazy on 2007-12-30
I had the battery out of my laptop, was positioning a new fan/usb hub, when I accidently pulled the power cord out, turning off the laptop.

I connected everything, things seemed to boot up fine, except now I have the following problems:

[LIST]
[*]Wireless doesn't work anymore (the only connection I have at home, I'm at work now).  The restricted drivers setting was still checked; I unchecked this and tried to restablish functionality, but now it's asking for the location of the firmware.  I downloaded what I think I need to my flash drive, and will try this tonight.

[*]The sound on my USB speakers, Yamaha YST-MS55D's sound terrible!  Like the speakers are blown, just very choppy, fuzzy sound.  Using the ALSA engines.  Not sure what to do to get this working properly.

[*]Get errors occasionally when rebooting.  FSCK runs, finds errors.  I've run fsck from terminal as root (autofix), run it from recovery mode (again, autofix) but still get that errors have been found.  What should I do here?
[/LIST]

Sigh.  :(

I was so excited about Kubuntu, was so nice to finally have a GNU/Linux distro that I could have (near) immediate functionality while still learning the ropes.  If I can learn how to fix this, I will most probably swear off MS forever.  Please help me do this!  Thanks in advance!

---

### Post by woodcarver on 2007-12-31
It sounds to me like you may have "fried" part of your motherboard, or a card attatched to it.
Boot into the BIOS and see if there are any errors or un-detected hardware.
What is the manufacturer? Usually pressing the delete key during the post will get you to "setup".

---

### Post by stir-crazy on 2007-12-31
BIOS recognizes everything, indicates no problems.  Wireless is enabled, etc.  Kubuntu recognizes everything, I just don't seem to get the wireless signal.

I since plugged my laptop into our LAN here at the office, which enabled the restricted driver to locate the firmware for my card; still, no signal located, though I know there are many around me.

Since I have a relatively fresh install, I'm just going to wipe the slate clean and reinstall the whole system.  Frustrating though.:mad:


EDIT:  Grrrr!  Re-installed, connected to LAN, which is what magically did the trick the first time I installed, everything's been detected, drivers are loaded etc, just not seeing any networks.  I KNOW I have several around me, but don't see one.  iwlist scan returns no scan results.  Could the antenna or some other component have been fried when I lost power?  Not sure what I need to fix to get results here.

---

### Post by woodcarver on 2008-01-03
Since you are at work, do you have an IT dept? If so maybe they can check your card and see if it is indeed bad. Or if you have access to a laptop with XP or Vista, try plugging it into it and have windows do a hardware check.

---

### Post by stir-crazy on 2008-01-03
A bit of an update, that reinstallation might or might not have been necessary.  I now can access WiFi, but only through my USB dish adapter; though the system recognizes my internal card, and it seems to be working, it doesn't detect any signals.  Think I fried the antenna on that one?  The USB dish didn't work until after the reinstall though.

As for the USB, it's still sounding off, though the USB ports seem to work fine for other devices.  If I plug the same speakers into my headphone jack, they sound great.  I'm guessing it's some configuration issue that I'm overlooking.  I had them working before, so I'm not really clear on what I'm not doing, but the current arrangement is "ok".

No IT at work at all, we're tiny, and I'm probably the "techiest" of the bunch.

---

### Post by Al42 on 2008-01-03
> **stir-crazy said:**
> Think I fried the antenna on that one?Unless you heard an explosion, probably not.  The antenna on most [all?] wireless cards is just wire, so there's nothing to blow.  You could have blown the front end [radio] though.  The card would look fine from the computer side, but it wouldn't hear anything.

---

