---
title: "SD card - Operation is already pending - Lubuntu 18.04"
date: 2021-04-13
forum: Hardware
---

### Post by steve234 on 2021-04-13
I'm having issues with SD cards I use for my 3d printer not mounting on my Lububtu 18.04 system

I get an "Operation is already pending" message, and "operation was cancelled" when unplugged. This happens with all (both) my SD cards.

In the past a restart has fixed this, but sadly not today.

Any help debugging would be greatly appreciated.

---

### Post by CelticWarrior on 2021-04-13
What [COLOR=#000000]"operation in progress" is that, exactly? 
I mean does the message show up when you insert the card or after trying to copy something?[/COLOR]

---

### Post by steve234 on 2021-04-13
I'll fire her up after dinner and get back to you

---

### Post by steve234 on 2021-04-13
> **CelticWarrior said:**
> What [COLOR=#000000]"operation in progress" is that, exactly? 
I mean does the message show up when you insert the card or after trying to copy something?[/COLOR]

Right, so I:


[LIST=1]
[*]Fire up the PC
[*]Open pcmanfm
[*]Insert SD card
[LIST=1]
[*]SD card shows up in left hand panel of pcmanfm, but is clearly not mounted (there's no little eject icon)
[/LIST]

[*]Left click on SD card
[LIST=1]
[*]Error message appears in popup ```
An operation is already pending
``` apologies - I was inaccurate in my first post.
[/LIST]

[*]Clear error message by clicking OK
[*]Right click and select "mount volume"
[LIST=1]
[*]Same error pop-up as 4.1 above
[/LIST]

[*]Clear error message in the same way as (5) above
[*]Right click and select "eject removable media"
[LIST=1]
[*]Pop-up says "operation was cancelled"
[/LIST]

[*]Remove and reinsert SD card
[LIST=1]
[*]Steps 4-8 above repeat without letting me mount the card
[/LIST]
[/LIST]

So something is happening - but no clues (from the UI that is) what the issue or "operation" is.

**Edit - if i try to copy a file (drag and drop) the UI just puts the file back where it came from - if you know what I'm saying

---

### Post by CelticWarrior on 2021-04-13
It's possible the cards and/or the reader are defective.
I would test the cards in a different computer if available. Also they may need to be formatted again.

---

### Post by steve234 on 2021-04-13
I'm wondering whether it's a hardware issue. They work fine in the printer - including mounting and unmounting (though I appreciate that is not a "computer" in that sense)

---

### Post by mastablasta on 2021-04-14
usb (2.0) card reader costs 2 or 3 EUR. or maybe you could borrow it from someone to test it and see if it's an OS or hardware issue.

---

### Post by steve234 on 2021-06-25
Apologies @mastablasta and @celticwarrior - it's been ages since I fired up the 3d printer. All was fine for a while but this issue (re)reared its head again.

It seems like an *OS level *issue, rather than a hardware issue, because:


[LIST=1]
[*]Both cards work fine in another PC, both in the SD slot and a USB card reader.
[*]Today, both cards refuse to mount in my main PC with the ```
[COLOR=#000000][FONT=&quot]An operation is already pending[/FONT][/COLOR]
``` as in the threads above, regardless of whether I use the SD slot, or a USB card reader.
[/LIST]

Mods - Do I need to move this post out of "hardware"?

---

### Post by sudodus on 2021-06-25
What file system is there in the SD card? And what version of Ubuntu are you running in your PC? If exFAT and an older version of Ubuntu you may need to install some program packages in order to manage the file system.

Otherwise there may be many things that can disturb the interaction between the operating system and the card, for example other USB devices, that are connected. So you can shutdown the computer, disconnect all other USB devices, reboot and then connect the USB adapter with the card and try again.

See also [this link](https://askubuntu.com/questions/952673/how-do-i-copy-a-file-larger-than-4gb-to-a-usb-flash-drive/952706#952706) and [this link](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035) with some more tips to analyze the problem.

---

### Post by steve234 on 2021-06-25
thanks Sudodus

> [COLOR=#000000]What file system is there in the SD card? [/COLOR] It's FAT32, which is the format my 3d printer recognises.

> [COLOR=#000000]And what version of Ubuntu are you running in your PC?[/COLOR] - this is in the title of this thread - lubuntu 18.04 - ```
lsb_release -aNo LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.5 LTS
Release:    18.04
Codename:    bionic

```

> [COLOR=#000000]there may be many things that can disturb the interaction between the operating system and the card, for example other USB devices[/COLOR]

This seems very unlikely to me, the SD card problem happens on and off - and my system setup has not changed.

> 
[COLOR=#000000]So you can shutdown the computer, disconnect all other USB devices[/COLOR]

I rebooted with the USB Bluetooth adaptor (the only device I have connected except my mouse and keyboard (which I obvs need to login)) unplugged and the SD cards work fine (for now). I've re-inserted the Bluetooth adaptor, and they still work fine. Is this a case of the BT adaptor doing something screwy?

---

### Post by tea for one on 2021-06-25
Do the SD cards appear in Disks (gnome-disk-utility)?

You can also mount and unmount there.

---

### Post by sudodus on 2021-06-25
> **steve234 said:**
> 
I rebooted with the USB Bluetooth adaptor (the only device I have connected except my mouse and keyboard (which I obvs need to login)) unplugged and the SD cards work fine (for now). I've re-inserted the Bluetooth adaptor, and they still work fine. Is this a case of the BT adaptor doing something screwy?

Maybe yes (the BT adaptor is doing something screwy), maybe there is some other culprit. Anyway, you found a work-around now.

---

### Post by Autodave on 2021-06-25
By chance, are you using the 3D printer in Windows?

---

### Post by steve234 on 2021-06-25
Thanks everyone, as @sudodus has noted I'll just use the PC without the BT adaptor as a workaround.

On the other Q's...

> [COLOR=#000000]By chance, are you using the 3D printer in Windows?[/COLOR]eeeerm no!?! Its standalone

> [COLOR=#000000]Do the SD cards appear in Disks (gnome-disk-utility)?[/COLOR]

[COLOR=#000000]You can also mount and unmount there.[/COLOR] lububtu doesn't have gnome, I'm not sure you've understood this thread - I'm working in in PCManFM, and when I tried to mount I got the "operation pending" error

---

### Post by tea for one on 2021-06-25
> **steve234 said:**
>  lububtu doesn't have gnome, I'm not sure you've understood this thread - I'm working in in PCManFM, and when I tried to mount I got the "operation pending" error

Apologies, I do know that Lubuntu does not use gnome-disks - I simply missed the Lubuntu tag. 

I was thrown by this in post 10:-
```
lsb_release -aNo LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.5 LTS
Release:    18.04
Codename:    bionic
```

I have seen other flavours such as Xubuntu also report Ubuntu in this command and it is a bit misleading when you skim through an older thread.

Anyway, I'm glad that [COLOR="#0000FF"]sudodus[/COLOR] pointed you to a solution.

Are you going to mark it as solved?

---

### Post by steve234 on 2021-06-26
> [COLOR=#000000]I simply missed the Lubuntu tag.[/COLOR]No worries man. My apologies, due to the frustration of this issue I was a bit too quick to criticise - can i ask, how did you tag u/sudodus? I must be missing something int he advanced menus?

> [COLOR=#000000]Anyway, I'm glad that [/COLOR][COLOR=#0000FF]sudodus[/COLOR][COLOR=#000000] pointed you to a solution.[/COLOR]

[COLOR=#000000]Are you going to mark it as solved?[/COLOR] So sorry guys, but after the initial couple of successes (having removed the BT adaptor) the issue persists - there must be something else going on here. I'm at a loss because:


[LIST=1]
[*]This is an issue specific to one machine;
[*]The SD cards seem not to be the issue. They work int he printer, and both in the card reader, and USB card reader of my (also lubuntu 18.04) laptop - but that laptop doesn't live in a convenient place for use with the 3d printer;
[*]The PC's built in card reader doesn't seem to be the issue - the issue happens regardless of whether a USB card reader, or the internal reader are used; and
[*]The issue is intermittent - I can get the SD cards (auto or manually) mount in PCManFM, sometimes, if I do a few shutdown / reboots - that is not efficient as boot time is not fast, and there's no guarantee it will work each time.
[/LIST]

---

### Post by sudodus on 2021-06-26
If you wish, we can try to find out if the issue is due to the computer hardware or the software (operating system). For example, you can create a persistent live or installed 20.04.2 LTS system in a USB pendrive and check if it works better with your SD card.

---

### Post by steve234 on 2021-06-26
That's very kind of you. I need to make a USB 20.04 drive anyway as I'll need to upgrade my machines eventually. Obvs the pendrives get the same "operation pending" issue as SD cards on this PC, so I'll have to use my laptop to generate those

---

### Post by tea for one on 2021-06-26
> **steve234 said:**
> No worries man. My apologies, due to the frustration of this issue I was a bit too quick to criticise - can i ask, how did you tag u/sudodus? I must be missing something int he advanced menus?

Thank you for your gracious reply.
It certainly is frustrating when software/hardware combines to trip us up.

To answer your question, I assume that you are referring to the text colour.
I like the choice of colours to emphasise certain words.

Advanced Reply > Top Line of Icons > Large **A** with Small Down Arrow to right of **A** = [COLOR="#0000FF"]Text Colour[/COLOR]

More format info here [https://ubuntuforums.org/misc.php?do=bbcode](https://ubuntuforums.org/misc.php?do=bbcode) 

Back to your SD card problem, a friend of mine had a similar problem with SD Card reader not working at all.
His Xubuntu 18.04 installation was in UEFI mode and we had to turn on the Legacy mode in the UEFI firmware to recognise the SD cards.
Subsequently using Xubuntu 20.04 in UEFI mode (together with latest UEFI update), the SD card reader works OK.
Sometimes, there is little rhyme or reason in the process.

Finally, I agree with [COLOR="#000080"]sudodus[/COLOR], try a live session of Lubuntu 20.04.

Good luck

---

### Post by Autodave on 2021-06-26
You don't happen to have a USB hub on the system?  Whether or not anything is plugged into it doesn't matter.  If you do, disconnect it and see what happens.  (I have one here that causes all sorts of problems even though anything plugged into it usually works.  It won't always allow the machine to boot and then if it does allow the boot, it can make it run so slowly.)

---

### Post by steve234 on 2021-06-26
Righty ho, - I'm ready to go with my freshly MKUSB'd 20.04 LTS (persistent) stick - what next?

---

### Post by steve234 on 2021-06-26
OK, it seems on the live USB, at least in the current session, I can mount and unmount my SD card with impunity. The only hiccup being lxqt-panel telling me that it's already mounted, but I think that happens if I click on it in the panel popup, and also the "removable media inserted" popup?

So I presume next steps are:

- reboot into live, see if luck continues; and
- if so, back up my very old and complicated (somehow) i3-gaps install, featuring many workarounds / mods etc, and then upgrade?

For the sake of not upgrading riiiiight now, is there anything I can do in 20.04 to troubleshoot my 18.04 setup?

---

### Post by tea for one on 2021-06-26
Good news about the SD cards in 20.04 but you cannot upgrade Lubuntu 18.04 to 20.04.
> Note, due to the extensive changes required for the shift in desktop environments, the Lubuntu team does not support upgrading from 18.04 or below to any greater release. Doing so will result in a broken system. If you are on 18.04 or below and would like to upgrade, please do a fresh install.

Info here [https://lubuntu.me/focal-released/](https://lubuntu.me/focal-released/)

LXDE was used in 18.04 and LXQT in 20.04

---

### Post by steve234 on 2021-06-26
Apologies for the loose language, I meant reinstall (I think you answered my previous thread on that, sorry)

---

### Post by sudodus on 2021-06-26
> **steve234 said:**
> OK, it seems on the live USB, at least in the current session, I can mount and unmount my SD card with impunity. The only hiccup being lxqt-panel telling me that it's already mounted, but I think that happens if I click on it in the panel popup, and also the "removable media inserted" popup?

So I presume next steps are:

- reboot into live, see if luck continues; and
- if so, back up my very old and complicated (somehow) i3-gaps install, featuring many workarounds / mods etc, and then upgrade?

Yes, try it a few times to make sure things work also when repeated. And yes, I think it is time to backup your personal files and make a fresh installation of Lubuntu 20.04.2 LTS.
> 
For the sake of not upgrading riiiiight now, is there anything I can do in 20.04 to troubleshoot my 18.04 setup?

If 20.04.2 keeps working well with the SD card, I would not spend more time to troubleshoot the 18.04 setup.

> **tea for one said:**
> Good news about the SD cards in 20.04 but you cannot upgrade Lubuntu 18.04 to 20.04.

Info here [https://lubuntu.me/focal-released/](https://lubuntu.me/focal-released/)

LXDE was used in 18.04 and LXQT in 20.04

+1; I agree with tea for one.

---

### Post by steve234 on 2021-06-26
Cheers all - I guess (if it works consistently) it's time to start afresh - god knows what i3-gaps / compton (or whatever the new one is) / syncthing / workarounds / mounting of spinner etc I'll lose (or perhaps won't need). 

I already have /home backed up. I guess a full backup of / is also a sensible starting place for things like /etc/fstab I might need lines from?

---

### Post by sudodus on 2021-06-26
Yes, that kind of backup is a good idea. You never know what you might want to use or at least look at, but my experience of new installations is that it is a good opportunity to get rid of tools and settings that you no longer use.

---

### Post by steve234 on 2021-06-27
All done, I'm now the proud owner of a 20.04 lts setup. Just need to work through the various i3-gaps things which have fallen over

I'll mark this as solved. Shame a fresh install was the solution (fingers crossed), but it needed to be done at some point.

Thanks again everyone

---

