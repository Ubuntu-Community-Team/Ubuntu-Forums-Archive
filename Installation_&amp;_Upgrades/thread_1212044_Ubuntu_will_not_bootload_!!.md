---
title: "Ubuntu will not boot/load !!"
date: 2009-07-13
forum: Installation &amp; Upgrades
---

### Post by stuart.reinke on 2009-07-13
I've got a strange problem. I can't get Ubuntu Intrepid or Jaunty to boot. 

I was running Hardy with no problems on my IBM Thinkpad R40e when I decided to install Jaunty.

I put in the live cd and tried to boot. The computer locks up and leaves me with a mouse pointer in the middle of a blank orange screen.

I assumed my cd was corrupted and decided to use Update Manager. 

After upgrading to Intrepid via Update Manager the computer locked up on reboot (see above)

I tried an Intrepid live cd and the same lock up happened.

I do not have a Hardy live cd to try.

I'm typing this via a PCLinuxOS live cd. It booted with no problem.

I can mount my Ubuntu partitions with no problem from this live cd

I hope someone can tell me what is going on with my computer, and how to fix it.

Thanks in advance for any help/ideas you might have.

Stu

P.S. I also have a small partition with Karmic alpha2 installed. It is currently not included in my GRUB file.

---

### Post by csabo2 on 2009-07-13
It sounds like a graphical issue to me, what video card do you have.

---

### Post by stuart.reinke on 2009-07-13
> **csabo2 said:**
> It sounds like a graphical issue to me, what video card do you have.  I don't know. How do I find out? I've run both jaunty and intrepid on this machine before.

---

### Post by DaGrimReefah on 2009-07-13
Try opening your xorg.conf and adding

```
Section "ServerFlags"
        Option     "AutoAddDevices"   "false"
EndSection
```

It sounds like you're having issues with hotplugging and the new way Ubuntu decided to handle X and your HAL.

---

### Post by stuart.reinke on 2009-07-13
> **DaGrimReefah said:**
> Try opening your xorg.conf and adding

```
Section "ServerFlags"
        Option     "AutoAddDevices"   "false"
EndSection
```

It sounds like you're having issues with hotplugging and the new way Ubuntu decided to handle X and your HAL.

That helped a little. I got the desktop to load, but it locked up when the first window opened.

I'm wondering if the Karmic installation is getting in the way somehow. 

Perhaps if I wipe the drive clean then the live cd will boot.

any thoughts?

---

### Post by DaGrimReefah on 2009-07-13
In your xorg.conf, change your device drivers to vesa.

```
Section "Device"
   Identifier   "Configured Video Device"
   Driver       [COLOR="Red"]_"vesa"_[/COLOR]
EndSection
```

---

### Post by stuart.reinke on 2009-07-13
> **DaGrimReefah said:**
> In your xorg.conf, change your device drivers to vesa. ```
Section "Device" Identifier "Configured Video Device" Driver [COLOR="Red"]_"vesa"_[/COLOR] EndSection
```            Ok. I'll give it a try tonight.

---

### Post by stuart.reinke on 2009-07-13
Still no joy. :(

I don't understand why all of a sudden Ubuntu quit working. I even tried taking out the hard drive and boot a live cd...nothing.

Has something gone wrong with my bios?

Why does PCLinuxOS work when Ubuntu doesn't 

I Hope someone can help me, Thanks for everything so far DaGrimReefah

Any more ideas?[-o<

---

