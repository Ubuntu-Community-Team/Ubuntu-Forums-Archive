---
title: "Latest kernel update caused problems"
date: 2008-11-30
forum: Hardware
---

### Post by mitchellcipriano on 2008-11-30
My ThinkPad R51 was running perfectly on 8.10. Suspend worked flawlessly. Then yesterday Update Manager found the 2.6.27-9 kernel. I accepted the update and it broke suspend.  If I try to do a suspend, it will suspend fine, but when I try to restart the password dialog comes up with no text. If I try to enter the password, it simply hangs. I can then switch to text mode, I can not get back into the GUI.
What is worse is that the update also broke shut down. If I try to shutdown the system just hangs.

Any ideas? Is it possible to step back to the previous kernel?

Thanks for the help,

Mitch

---

### Post by mitchellcipriano on 2008-12-01
Anyone??

---

### Post by quanumphaze on 2008-12-02
> **mitchellcipriano said:**
> Anyone??

Don't worry, I'm here for you :D

Just use the previous kernel for the time being. You can set it default for Grub with the Startup Manager package. I will stick with 2.6.27-7 and see if things get better. Was there a -8?

I'm running an Acer Aspire 3680, and that kernel update just made things really crap. Suspend still works fine (though the ath_pci wireless module sometimes needs a kick in the butt).

When I start up, sometimes it hangs for about 20 sec near the end just before X starts (the usplash progress bar is just about finished) and it drops back into text mode (killing of usplash) showing that HAL is loading up. Soon is continues as normal.

Later when I shut down it hangs at the end every time with the little cursor in the top left corner. By pressing the MagicSysRq combo (that's Alt+PrtScn+R,S,E,I,U,O) it prints those opperations and will half the time shutdown on the 'O'. The other half of the time just hang in a weird state where it spins down the disk and seems to be in an off state but the fan is still spinning (and I think the backlight is still on, though I'm not sure, can't remember).

The whole system has locked up on me several times. Sometimes X dies violently with it and MagicSysRq doesn't work, or once the screen was off in power save and it didn't wake up (and MagicSysRq doesn't work again). The weirdest time was when it just froze the screen, yet the mouse cursor could still move freely. Since the mouse was still happy that means it's just X having explosive diarrhea. Crtl+Alt+Backspace ... nothing, Crtl+Alt+F1 ... nothing, Crtl+Alt+Del ... nothing, Alt+PrtScn+R,S,E,I,U,O ... WTF nothing! Even when the mouse was still happily moving across the screen the MagicSysRq combo did nothing.

2.6.27-9 must die!

---

### Post by steveneddy on 2008-12-02
When you get to the GRUB screen during boot up, hit the Esc key and select the previous kernel.

If that helps, you can edit the GRUB boot file so it won't boot into the bad kernel.

I'm on Windows right now and don't recall the name of the file to edit at the moment.

Commenting out the kernel that gives issues should solve the issue until an updated kernel is released.

Not sure, but I think it is:

/boot/grub/menu.lst

and just comment out the first two kernel entries:

```

#title        Ubuntu 8.04.1, kernel 2.6.24-22-generic
#root        (hd0,4)
#kernel        /boot/vmlinuz-2.6.24-22-generic root=UUID=769b8506-4b75-461c-9f9a-7e9e7acfe04c ro quiet splash
#initrd        /boot/initrd.img-2.6.24-22-generic
#quiet

#title        Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
#root        (hd0,4)
#kernel        /boot/vmlinuz-2.6.24-22-generic root=UUID=769b8506-4b75-461c-9f9a-7e9e7acfe04c ro single
#initrd    

```

then reboot and it should be fine.

---

### Post by mitchellcipriano on 2008-12-02
Thanks for the suggestions. It seems to have fixed my problem. I will just look forward to the next kernel.

---

### Post by steveneddy on 2008-12-03
Glad to help.

---

### Post by mitchellcipriano on 2008-12-04
I continued to play around with the 2.26.27-9 kernel and I think I solved the problem.

After the update to the 2.26.27-9 kernel, I had sound problems and shutdown issues. My sound problem was solved by turning the sound up. Even with the mute off and the slider showing full volume, I had no sound. If I muted it in that position and then turned it up, I would get sound.

Each time I rebooted the system would hang and I would need to force the shutdown and my sound problem would be back when I rebooted. I noticed it was hanging when shutting down ALSA. At the same time I found a discussion thread about the ownership of files in the home folder being switched to root. I then checked and found the .dmrc file was owned by root. So, I ran ran Nautilus with sudo rights and gave myself ownership of all the files in home. This seems to have solved all my problems - sound and shutdown.

---

### Post by quanumphaze on 2008-12-05
My .drmc is fine and owned by me.

The ALSA problem should have been fixed by a recent update to alsa-utils. Before that update there was a thread by frodon [[click here]("http://ubuntuforums.org/showthread.php?t=966436")] that has lots of hacks to get around the problems many users are experiencing with Intrepid, and contained the ALSA hack. It had to do with ALSA and the network being up/down and making NetworkManager shutdown before ALSA.

I think I will try out -9 again and see if anything is still bad. My problems extended beyond the ALSA shutdown hang.

---

