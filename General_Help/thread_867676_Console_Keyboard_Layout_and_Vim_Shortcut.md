---
title: "Console Keyboard Layout and Vim Shortcut"
date: 2008-07-23
forum: General Help
---

### Post by ookamisan on 2008-07-23
Hello folks,

I have 2 problems I am trying to solve for quite a while already.

First I have Ubuntu 8.04.

I selected during installation the US alt_intl keyboard scheme. (selected from the ubuntu alternate installation cd)

Now I have two problems with that:
First is: The Keyboard Layout in the console (the tty, not in X-Terms or anything) has "dead keys" activated, so typing something like even " is quite a burden and annoying. I tried googling the problem, but everything I found about that was to change the layout via "loadkeys" or via the dpkg-reconfigure console-tools
"loadkeys us" solves the problem in that console window up to the next reboot.
"dpkg-reconfigure" doesn't solve the problem at all, because there is not such an detailed choice of keyboards available as in the ubuntu installer.
I even tried "cp /usr/share/keymaps/i386/qwerty/us.kmap.gz /etc/console-setup/boottime.kmap.gz" but it didn't help.

The next problem is somewhat quite common in google but I didn't get a real solution from the results:
In the vim help there is the shortcut for jumping on a link C-]
That works in the console. (Maybe it is important in this case that I have a german keyboard (but the layout and everything is set to us))
But in the terminal window in gnome pressing C-] zoomes the window like C-+ is supposed to do (and what is in fact on a german keyboard the same key as the ] key on the us). But when I press the combination of C-AltGr-9 (wich worked in the past when I had german layout and german keyboard for C-] (because AltGr-9 results on a german keyboard in a ])) nothing happens. So I can't browse the help in the terminal window.

Maybe some of you guys have some ideas, would be awesome.

Greetings from germany,

ookamisan

---

### Post by ookamisan on 2008-07-23
I have some files found in /etc/console-setup , compose.*, they seem to contain the combinations for the composition with the dead keys, but that doesn't help me... :(

Is there maybe a way to start seperate parts of the ubuntu installer? Maybe I should check the source code of the installer for a clue...

---

### Post by panet on 2008-09-11
i had a similar problem and after reading your post, i tried this and it worked for me.
maybe this step isn't required, i've changed the line ```
XKBLAYOUT="ca"

``` in /etc/default/console-setup to my desired keyboard layout.
i also specified a empty string as as md5sum for the ```
BOOTTIME_KMAP_MD5=""
```
then ```
sudo dpkg-reconfigure console-setup
```
and rebooted.

---

