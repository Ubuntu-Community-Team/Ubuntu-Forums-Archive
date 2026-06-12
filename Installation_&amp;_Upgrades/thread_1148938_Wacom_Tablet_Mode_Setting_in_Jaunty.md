---
title: "Wacom Tablet Mode Setting in Jaunty"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by bjennworld on 2009-05-04
Hi,

Upgrading to Jaunty my Wacom ET tablet reverted to Relative Mode using the new hal default settings. Information posted seem to imply that the default hal setting should be Absolute Mode. Attempts to force Absolute Mode in custom_wacom.fdi failed using the line 

<merge key="input.x11_options.Mode" type="string">Absolute</merge>

so I have resorted deleting the custom_wacom.fdi file and re-instating the xorg.conf wacom settings.

Hot plugging is not an issue for me, so having Absolute Mode working again solves my immediate problem.

Has anyone else run into this problem and if so find a solution?

---

### Post by Favux on 2009-05-08
Hi bjennworld,

As I understand it Absolute is suppose to be the default.  If you're interested you could try this modified 10-wacom.fdi.  It's on post #176 here:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)  Maybe it would work for you.

By the way xorg.conf is working for you with the "default" Jaunty 0.8.2-2 linuxwacom packages?

---

### Post by bjennworld on 2009-05-09
Hi Favux

Thanks for the suggestion. I tried the modified .fdi file but it didn't address my problem of defaulting to Relative mode.

I agree that all the posts I have seen state that the Jaunty default mode should be Absolute, but for some reason that's not the case for me.

When I upgraded from Intrepid all my custom wacom lines in xorg.conf were automatically commented out, so to get back to Absolute mode I re-instated these lines and added .backup to the custom_wacom.fdi file. So it's not a standard Jaunty install xorg.conf that's working now.

It looks as though the next Ubuntu release will have a proper Wacom setup GUI, so hopefully these sort of issues will be resolved in due course.

---

### Post by Favux on 2009-05-09
Hi bjennworld,

That's too bad.  Did you try putting the Absolute mode into the .xinitrc file the calibration gui "wacomcpl" generates?  I think it's an allowed xsetwacom command.  Would have to check the LWP HOW TO.

---

### Post by Favux on 2009-05-09
Yep, it would be:
```
xsetwacom set stylus Mode Absolute
```
or Relative.  That isn't in my .xinitrc because it suppose to be default but the HOW TO says you can apply it so it should work in .xinitrc.

---

### Post by Sawer on 2009-05-09
I'm  new to  Jaunty I.m  running  Klikit Hardy. What do I need to do  to get my Bamboo  to fully to  work. I see from a post in this thread that xorg is already set for Wacom but I don't see the settings. Can I just  run the script for Hardy updated to 8.2?
Thanks

---

### Post by Favux on 2009-05-09
Hi Sawer,

Pardon, but I don't understand what you're saying.  So correct me.

You just moved from Hardy to Jaunty.  You have a Wacom Bamboo.

You have something called Klikit Hardy.  Is this a script that automatically installs your Bamboo in Hardy?

If so while the script could probably be updated to Jaunty I think it would be easier if you just installed this new .fdi.  It has worked for a Bamboo and Bamboo Fun already.  You can find it on post #176 here:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)

If you need more help ask.

Good luck!

---

### Post by Sawer on 2009-05-09
Sorry Favux for not being  clearer. Klikit is a  Ubuntu  spin off the script is  from Ubuntu how to. it has worked fine until Jaunty. I've used it  in Debian 5.0 and Mepis and  LXDE lite. it has worked fine  in all of them.
In Jaunty it sounds like you don't need to edit xorg.conf is this correct? What I need to do is make the file you have  shown a link to is this  correct? What about the wacom kernel does this need to be installed before  adding the fdi file?
I hope this makes more sense and thanks for the quick reply

---

### Post by Favux on 2009-05-09
Hi Sawer,

That is correct, in Jaunty you don't use xorg.conf, you use the HAL/.fdi method.  Now I know what Klikit is.  I assume the script your talking about configures the Bamboo buttons?

If you check Synaptics Package Manager you should have the 0.8.2-2 linuxwacom packages (specially patched to support Xserver 1.6 and HAL) installed.  They are xserver-xorg-input-wacom (the drivers) and wacom-tools.  If not install them.  Then replace the default 10-wacom.fdi with the 10-wacom.fdi I referred you to.   Then the script (which I'm assuming uses xsetwacom commands) should work.

---

### Post by Sawer on 2009-05-09
I hate to be a pain but  all I can find is /usr/share/hal/fdi/preprobe/20ththirdparty or policy/20ththirdparty.There is also a fdi.dtd file. 
These don't look right to me is there someplace else i can find 10-wacom.fdi?

---

### Post by Favux on 2009-05-09
Hi Sawer,

Isn't the 10-wacom.fdi in the /usr/share/hal/fdi/policy/20thirdparty/, ie the 20thirdparty folder?

---

### Post by Sawer on 2009-05-09
All that's in there is 10osvendor with a  number of fdi's but not 10-wacom.fdi. In the20thirdparty there is only 20-libgpod-sysinfo-extended.fdi. There is 10-tabletPCs.fdi in 10osvendor folder. Do I need to build the kernel source?

---

### Post by Favux on 2009-05-09
Hi Sawer,

It sounds like the linuxwacom packages aren't installed.  Did you check in Synaptic Package Manager?  If it says they are installed tell it to reinstall both of them them.  Reboot and see if the "default" 10-wacom.fdi is now there.

I suppose you could check "/etc/hal/fdi/policy/" and see if the wacom.fdi is there.  It shouldn't be.

The 10-tabletPCs.fdi is executed first, I think, because it's in 10osvendor.  So sets things up for the 10-wacom.fdi.  It shouldn't matter to us at this point.

---

### Post by bjennworld on 2009-05-10
Hi Favux

The .xinitrc suggestion didn't work, still in Relative Mode.

Wacomcpl doesn't recognise the tablet when in 'hal control' (blank select device box) - in 'xorg control' it does recognise it and sets the modes correctly. Hence I assumed wacomcpl had been sidelined by the new hal routine.

Interesting!

---

### Post by Favux on 2009-05-10
Hi bjennworld,

No, wacomcpl still works.  The problem is the info.callout in the default 0.8.2-2 wacom.fdi is returning HAL names that wacomcpl and xsetwacom don't recognize.  You can see that by typing in a terminal:
```
xsetwacom list
```
and comparing it to
```
xinput --list
```
The .fdi isn't parsing the names correctly.  The new .fdi I linked above does parse the names correctly.  So then the specially patched 0.8.2-2 linuxwacom (to support HAL) in Jaunty works as does wacomcpl and xsetwacom.  Well it's worked so far for several tablets anyway.  Maybe we can add the absolute command to the .fdi.

---

### Post by Amrith Kumar on 2009-05-10
I found that many links on this subject didn't work for me. The names of the devices are incorrect as indicated in most of these posts.

I found a different workaround that is at [http://technophilesdiary.wordpress.com/2009/05/10/ubuntu-9-04-wacom/](http://technophilesdiary.wordpress.com/2009/05/10/ubuntu-9-04-wacom/)

I hope it helps some of you.

---

### Post by bjennworld on 2009-05-10
Hi,

This seems to be a widespread problem.

By running 'xsetwacom list' and 'xinput list' in HAL and xorg control modes I seem to confirm Favux comments that in xorg mode all is well and in HAL mode there is a 'mismatch' of identities. This may also explain why custom_wacom.fdi file entries have no effect either.

The workaround used by Amrith didn't work for me.

Reading all the posts on this subject it seems likely a problem exists that will be resolved in due course, so as the xorg.conf option works for me at present I will revert to that for now and await future developments.

Thanks for your responses.

---

### Post by Sawer on 2009-05-10
I'm now getting 10-wacom.fdi as a XML doc with no text files. Everything in  hal is like this now. I find  I can't  edit any file except in terminal as sudo, this very annoying.

---

### Post by Favux on 2009-05-10
Hi Sawer,

All .fdi files are xml doc.s.  You can edit them as a text file by right clicking and choosing the "open with text editor" option.  Or to change it back to a text file rename it with the .txt extension like:  10-wacom.fdi.txt

---

### Post by Sawer on 2009-05-10
Thanks Favux, I still have a lot to learn. I'll try it in a few minutes.

---

### Post by tienhn on 2009-05-13
Hi All,
I have Wacom tablet and I follow this instruction here:
[https://help.ubuntu.com/community/Wacom.fdi](https://help.ubuntu.com/community/Wacom.fdi)

It helps me configure relative/absolute mode properly. The best part is you only need to unplug and plug the device to apply the new setting.

Cheers,

---

### Post by bjennworld on 2009-05-14
Hi tienhn

That is interesting. I used the same document as a basis to try and resolve my problem.

I inserted the command -

<merge key="input.x11_options.Mode" type="string">Absolute</merge>

in each of the 'stylus' 'eraser' code blocks with no success.

Have I got this line wrong?

---

