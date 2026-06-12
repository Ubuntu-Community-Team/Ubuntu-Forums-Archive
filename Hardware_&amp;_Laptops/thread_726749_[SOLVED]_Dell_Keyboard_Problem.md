---
title: "[SOLVED] Dell Keyboard Problem"
date: 2008-03-17
forum: Hardware &amp; Laptops
---

### Post by donniezazen on 2008-03-17
Hello Friends,

I am new to Linux and i am facing problem regarding my dell laptop keyboard. I have Dell 6400/E1505.  I have successfully installed Ubuntu 7.10. My front multimedia key control panel is not working. When  i press the front volume keys a big figure appears to increase or decrease volume but it has no effect on volume.  I have tried choosing different keyboard layouts and also tried using keyboard shortcuts. But nothing is working. I don't know if i should connect these two things but i think because of this keyboard layout problem i am not able to use some of the desktop effects like cube effect...

I have also searched for related forum but as i am new all those things are confusing me and of not much help.

I would appreciated any help or direction.

Thanks.

---

### Post by erginemr on 2008-03-17
Hello and welcome to Ubuntu Forums.

IMHO, the two issues (keyboard buttons and desktop cube) are unrelated. Putting the keyboard problem aside, I will try to address the Desktop Cube issue.

For the cube to work, you should first install the package "compizconfig-settings-manager", or ccsm in short, if you do not have it already. Then, you will have an "Advanced Desktop Effect Settings" item in your menu. 

You also need to have a compatible (read 3D capable) graphics card, preferably an NVIDIA brand. And also need to have 3D enabled by letting the system (Restricted Drivers Manager in the menu) install the appropriate 3D driver for it. You can check whether the 3D has been enabled by running:
```
glxinfo | grep -i direct
```
from the terminal, and can gather more information on the brand of your graphics card by:
```
lspci | grep -i vga
```

Once this is out of the way:

1. First, make sure that compiz-config-settings-manager (or ccsm in short) has been installed in Synaptic.

2. Then right click on your desktop and select Change Desktop Background -> Visual Effects tab and set visual effects to "Custom". 

3. Press "Preferences" on the same tab next to the "Custom" selection. In there, make sure that the plugins "Desktop Cube" and "Rotate Cube" have been enabled.

4. Last but not least, you should also make sure the number of virtual desktops is four (4). You can adjust this setting by right-clicking the virtual desktops applet on the bottom-right corner of your desktop and selecting options / preferences from the pop-up menu.

---

### Post by donniezazen on 2008-03-17
Thanks you my cube problem is solved. But the keyboard is still the problem.

Hope somebody will come with any solution.

Thanks a lot.

---

### Post by DellCA on 2008-03-17
The media buttons are not part of the keyboard, so adjusting the keyboard layout is not going to get them to work.  They are more like hardware switches that talk to the motherboard (like the power button or the suspend (aka reed) switch that puts the computer to sleep when you close the LCD on a notebook).

In Windows it is the Dell Notebook System software (the Dell addtion to the chipset software) that ensure those buttons work.  Unfortunately, I do not know what you need to change/set in linux to get them to work, but I do know it can be done as I have seen posts on the Gentoo forum (the linux flavor I use at home) from people that got them to work.  My guess would be it requires, at the least, a kernel option to be enabled.

Larry
Dell Customer Advocate

---

### Post by unutbu on 2008-03-17
This is just a shot in the dark:
Go to the gnome panel in the upper left corner of your screen and click System>Preferences>Keyboard shortcuts. There you should (may?) see a Sound tab, underwhich you should find items "Volume down" and "Volume up". Maybe you can configure it that way.

---

### Post by donniezazen on 2008-03-17
> **DellCA said:**
> The media buttons are not part of the keyboard, so adjusting the keyboard layout is not going to get them to work.  They are more like hardware switches that talk to the motherboard (like the power button or the suspend (aka reed) switch that puts the computer to sleep when you close the LCD on a notebook).

In Windows it is the Dell Notebook System software (the Dell addtion to the chipset software) that ensure those buttons work.  Unfortunately, I do not know what you need to change/set in linux to get them to work, but I do know it can be done as I have seen posts on the Gentoo forum (the linux flavor I use at home) from people that got them to work.  My guess would be it requires, at the least, a kernel option to be enabled.

Larry
Dell Customer Advocate

Thanks Larry,

Can you elaborate what you mean and how to enable kernel option? The other thing is when i first installed Ubuntu my wireless was not working but my front keys were working, when i reinstalled it my internet started working flawlessly without doing anything but this time front keys are not working.

Soham

---

### Post by donniezazen on 2008-03-17
> **unutbu said:**
> This is just a shot in the dark:
Go to the gnome panel in the upper left corner of your screen and click System>Preferences>Keyboard shortcuts. There you should (may?) see a Sound tab, underwhich you should find items "Volume down" and "Volume up". Maybe you can configure it that way.

Thanks but as i earlier mentioned i have already tried changing keyboard shortcut but that thing is not working.

Thanks anyways

---

### Post by unutbu on 2008-03-17
Mea culpa.
To make up for it, may I point out this thread:
[http://ubuntuforums.org/showthread.php?t=448669](http://ubuntuforums.org/showthread.php?t=448669)

---

### Post by erginemr on 2008-03-18
> **unutbu said:**
> This is just a shot in the dark:
Go to the gnome panel in the upper left corner of your screen and click System>Preferences>Keyboard shortcuts. There you should (may?) see a Sound tab, under which you should find items "Volume down" and "Volume up". Maybe you can configure it that way.

> **unutbu said:**
> Mea culpa.
To make up for it, may I point out this thread:
[http://ubuntuforums.org/showthread.php?t=448669](http://ubuntuforums.org/showthread.php?t=448669)

This is a valuable advice indeed. I believe the second post involving selecting the default sound will work, but if it doesn't, then I also suggest you to retry the first one and try to assign volume temporarily to a new keyboard shortcut this time to check if it works. 

You should also try if your media buttons work without Compiz enabled.

If you can see the volume increase/decrease icon showing up when you press those buttons, then it means the system "understands" the command, but the sound system does not reply appropriately. So, the next in line to look at is the sound driver. But for now, you should  concentrate on the keyboard.

If all else fails, then I suggest to to read the following 3 page thread thoroughly and turn your attention to the tool "xev" as written there, where we have worked elaborately to sort out the keyboard issue of another forum member, but to no avail unfortunately:

[http://ubuntuforums.org/showthread.php?t=624051](http://ubuntuforums.org/showthread.php?t=624051)

---

### Post by donniezazen on 2008-03-18
Thank you

Its lot for me at this time. Let me try and i will come up with results.

soham

---

### Post by donniezazen on 2008-03-18
> **erginemr said:**
> This is a valuable advice indeed. I believe the second post involving selecting the default sound will work, but if it doesn't, then I also suggest you to retry the first one and try to assign volume temporarily to a new keyboard shortcut this time to check if it works. 

You should also try if your media buttons work without Compiz enabled.

If you can see the volume increase/decrease icon showing up when you press those buttons, then it means the system "understands" the command, but the sound system does not reply appropriately. So, the next in line to look at is the sound driver. But for now, you should  concentrate on the keyboard.

If all else fails, then I suggest to to read the following 3 page thread thoroughly and turn your attention to the tool "xev" as written there, where we have worked elaborately to sort out the keyboard issue of another forum member, but to no avail unfortunately:

[http://ubuntuforums.org/showthread.php?t=624051](http://ubuntuforums.org/showthread.php?t=624051)

> **unutbu said:**
> Mea culpa.
To make up for it, may I point out this thread:
[http://ubuntuforums.org/showthread.php?t=448669](http://ubuntuforums.org/showthread.php?t=448669)

Hey that worked. Second post solved my problem. Thanks you so much to all of you guys.

---

### Post by erginemr on 2008-03-18
Great! Now you can have fun with your Ubuntu! :guitar:

**To close a thread** -> Select "mark this thread as solved" from the thread tools menu.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by DellCA on 2008-03-18
> **soham_1207 said:**
> Thanks Larry,

Can you elaborate what you mean and how to enable kernel option? The other thing is when i first installed Ubuntu my wireless was not working but my front keys were working, when i reinstalled it my internet started working flawlessly without doing anything but this time front keys are not working.

Soham
If it used to work, you made some changes, and then it stopped working then something you changed would be the problem.  That tells me it was some kind of configuration change (but not necessarily a kernel configuration change, unless you made kernel changes) that caused the problem.  The solution you used looks like it just corrected how the audio channels were configured (whats active, whats muted, how they are combined, etc).

Basically, the media keys talk to the motherboard and tell it a hardware request for <event> has been given. e.g., volume up, volume down, eject CD tray.  The chipset/dell notebook system software tells Windows how to respond to those commands, and there are kernel options you can configure that do the same thing for the linux kernel.  From what you've posted, and what I've seen on other threads, Ubuntu appears to have the kernel configured already for at least some of those commands.


Larry
Dell Customer Advocate

---

### Post by donniezazen on 2008-03-18
Thanks,

I love Ubuntu. And some front multimedia keys are not going to stop me from using Ubuntu.

---

