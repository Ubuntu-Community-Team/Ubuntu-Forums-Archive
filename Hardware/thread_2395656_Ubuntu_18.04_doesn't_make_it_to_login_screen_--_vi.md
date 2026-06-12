---
title: "Ubuntu 18.04 doesn't make it to login screen -- video issue?"
date: 2018-07-05
forum: Hardware
---

### Post by ruberad on 2018-07-05
Over on previous thread, oldfred suggested I create a new issue, so here I go. For reference [here's the previous issue.]("https://ubuntuforums.org/showthread.php?t=2395575")

[Intel NUC D34010WYK (4th gen, "Wilson Canyon") with Core-i3 processor (integrated graphics)]("https://ark.intel.com/products/76978/Intel-NUC-Kit-D34010WYK")

I bought it in 2014, installed 14.04 onto it, then installed 16.04 onto it, and about a month ago installed 18.04 onto it (BIOS boot, not UEFI). The 18.04 install has been fine for that month. Then suddenly the boot process stopped making it all the way to the login screen. It is stuck on one red dot under Ubuntu logo on the splash screen. Pressing the power button again at that point (or checking boot.log from live USB) shows "Started GNOME Display Manager" as the last statement.

What diagnostics can I run to understand what's not working?

SOLUTION (thx to apeitheo2!): [See also here]("https://ubuntuforums.org/showthread.php?t=2395459&page=2&p=13781140#post13781140").

From the grub screen 'e' to edit. At the end of the 2nd to last line that starts 'linux', add 
   systemd.unit=multi-user.target
Then Ctrl-X to resume boot into text login only. After logging in, 

   sudo apt install haveged          # these two commands didn't help me
   sudo systemctl enable haveged # but they helped others and can't hurt I dont' think
   sudo apt update                      # this is what seemed to do the trick
   sudo apt upgrade                     # or perhaps dist-upgrade?
   startx

That got my Xwindow system back, except the sidebar was funky. Reboot after that worked as expected and everything looks good

---

### Post by ruberad on 2018-07-05
Other information from the previous thread; oldfred directed me to use boot-repair to reinstall grub and the kernel, which I did but it didn't change anything.

I booted into recovery mode many many times trying to run grub update, dpkg update, fsck, etc. Grub update was apparently successful, but nothing else. The commands cause a bunch of 'gettin ready to do stuff' messages to print to screen, and then it hangs. dpkg prepares a lot of stuff and then fails because no network (enable network didn't work)

After many iterations of rebooting into recovery mode, I got into a state where recovery mode is frozen (doesn't respond to keyboard). Keyboard works to navigate grub into Advanced/recovery, but then recovery mode is frozen. I tried using a different keyboard as well. And I disconnected spurious USB devices (printer, scanner, optical drive), leaving just keyboard and mouse

---

### Post by ruberad on 2018-07-05
Two general questions: since I was working fine with 16.04 for two years, should I go back to 16.04?

Also oldfred pointed me to 'NUC-certified' ISOs of 16.04 [specifically for the NUC]("https://www.ubuntu.com/download/iot/intel-nuc-desktop"). That appears to be for gen7 NUCs (Dawson Canyon or June Canyon), mine is gen 4 (Wilson Canyon). Would one of those special NUC ISOs be appropriate for my older NUC?

---

### Post by Autodave on 2018-07-05
Did you upgrade 16.04 to 18.04? If so, that is probably your problem: I would do a clean install.  Since 18.04 was working, it should work again. Try booting the machine with a boot disc/USB and see if it runs OK that way. If it does, do a clean install.

---

### Post by apeitheo2 on 2018-07-05
If it boots all the way up to right before the login screen should show, you might have the same issue I had. There's a bug in the 4.15.0-24 kernel that's soon to be fixed, but in the meantime you could try:

```
sudo apt install haveged
sudo systemctl enable haveged
```

There's more information here: [https://ubuntuforums.org/showthread.php?t=2395459&page=2&p=13781140#post13781140](https://ubuntuforums.org/showthread.php?t=2395459&page=2&p=13781140#post13781140)

Good luck

---

### Post by ruberad on 2018-07-05
> **Autodave said:**
> Did you upgrade 16.04 to 18.04? If so, that is probably your problem: I would do a clean install.  Since 18.04 was working, it should work again. Try booting the machine with a boot disc/USB and see if it runs OK that way. If it does, do a clean install.
I did a clean install, reformatting my / partition (I keep my stuff on separate /data and /home partitions). I have never done an Upgrade, from what I've heard it never works anyways, not sure why it is still around, does it ever work for anybody?

Live USB with the same 18.04 ISO that I installed from works fine. So I guess your advice is just reinstall it again? I just might end up doing that, but is this problem going to come back every month though?

---

### Post by ruberad on 2018-07-05
> **apeitheo2 said:**
> If it boots all the way up to right before the login screen should show, you might have the same issue I had. There's a bug in the 4.15.0-24 kernel that's soon to be fixed, but in the meantime you could try:

```
sudo apt install haveged
sudo systemctl enable haveged
```

There's more information here: [https://ubuntuforums.org/showthread.php?t=2395459&page=2&p=13781140#post13781140](https://ubuntuforums.org/showthread.php?t=2395459&page=2&p=13781140#post13781140)

Good luck

Wow that's crazy. Did the 4.15.0-24 kernel just roll out and this is affecting lots of people?

How do I make those commands affect my distro from liveUSB?

thx,

r

---

### Post by apeitheo2 on 2018-07-06
A lot of people with this issue have found that pushing/holding the shift key or moving the mouse around while booting prevents the system from hanging. You could also try switching to one of the other virtual terminals when it hangs by pressing Ctrl+Alt+F2 or Ctrl+Alt+F3, etc. If you can get to the login screen doing that, that's the easiest way.

Otherwise, I would press the 'e' key at the grub screen and then type 'systemd.unit=multi-user.target' (without the quotes) at the end of the line that starts with 'linux' and then pushing Ctrl-X to boot. That'll cause it boot to a text login screen instead of the graphical one, at which point you can login and install & enable haveged, as shown above.

Good luck.

---

### Post by ruberad on 2018-07-06
Hey thanks man, I tried all those things and it didn't help. I don't know what Ctrl+Alt+F2/F3 whatever is supposed to do, it was just iterating between two commands that seemed to not be getting anything done. One was snapd I think?

Holding shift or mousing around like crazy didn't get me there. I did e and edit boot commands, and got to a text login, installed and enabled haveged, but rebooting still behaved the same.

If I'm in that text login, is it possible for me to manually start x windows? That should be able to bypass the hung login screen, right? Or would it just be the same problem?

Any idea when the fix will be released? At that point I should be able to from the text login acquire the fix with an apt or dpkg command, right?

---

### Post by apeitheo2 on 2018-07-06
> **ruberad said:**
> Hey thanks man, I tried all those things and it didn't help. I don't know what Ctrl+Alt+F2/F3 whatever is supposed to do, it was just iterating between two commands that seemed to not be getting anything done. One was snapd I think?
Ctrl+Alt+F1 through Ctrl+Alt+F6 change to different virtual terminals, each with their own login prompt. Ctrl+Alt+F1 and Ctrl+Alt+F2 are used for the display manager and xorg session by default, I believe.
> Holding shift or mousing around like crazy didn't get me there. I did e and edit boot commands, and got to a text login, installed and enabled haveged, but rebooting still behaved the same.
It sounds like you may have a different problem than the one I was talking about. A lot of people have been experiencing the issue I was talking about, so I figured it couldn't hurt for you to give it a try.
> If I'm in that text login, is it possible for me to manually start x windows? That should be able to bypass the hung login screen, right? Or would it just be the same problem?
Yeah, just run 'startx' (without quotes).
> Any idea when the fix will be released? At that point I should be able to from the text login acquire the fix with an apt or dpkg command, right?
For the issue I was talking about, I'm hoping they release the fix soon, but I don't know. As long as you have a network connection, you'll be able to update as you normally do with apt: sudo apt update && sudo apt dist-upgrade

I'm interested to see if 'startx' works or not.

---

### Post by ruberad on 2018-07-06
> **apeitheo2 said:**
> Ctrl+Alt+F1 through Ctrl+Alt+F6 change to different virtual terminals, each with their own login prompt. Ctrl+Alt+F1 and Ctrl+Alt+F2 are used for the display manager and xorg session by default, I believe.
When I switch to different ttys it is not presenting me with a prompt, just showing status of commands that are trying to get started

> It sounds like you may have a different problem than the one I was talking about. A lot of people have been experiencing the issue I was talking about, so I figured it couldn't hurt for you to give it a try.
I read that other thread and it sure sounds the same, some other people were not having success with haveged. I'm hopeful

---

### Post by ruberad on 2018-07-06
OK, so I'm kinda back, with editing to boot into text mode. First try at startx kinda did nothing (same hang?) then I did sudo apt update and sudo apt upgrade (didn't remember "dist-"), but after that startx worked!

Kinda. So I don't get my old sidebar by moving the mouse to the left so it can auto-raise, but I do get it from pressing the windoze key. 

I'm gonna press my luck and try for a reboot now...

---

### Post by ruberad on 2018-07-06
Success!! Seems all back to normal now. Thanks so much for your help -- it's helpful knowledgeable people like you that allow less-knowledgeable people like me avoid windoze

---

