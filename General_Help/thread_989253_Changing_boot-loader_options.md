---
title: "Changing boot-loader options"
date: 2008-11-21
forum: General Help
---

### Post by habileheretic on 2008-11-21
Hello guys,
I was wondering if there's any way to change the boot-loader options? I'm quite content with GRUB but the only problem I face is it loads Ubuntu by default!
I have a dual boot between XP and Ubuntu and after a set amount of time, GRUB loads Ubuntu. How can I make XP it's default choice?

I hope this image makes things clear

[IMG]http://i35.tinypic.com/33o0gg6.jpg[/IMG]

---

### Post by Elfy on 2008-11-21
Open your menu list to edit it and change the default. Grub counts from 0 so your XP is number 4

Find this line
> default		0
change to 4 - that should do it.

Backup the file first with
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.2111
```
Open the file for editing with
```
gksudo /boot/grub/menu.lst
```

change the line and save it - next time it should default to XP for you.

Now it's likely that you'll get a kernel update at some point and they will go at the top of the list - this is going to make your XP maybe the 6 or 7th option then and the file will need to be edited unless you move the whole thing within the file. I fyou want to do that post back.

---

### Post by unix192 on 2008-11-21
change your /boot/grub/menu.lst to reflect what you want to boot by default the option at the top is what it will load by default. in your case ubuntu kernel 2.6.12-9-386.

applications -> accessories ->terminal

type in "sudo gedit /boot/grub/menu.lst"

find your windows/nt/2000/xp entry at the bottom and place it above ubuntu kernel 2.6.12-9-386 by the way make sure to delete the windows/nt/2000/xp entry at the bottom or there will be two of them on your grub options.

\\:D/

---

### Post by Elfy on 2008-11-21
> **unix192 said:**
> change your /boot/grub/menu.lst to reflect what you want to boot by default the option at the top is what it will load by default. in your case ubuntu kernel 2.6.12-9-386.

applications -> accessories ->terminal

type in "sudo gedit /boot/grub/menu.lst"

find your windows/nt/2000/xp entry at the bottom and place it above ubuntu kernel 2.6.12-9-386 by the way make sure to delete the windows/nt/2000/xp entry at the bottom or there will be two of them on your grub options.

\\:D/

If you do that it must be above the automagic lines.

---

### Post by drs305 on 2008-11-21
I just posted a comment on another thread about startup-manager. It's a great gui-based app that can modify settings without manually editing grub's menu.lst

[http://ubuntuforums.org/showthread.php?t=989266#2]("http://ubuntuforums.org/showthread.php?t=989266#2")

---

### Post by Elfy on 2008-11-21
I used SUM once and had awful problems with splash afterwards - might not have been connected in truth, but I've not used it since.

While I'm all for GUI tools, I'd be more inclined to use them for 'complicated' tasks myself than things that a file edit can accomplish. In addition being able to edit files would be a useful thing to be able to do if you're dropped to a root prompt when something is broken.

---

### Post by unix192 on 2008-11-21
Thanks forestpixie nice addition to my post. I am not much for GUI based any thing but there are several ways to accomplish this task as you can see.

---

