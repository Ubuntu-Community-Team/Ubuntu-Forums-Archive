---
title: "I can't find an option on the Live CD"
date: 2009-02-15
forum: Installation &amp; Upgrades
---

### Post by shateredsoul on 2009-02-15
Hi again,

So I'm trying to remove windows with the live cd using the instructions at

[https://help.ubuntu.com/community/HowToRemoveWindows](https://help.ubuntu.com/community/HowToRemoveWindows)

but i pretty much just see this screen

[IMG]http://taqeem.files.wordpress.com/2007/11/vista_ubuntu_05article-width.jpg[/IMG]

I can't find the "system->Administartion->partition editor

I can't even find the system option...

am I doing something wrong?

---

### Post by kestrel1 on 2009-02-15
The screen you show is just the boot menu for the CD. Press enter & you should start the Live CD.

---

### Post by Regnulify on 2009-02-15
Once you boot into ubuntu the graphical partition editor will be available. If you want to whack window you can just install right over it.

---

### Post by Zip247 on 2009-02-15
in your tutorial here [https://help.ubuntu.com/community/HowToRemoveWindows](https://help.ubuntu.com/community/HowToRemoveWindows)

it states this

Place the LiveCD into your CD/DVD drive, and reboot the computer. Each computer is different, but you may need to change your BIOS to have the system boot from the CD drive before the hard disk. Refer to your computer manufacturer's documentation for this

Basically, it is saying to run gparted from the live cd mode. 

wdecker

---

### Post by shateredsoul on 2009-02-15
oh ok.. i just ran it from within ubuntu instead of the live cd.   In the box on the bottom it has the operation now "Delete /dev/sda2"

then at the very bottom it says, 1 operation pending

I guess now I wait until it actually deletes it? Not sure what to do now other than wait

---

### Post by wpshooter on 2009-02-15
I think there is an option in one of the menu choices on the top menus bar that will let you APPLY the pending changes.

---

### Post by ScarySquirrel on 2009-02-15
Make sure to use the CD's programs to delete the Windows partition.

---

### Post by Elfy on 2009-02-15
> then at the very bottom it says, 1 operation pending
I guess now I wait until it actually deletes it? Not sure what to do now other than wait

If you are using the partition editor on the live cd and you've set up the change that you want and it is saying that 1 operation is pending - I would say you gace haven't hit the Apply button yet.

---

### Post by ugm6hr on 2009-02-15
> **shateredsoul said:**
> oh ok.. i just ran it from within ubuntu instead of the live cd.

Try again from the LiveCD.  Select "Start or Install Ubuntu"

This boots into Ubuntu LiveCD.

Then follow the instructions.

And yes - you need to click APPLY to actually format stuff (essentially, it is a double-check to ensure you don't accidentally format your HD).

Provided you are just wiping / formatting the HD, it should still work from within Ubuntu (with the Windows partition unmounted), you just won't be able to move partitions around.

---

