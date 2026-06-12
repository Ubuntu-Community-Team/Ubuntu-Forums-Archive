---
title: "(probably easy) grub question"
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by MacHaddock on 2009-05-08
I can't get 9.04 working if I don't "enter" the grub and go down the menu to the second choice that's not a "failsafe" mode. That is the third choice counting all of them.

Sooooo. I was wondering how I tell the grub to choose this one as a default.

Thanks for your help.

---

### Post by jenkinbr on 2009-05-08
> **MacHaddock said:**
> I can't get 9.04 working if I don't "enter" the grub and go down the menu to the second choice that's not a "failsafe" mode. That is the third choice counting all of them.

Sooooo. I was wondering how I tell the grub to choose this one as a default.

Thanks for your help.
Once booted into the system, open a terminal and run the command ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```This command will back up your menu.lst file, the file that needs to be edited.

Now, hit <alt+F2> and type ```
gksudo <editor> /boot/grub/menu.lst
``` repacing <editor> with whatever editor Xubuntu uses (Gnome uses Gedit)

Enter your password when prompted.

Once opened, you should see a text file open.  There is a line that reads ```
default 0
```

You will need to change this entry to a different number.  I believe that would need to be '2' based on what you said, but I could be wrong, so be sure you read the rest of this.

Towards the end of the file, you will see entries that begin with a 'title' line.  Starting at 0, count up by one for each entry until you see the title that you normally have to boot.

You say that the entry you choos is the third list item, which would mean that you would be selecting the third title line.  That would mean you need to change ```
default 0
``` to ```
default 2
```

Hope this helps.

Help articles that have helped me in the past:
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

---

### Post by ronparent on 2009-05-08
The grub choices are found in /boot/grub/menu.lst. To shuffle the boot choices is merely to select one you want (near the end of the file) and relocate it in the order you would like it to appear in. Be careful to select all of the lines for that selection and move it as a block. Use the command [B]sudo gedit[/menu.lstB] to do this as administrator. Save when done and if done right you should see the boot order you want at nest boot. If you are nerveous about editing a system file, make a copy of the original before you begin (ie /boot/grub/menu.lst.bu). Good luck.

---

### Post by MacHaddock on 2009-05-08
Yeaaaaah it worked!

If someone could only help me with my [_other problem_]("http://ubuntuforums.org/showthread.php?t=1070617") I would be set. hint hint wink wink noch noch know what I mean.:wink:

---

### Post by jenkinbr on 2009-05-08
Glad to help.

I'll take a look at your other problem as well and see if I know anything.

---

