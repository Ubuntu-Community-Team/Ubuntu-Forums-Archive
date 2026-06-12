---
title: "Got absolutely no sound after Karmic upgrade with your USB? Solution here..."
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by btbluesky on 2009-10-31
Long story short. Been a linux user for 10 yrs, using ubuntu since Dapper. Also an audio lover, using outboard USB DAC (been working flawlessly in linux w/ USB sound driver)

Upgraded Karmic, read all the upgrade instruction, went through it smoothly. Reboot, all sound don't work, the new "multimedia" setting in the "System Setting" doesn't even list the USB hardware, only onboard sound. Even dmesg listed it as well as alsa aplay and vlc.

Seems like pulseaudio (...again...) is acting up, which I've been dealing with every 6 months now.

After going through dozens of things to get the pulseaudio to at least get some sound out. Gave up and [I]sudo apt-get remove pulseaudio
[/I]
It does remove the meta package ubuntu-desktop, but since it has nothing in it, I think it's fine.

Reboot, now the vlc is playing, mplayer is playing by setting hw=1.0 (or whatever your usb sound device is).

Not saying anything about pulseaudio, there might be alot of scenarios for its usage, plus it might be ubuntu team's fault as well. But when u plug in the most common 16bits USB sound chip in, and cannot be found in System Setting, but in all other apps, someone is at fault.

Also, I'm not an audiophile, but I ABSOLUTELY abhorred by what goes in to the default sound setup in recent releases. Have not look at Fedora or Gentoo (2 of my other favorites), but **WHY IS IT SO HARD TO GIVE USER AN OPTION TO SEND SIGNAL DIRECTLY TO ALSA THEN DEVICE?** (I'll deal w/ the dmix myself...) Is it too much to ask for a shortest path for sound signal.

If you do these crap in network, someone's going fork your code so fast like gentoo in deepblue. But apparently in sound, its the preferred way to add as many layers of things as possible.

---

### Post by Eul_Bofo on 2009-10-31
> **btbluesky said:**
> Long story short. Been a linux user for 10 yrs, using ubuntu since Dapper. Also an audio lover, using outboard USB DAC (been working flawlessly in linux w/ USB sound driver)

Upgraded Karmic, read all the upgrade instruction, went through it smoothly. Reboot, all sound don't work, the new "multimedia" setting in the "System Setting" doesn't even list the USB hardware, only onboard sound. Even dmesg listed it as well as alsa aplay and vlc.

I had the exact same problem, but none of your workarounds seemed to do me any good. Then, trying something else (an Alsa upgrade), I noticed that I was still trying to use the old 9.04 kernel. Problem is, I answered no to the question about "menu.lst upgrade".

So I edited this menu.lst to reflect the kernel changes, and now the sound is back to normal.

I can't guarantee this will work for others, as I tried quite a few things in the mean time.

Hope this can help.

\bye

-- 

Eul_Bofo

---

### Post by btbluesky on 2009-11-01
Did a full fresh install (but w/ home dir attached of course...), it's alittle bit better, the vlc and mplayer works right off.

But pulseaudio still does not detect USB outboard DAC (right click volume icon, preference->hardware)

and of course flash(youtube) has no sound, coz there are no default sound device.

---

### Post by saulysw on 2009-11-01
I absolutely agree with Uel_Boffo.

It seems to me a whole bunch of problems are caused by the seemingly innocent menu.lst changes at the end of the upgrade. At that stage of the upgrade you can sense the end, and in your excitement may not read (or fully understand) the implications of what it is telling you. The safest option appears to keep the old menu.lst file. That's what happened to me, anyway.

This may be limited to those who still use the older version of Grub, not sure. The problem is that it doesn't actually add the new kernel to the boot options, so you boot using the old one. 

Problems I had were --

[LIST]
[*]Boot to a blank screen (just gets past "Waiting for root file system")
[*]No Audio hardware detected. No sound also, obviously.
[*]USB Drives would not mount, claiming "Not Authorized" or something (didn't write down the exact error)
[/LIST]

I could get it to boot (past the black screen) using the older kernel choice in Grub. But you get the feeling it's just hobbling along. I'm assuming you can get it to boot too, somehow, possibly using a recovery option. If you can't do that, well, I don't think I can help you - someone else probably can though.

How can you tell what kernel you are actually running? 

In terminal, run ```
uname -r
```

You want it to say 2.6.31-14-generic. If it doesn't you have the problem I'm trying to describe (probably, badly). The good news is that it's a fairly easy fix! Just add the new options to the menu.lst file yourself, and reboot to a machine that works properly. So, in terminal again --

```
sudo gedit /boot/grub/menu.lst
```

Find the TOP most (and known good to you) bit that starts with "TITLE" and select to just before the next TITLE section. Copy/Paste this above the selected text. Now change the title, kernel and intrd sections to have the new magic numbers, as above, at 2.6.31-14. For example, it probably was from 9.04 and the values on my system were 2.6.28-15. 

I would show you what my menu.lst looks like, but if you are like me you might be tempted to copy/paste it into your file and that would NOT work. You need to copy one of the previous ones on YOUR system. 

Save, reboot, select the new entry in grub, and be proud of fixing your problems, caused by a somewhat misleading upgrade option.

I hope this helps someone!

---

### Post by NEUR0M4NCER on 2009-11-01
This did the trick for me - you're right, those messages during upgrade are a little... lacking in information.

Thanks for the help!

---

### Post by tom3k493 on 2009-11-01
Sorry, am a noob - I think this will help me, but i am unsure of what to change, and what to replace it with ?

---

