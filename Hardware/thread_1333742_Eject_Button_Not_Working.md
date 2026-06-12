---
title: "Eject Button Not Working"
date: 2009-11-21
forum: Hardware
---

### Post by nishant.singh28 on 2009-11-21
I have a Dell Studio 1555 notebook with slot load optical drive. the eject button is a key on the main keyboard. (see attached pic)
The key worked OK for a couple of days after install. It did not work at all in Jaunty. However, today it stopped working altogether. xev does not map it so I am forced to use a custom shortcut( super+e). Is there a way to patch this problem as I have decided to use Ubuntu as my mainstream OS and I would really like it if my laptop was fully functional.

---

### Post by maaaw2010 on 2009-11-24
same issue! i am new to linux altogether so i dont even know how to configure shortcuts as 
you did! my only way is to rightclick on the mounted image of the cd/dvd then eject.
any help?
thnx in advance

---

### Post by v1nsai on 2009-11-24
Usually when Linux is using the CD drive it won't "let go" of the drive, and so pushing the button does nothing.

Try going to Places > Computer and right clicking the drive and selecting "unmount" or try running the command "umount -a" which will automatically unmount everything not required for the system to run.

After your sure the drive is unmounted, try ejecting the disk again.  I've had this problem lots of times and I finally figured out it was because Linux was still using the drive -_-

---

### Post by phenest on 2009-12-15
I have a Dell Precision M90 that I just fitted a slot drive to. I have the same issue, and the 'unmount first' workaround fixes the problem. But I never had this problem with the previous drive which is of the drawer type. I thought ejecting unmounted it first?

EDIT: If I right click and select eject without unmounting first, it does eject. In fact, every eject method works (without unmounting) except the keyboard shortcut.

---

### Post by nishant.singh28 on 2010-01-15
Bump!!

---

### Post by v1nsai on 2010-01-18
I think this is an ACPI related issue.  I just recently got a Dell Studio 15, and the special brightness, volume control and eject keys often stop working.  These are controlled by ACPI.  There are various combinations of boot options to use, such as 'noapic', 'nolapic', 'acpi=force' that I have had marginal success in getting ACPI to stay on.  As of right now ACPI has been working for a few days now, but it will go out without warning and will stay out until i reboot.

---

### Post by DestructionsRightHand on 2010-01-18
does

```

eject

```

work?

---

### Post by nishant.singh28 on 2010-01-18
> **DestructionsRightHand said:**
> does

```

eject

```work?
yes

---

### Post by falconindy on 2010-01-18
> **v1nsai said:**
> I think this is an ACPI related issue.  I just recently got a Dell Studio 15, and the special brightness, volume control and eject keys often stop working.  These are controlled by ACPI.  There are various combinations of boot options to use, such as 'noapic', 'nolapic', 'acpi=force' that I have had marginal success in getting ACPI to stay on.  As of right now ACPI has been working for a few days now, but it will go out without warning and will stay out until i reboot.
[ACPI]("http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface") != [APIC]("http://en.wikipedia.org/wiki/Advanced_Programmable_Interrupt_Controller")

Please don't confuse these unrelated acronyms.

---

### Post by nishant.singh28 on 2010-01-19
Thanks for clarification. Any suggestions?

---

### Post by Velophile on 2010-01-19
Try:

sudo gedit /etc/sysctl.conf

dev.cdrom.lock=0

---

### Post by nishant.singh28 on 2010-01-25
> **Velophile said:**
> Try:

sudo gedit /etc/sysctl.conf

dev.cdrom.lock=0
Doesn't work.

---

### Post by clevertomato on 2010-01-26
I have a Studio 1555 with slot loading optical drive and ATI 4570 that was delivered Dec 2009. It may not be identical in every way with yours, but the eject button works fine for my slot loading drive in Karmic. I had to add "noapic" to the end of my boot line in Grub to get the screen brightness Fn keys and lid closure behavior to work. I know someone already mentioned the idea of this, but have you actually tried this? I'd be careful about messing with ACPI options but I've experienced no adverse effects of using "noapic" option. (As someone else said, ACPI and APIC are two very different things.)

Before editing the Grub config file, if you want, you can just try it one time temporarily by hitting "e" at the Grub menu, arrowing down to the end of the line that says "nosplash" and add " noapic" to the end, then go ahead and boot like that. If it works, edit your Grub config file (filename depends on which Grub version you're on... if running Grub 2 w/Karmic it should be /boot/grub/grub.cfg

I hope this helps you. If it doesn't help, I have no other ideas for you.

---

### Post by nishant.singh28 on 2010-01-26
I've done that too. But the problem is it worked ok for a week and then *poof*.

---

### Post by clevertomato on 2010-01-26
This is really "reaching" and I wouldn't think it would be relevant since the eject button is not a function key, but out of desperation, have you tried changing the setting in your BIOS back and forth... the one that determines whether or not the function keys are "function keys first"? (F1, F2, F3... or Fn+WiFi, Fn+brightness, etc).

I'm just taking stabs in the dark at this point because I know the frustration you must be feeling.

---

### Post by nishant.singh28 on 2010-01-26
Done that too.
Not too frustrated :D. I don't us the drive anyway. But it's good to have a fully working laptop. I have a different keyboard shortcut set as a workaround. And I can always drag the Drive icon into the Trash in Cairo dock and it ejects.
PS-Nice signature....but if u're caught in a flock of geese, will u luk 4 lions to pick a fight with? :D

---

### Post by clevertomato on 2010-01-26
I wish I were as calm as you are when things don't work in Linux.  :)  That would irritate me quite a bit if the eject button didn't work.

You bet I would look for some lions if a flock of geese were about to trample me to death! :D

---

### Post by nishant.singh28 on 2010-01-26
Haste leads to waste.....:)

---

### Post by nishant.singh28 on 2010-01-26
OK. I finally figured it out. I opened configuration editor and under Apps->gnome_settings_dameon->keybindings, set eject as XF86Eject and Bingo!!!

---

### Post by linuxguiri on 2010-03-28
Is it still working for you? Because it no longer works for me and eject is set to XF86Eject.

---

### Post by clevertomato on 2010-03-28
linuxguiri what hardware do you have? My Dell Studio 1555 is still working fine with the Eject button and the screen brightness Fn keys.

---

### Post by linuxguiri on 2010-03-28
I also have a Studio 1555. Running Karmic 64. (Plus, the screen brightness keys don't work for me either.) :(

---

### Post by nishant.singh28 on 2010-03-29
Aha!! You need to use "noapic" option. Google it.

---

### Post by clevertomato on 2010-03-29
I wish I could help you, but if my post on page 2 about adding noapic to your grub entry does not work, I don't have any other ideas. I hope you get it working.

---

### Post by draki on 2010-04-13
I have the same problem:

I have an Apple Aluminium keyboard - everything has worked perfectly until Ubuntu Lucid

Keyboard shortcuts all seem correct - XF86Eject - and 'eject' at the CLI works fine.

Pressing the key triggers a notification in the top-right of the screen, but no eject of the drive :-(

Right clicking on the drive when a CD/ DVD is loaded allows me to eject it..

But for some unknown reason the keyboard button will not trigger the eject

any ideas?

---

### Post by nishant.singh28 on 2010-04-13
> **draki said:**
> I have the same problem:

I have an Apple Aluminium keyboard - everything has worked perfectly until Ubuntu Lucid

Keyboard shortcuts all seem correct - XF86Eject - and 'eject' at the CLI works fine.

Pressing the key triggers a notification in the top-right of the screen, but no eject of the drive :-(

Right clicking on the drive when a CD/ DVD is loaded allows me to eject it..

But for some unknown reason the keyboard button will not trigger the eject

any ideas?
Did you try noapic?

---

### Post by cphayes0914 on 2010-04-16
> **Velophile said:**
> Try:

sudo gedit /etc/sysctl.conf

dev.cdrom.lock=0



Thanks velophile for the advice, this problem has been bugging the hell out of me, that fix solved it.

---

