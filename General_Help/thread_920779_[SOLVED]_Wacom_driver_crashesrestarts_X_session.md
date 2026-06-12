---
title: "[SOLVED] Wacom driver crashes/restarts X session"
date: 2008-09-15
forum: General Help
---

### Post by Dan_Dranath999 on 2008-09-15
I've been using LinuxWacom driver since Feisty and Gutsy, without any problems or crashes...(0.7.9-4 for Feisty and 0.8.0-3 for Gutsy)

But it seems that both wacom drivers, stable 0.8.0-3 and development 0.8.1-4 make Hardy unstable. 

X will crash every time a beep sound occurs, every time backspace key is pressed in terminal when there's no text. Or in firefox, when the find-feature fails. (and sometimes when trying to close a program, like ZynAddSubFX for me)




All this other posts are related, but none came with a solution (including the first which is mine)

[http://ubuntuforums.org/showthread.php?t=893600]("http://ubuntuforums.org/showthread.php?t=893600")

[http://ubuntuforums.org/showthread.php?t=813214]("http://ubuntuforums.org/showthread.php?t=813214")

[http://ubuntuforums.org/showthread.php?t=830164]("http://ubuntuforums.org/showthread.php?t=830164")

[http://ubuntuforums.org/showthread.php?t=817290]("http://ubuntuforums.org/showthread.php?t=817290")

[http://ubuntuforums.org/showthread.php?t=806889]("http://ubuntuforums.org/showthread.php?t=806889")

---

### Post by Dan_Dranath999 on 2008-09-16
Anybody else has this problem?

---

### Post by Dan_Dranath999 on 2008-09-18
bump

---

### Post by Crystal Red on 2008-09-20
Yeah, I got the same issues.

As long as the Wacom Drivers for my Bamboo One are installed (as per this [Tutorial]("http://ubuntuforums.org/showthread.php?t=765915")), some actions will 'crash' my session back to the login.

- pressing Backspace in the Terminal when there is nothing to delete
- browsing man pages all the way down, pressing down at the end
- doing a Ctrl+F pagesearch in Firefox without result
- new inbox mails in Evolution (but I somehow disabled the sound for that, and the crashs stopped for Evolution)


Mind you, I'm almost totally new to Linux, still learning lots.
I mainly do office and cgi work on this machine anyway, so no much use for multimedia sound - I managed to uninstall everything concerning PulseAudio, but that didn't help solve the problem.

---

### Post by Dan_Dranath999 on 2008-09-23
Exactly. I 've been able to disable the sound for firefox pagesearch, so that takes care of that one.

But the Terminal crashes, and the ZynAddSubFX not being able to close itself, persists.


I'm thinking i should write an email directly to the guys at linuxwacom.

---

### Post by Skopar on 2008-09-27
Hello,

As long as problem is not solved upstream, following workaround works for me:

Switch off system bell in System -> Preferences -> Sound, last tab
Switch off system bell in Terminal -> Edit -> Current Profile -> General (disable Terminal Bell and restart Terminal).

After those steps (and disabling system bell in Firefox) everything should work okay (at least worked for me)

---

### Post by Dan_Dranath999 on 2008-09-30
Yup, that made the crashes stop. (it was the system bell. I assume Something going on with the new sound implementation on Hardy)

But i uninstalled** ZynAddSubFX** before this. So i don't know if that still crashes.

---

### Post by Crystal Red on 2008-10-20
Today I made a fresh install of Hardy and noticed something.

Again I followed the guide to install my Wacom Bamboo One, and after Step 19 (Rebooting) the tablet worked and the beep-crashes where back, as expected.


Then I got an idea. I went again to the directory where I compiled everything and did a 'sudo make uninstall'. Then I rebooted: The cursor still followed the pen, but clicks did not work. The beep-crashes where already gone at that point.

Then I used Synaptic to uninstall and directly reinstall the package "xserver-xorg-input-wacom". After another reboot, an ideal situation appeared:
The tablet works, clicks, pressure sensitivity, everything. And beeps don't crash me anymore.


I don't know what I actually did by doing that stuff, if I messed up something else, or if it will work for anybody else. I just wanted to share that experience.

---

### Post by DirtDawg on 2008-10-28
For anyone wondering, to turn off the offending Firefox sound enter 'about:config' into your address bar, then enter 'typeahead' into the filter bar and change 'accessibility.typeaheadfind.enablesound' to False. Restart Firefox.

Thanks for the great thread, this solution worked perfectly.

---

### Post by Dan_Dranath999 on 2008-10-29
> **Crystal Red said:**
> 
Then I used Synaptic to uninstall and directly reinstall the package "xserver-xorg-input-wacom". After another reboot, an ideal situation appeared:
The tablet works, clicks, pressure sensitivity, everything. And beeps don't crash me anymore.



So maybe i should try the driver in the Hardy repositories (7.x i think) instead of compiling the 8.x (downloaded from linuxwacom website)

There shouldn't be any significant differences: I used to compile the 7.x driver back when i had Feisty (and the wacom driver in the repositories didn't support the Bamboo Series) 

good tip!

---

### Post by DirtDawg on 2008-10-30
> **Dan_Dranath999 said:**
> So maybe i should try the driver in the Hardy repositories (7.x i think) instead of compiling the 8.x (downloaded from linuxwacom website)

There shouldn't be any significant differences: I used to compile the 7.x driver back when i had Feisty (and the wacom driver in the repositories didn't support the Bamboo Series) 

good tip!

I can also confirm that using the older driver seems to solve the problem. Thanks again!

---

### Post by griph on 2008-11-08
Try removing/commenting out input devices your wacom doesn't have in xorg.conf. For bamboo 1 removing "cursor", "eraser" and "pad" devices (leaving only "stylus") stops X crashes (linuxwacom 0.8.1-6). Look [here]("http://sourceforge.net/tracker2/index.php?func=detail&atid=525124&aid=2089256&group_id=69596") for progress on this bug.

---

