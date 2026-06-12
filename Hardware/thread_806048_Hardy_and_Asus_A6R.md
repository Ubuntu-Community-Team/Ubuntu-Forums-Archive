---
title: "Hardy and Asus A6R"
date: 2008-05-24
forum: Hardware
---

### Post by alih on 2008-05-24
Since old Asus A6R threads ([here]("http://ubuntuforums.org/showthread.php?t=251248") and [here]("http://ubuntuforums.org/showthread.php?t=205263")) are 2 years old, I decided to start a new one.

Here is the summary of my current state:

Worked out of the box: wireless LAN (well, card-specific, I know), card reader, special keys like Fn+F1, Fn+F2
Worked after some effort: DVD playback, sound playback, 3D acceleration
Still doesn't work for me: hibernate (but there's hope),  suspend, microphone

USB freezes were cured (hopefully) by:
 1) updating to the [latest BIOS from ASUS]("http://support.asus.com/download/download_item.aspx?product=3&model=A6R");
 2) setting DVD's DMA mode to SWDMA0 in BIOS.

I found this laptop to be affected by the controversial [Load_Cycle_Count issue]("http://ubuntuforums.org/showthread.php?t=805570") (~140 cycles/hour). Applied the ["ugly fix"]("http://ubuntuforums.org/showpost.php?p=5031046&postcount=3").

*Video Playback*
By default, Ubuntu Hardy disabled DMA for the DVD drive. Have a look at [this bug]("https://bugs.launchpad.net/ubuntu/+bug/175022") if your DVDs are playing too slow.

*Graphics card*
Works for me with fglrx; I don't remember exactly what I did but have a look [here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI").

*Sound Playback*
In alsamixer, disable external amplifier and set downmix 6->2. Somebody also recommended blacklisting snd_ixp_modem if you're not using it, but it works for me either way.

*Hibernation*
TuxOnIce worked in another distro (Vector) almost out of the box, so I have a good feeling about it. Have to recompile the kernel though.

That's all I know so far. If you can make this laptop friendlier, please share your knowledge!

---

### Post by jakupl on 2009-04-28
My microphone works in skype, but nowhere else.


Just for the record. If ubuntu absolutely refuses to boot, and you only ever see a blank screen, then you should add hpet=disable to the boot parameters, or update the bios.

---

