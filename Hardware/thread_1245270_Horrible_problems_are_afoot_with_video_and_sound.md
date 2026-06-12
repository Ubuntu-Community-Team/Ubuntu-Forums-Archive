---
title: "Horrible problems are afoot with video and sound"
date: 2009-08-20
forum: Hardware
---

### Post by Cadeyrn on 2009-08-20
Suddenly I can't use the Linux half of my computer at all for two reasons. And don't suggest a no dual-booting solution. [URL="http://ubuntuforums.org/showthread.php?t=1218499"]This topic] contains a discussion of why I have to dual-boot. Anyway:

1. Compiz will randomly turn itself off, and I use the tray icon to reload it. But soon after that the display will die, the screen will turn black, I'll get three lines of Ubuntu telling me it's restarting the display, and I'm in the login screen. This used to happen once in a blue moon, but now this usually happens within 5 minutes of using Ubuntu, rendering it unusable because I can't do anything before the display dies and logs me out. But it's definitely true that one or some of the following things speed this process up to take about 5 seconds:
-Having a window open
-Having a maximized (but not fullscreen) window open
-Having Firefox open
-Having Syaptic open

2. There is something seriously wrong with my sound card. Every time I ask for support from the Ubuntu forums or System76 with my god damn sound card I'm ignored. I don't even get politely told that no one knows how to fix it. Well, this time someone better reply, because I need help!
My sound card originally worked great. Then it used to just block itself out of HAL and whatever Windows uses to load hardware on the first boot of the day, but a reboot would fix that. Might I add no changes were made to my system to make it act like this. Nor were any made to cause this: My sound card still works fine, but now it blocks itself out of Windows and Linux, every single boot. I have no sound because this sound card is refusing to let my operating systems touch it. And I do have the proper driver installed, on both OSes.

On a side note, an extremely annoying bug I've dealt with for months is that one time I added Tomboy Notes to the Startup Applications list. Soon after I removed it. But ever since, it still launches at startup, and it's still not in the list.

So, basically, until I get these problems fixed, I'm locked out of all my documents (don't suggest an ext reader because my Linux partition is on Ext4), I'm stuck with vanilla Google Chrome which, while OK, is horrible compared to my customized Firefox, I have NO SOUND, and worst of all, I have to deal with the horrible, crappy, half-*** kernel that made me leave Windows that I want to use just for games and not my whole computer usage.

My technical details:
-My driver in both OSes for my NVidia Geforce G105M is the 180.44 driver.
-I don't know what driver Linux uses for my sound card, but I do know that it's been called by Linux an Intel High Definition Audio card, and been called by ALSA a Realtek ALC662. Whatever it is, there is no driver for "Intel High Definition Audio" besides a not-working one by Microsoft, and Realtek's generic driver worked just fine in Windows for it.

---

### Post by Cadeyrn on 2009-08-21
Update: the System76 support e-mailing has fixed most of this. The problems I have now are, my display crashes when I use Emerald on a maximized window, and the sound card isn't recognized on Linux's first boot of the day. I still want to fix these problems because I don't like having to boot Linux twice every morning and Emerald is pure awesome.

---

### Post by Cadeyrn on 2009-08-22
This is so irriratating... My sound card hates me. It refuses to be recognized on either system in midday and there's nothing I can do about it. Why am I ignored EVERY time I make a topic here!!! Whenever I find a topic that might help me while Google searching, in Ubuntu forums, it got a reply within hours. I always end up waiting weeks. Why does no one ever help me!!!!!

---

### Post by Cadeyrn on 2009-08-23
AHA! It turns out, Ubuntu and the Systm76 Driver program both put a Realtek driver into ALSA by default, and I had a Realtek driver installed in Windows. But my real sound card in Windows in the Device Manager was listed as unused and un-drivered. I told XP to automatically install a driver for me and I don't know if that fixed it yet, but if it did fix it, obvious the Realtek driver is not right for my sound card on any operating system, which means I will need to know the exact model and vendor of the Pangolin Performance laptop's sound card and I'll need a guide for installing a driver for that sound card into whatever part of Linux handles sound drivers (ALSA, right?). For now, in Linux, I'll try installing an NVidia sound driver because that's the one that Windows automatically gave my sound card.

I'm still pissed off that this is yet *another* problem with my computer I've had that I solved all by myself while a regularly bumped help topic remained in the forum for days.

---

### Post by Cadeyrn on 2009-08-23
Case closed.

I can't believe I spent all this time trying to track down the problem when all I had to do was think...

My computer BIOS originally had the boot order set to boot Realtek devices before my hard drive. Something changed that, and for some reason my computer cannot use the sound properly when the hard drive boots before the sound card. I went into the BIOS and changed it back, and now it works.

P.S. I also fixed the Tomboy problem. Turns out it was because of the common Jaunty glitch where unchecking the remember session box doesn't really uncheck it.

---

