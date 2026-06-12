---
title: "Upgrade to 9.04 error: kernel 2.6.27.11"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by Monkey_Tales on 2009-04-24
Hello,

I have upgraded from 8.10 to 9.04, but when i try to startup my pc, i don't get the right kernel in GRUB (Kernel 2.6.27.11). I have tied to upgrade-grub but this doesn't work:

[COLOR=DarkRed]:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/vmlinuz-2.6.27-14-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... Updating the default booting kernel
done

[/COLOR]I still get the 2.6.27.11 kernel in GRUB, not the 2.6.28.11.
Can someone help me?

---

### Post by jimmyboy09 on 2009-04-24
I have a very similar problem.  I finished the upgrade and restarted my pc, only to see that grub wasn't listing jaunty as an option in the menu.

So when I select to boot intrepid (and old kernel 2.6.27-11-generic) anyways, it gets past boot splash, but after that just stays on a blank screen.

So I go back to grub and (crudely, mind you) edit the kernel name twice in one of the submenus, boot from there, and end up with the same result:  get past boot splash but freeze on blank screen.

Can anyone help me too?  

ps.  In retrospect I now realize that it was a bad decision, but during upgrade I choose to keep my menu.lst instead of getting a new one.  I can see how this would be the root of my problems.  So on another note, does anyone know how I can fix that problem as well?

Thanks.

---

### Post by HyRax on 2009-04-24
> **Monkey_Tales said:**
> Hello,

I have upgraded from 8.10 to 9.04, but when i try to startup my pc, i don't get the right kernel in GRUB (Kernel 2.6.27.11). I have tied to upgrade-grub but this doesn't work:

I still get the 2.6.27.11 kernel in GRUB, not the 2.6.28.11.
Can someone help me?

Do a complete uninstall of kernel 2.6.28.11, then re-install it. Clearly the post-process of installation did not complete properly the first time.

---

### Post by _sleeper on 2009-04-24
i have the exact same problem with jimmy, but the paradox is that when i select the 8.04 kernel, it boots regularly in jaunty!

---

### Post by Monkey_Tales on 2009-04-24
> **HyRax said:**
> Do a complete uninstall of kernel 2.6.28.11, then re-install it. Clearly the post-process of installation did not complete properly the first time.

Tnx,

This sounds like a logical solution, but how do i uninstall it? Do you mean to completely uninstall 9.04 or just the kernel 2.6.28.11 and how do i do this operation?

Tnx for the quick reply

---

### Post by HyRax on 2009-04-24
> **Monkey_Tales said:**
> Tnx,

This sounds like a logical solution, but how do i uninstall it? Do you mean to completely uninstall 9.04 or just the kernel 2.6.28.11 and how do i do this operation?

Tnx for the quick reply

You're already booting up with a working kernel, so there's no need to redo everything. First check what kernel you're on with the following in a terminal:

```

uname -a

```
...since we obviously don't want to uninstall a kernel we're currently using.

If the current in-use kernel is not "2.6.28.11-generic" then go into Synaptic and look for the packages "linux-headers-2.6.28.11-generic" and "linux-image-2.6.28.11" (basically anything containing "2.6.28.11-generic", really). Do a "complete removal" of them (do a right-click and choose that from the menu), apply, and when finished then close Synaptic. Open up Update Manager, click the "Check" button to reload your package lists and then the 2.6.28.11-generic kernel should appear again as an update option. Proceed as normal.

---

### Post by huntz on 2009-04-24
A quick fix to this bug/problem:

move and backup your menu.lst

```
 mv /boot/grub/menu.lst /boot/grub/menu.lst.bck 
```

run update-grub (answer yes to generate a new config file question)

```
 sudo update-grub 
```

If you have a multi-boot system you have to integrate the new generated menu.lst with the old (inspect the /boot/grub/menu.lst.bck).

Remember to add your customization after the line "### END DEBIAN AUTOMAGIC KERNELS LIST"

Reboot and you'll see the new kernel.

I hope this will help.

---

### Post by Monkey_Tales on 2009-04-24
> **HyRax said:**
> You're already booting up with a working kernel, so there's no need to redo everything. First check what kernel you're on with the following in a terminal:

```

uname -a

```...since we obviously don't want to uninstall a kernel we're currently using.

If the current in-use kernel is not "2.6.28.11-generic" then go into Synaptic and look for the packages "linux-headers-2.6.28.11-generic" and "linux-image-2.6.28.11" (basically anything containing "2.6.28.11-generic", really). Do a "complete removal" of them (do a right-click and choose that from the menu), apply, and when finished then close Synaptic. Open up Update Manager, click the "Check" button to reload your package lists and then the 2.6.28.11-generic kernel should appear again as an update option. Proceed as normal.

Oke,

First i have done: 

:~$ uname -a Linux Maverick 2.6.27-11-generic #1 SMP Wed Apr 1 20:57:48 UTC 2009 i686 GNU/Linux

So i am not in 2.6.28.11 and then i did the complete removal in synaptic of all 2.6.28.11(-generic) packages and closed synaptic.
But in Update Manager i did not get the option for installing anything 2.6.28.11(-generic)
Did i do anything wrong? I followed your instructions to the letter, so that must be good.
What am i missing?

---

### Post by Monkey_Tales on 2009-04-24
Yes, i finally have got it running!

I manually installed the 2.6.28.11(-generic) packages in synaptic and i tried:

mv /boot/grub/menu.lst  /boot/grub/menu.lst.bck
and
sudo update-grub

Then i restarted the system and a new bootup-menu with ubuntu 9.04 - 2.6.28.11-generic
came up, but my windows-vista grub entry is gone. 
I will have to get it back into the Grub-menu somehow...

Tnx you all for the quick reply's 
 
:guitar:

---

### Post by huntz on 2009-04-24
You have to open the menu.lst.bck and look for something like this:

```

title Windows Vista/Longhorn (loader)
root (hd0,2)
chainloader +1
makeactive
```

Copy and paste to the bottom of your **/boot/grub/menu.lst**.

DON'T USE MY PREVIOUS GRUB ENTRY, BECAUSE IT'S FROM MY LAPTOP AND WE HAVE FOR SURE A DIFFERENT SETUP...

Bye.

---

### Post by jimmyboy09 on 2009-04-24
can any help me too?

Huntz:  The farthest that I get is grub, and those commands you gave don't run in grub.  Is there anyway I can do something similar from grub itself?  

Thanks.

---

### Post by Monkey_Tales on 2009-04-24
> **huntz said:**
> You have to open the menu.lst.bck and look for something like this:

```

title Windows Vista/Longhorn (loader)
root (hd0,2)
chainloader +1
makeactive
```Copy and paste to the bottom of your **/boot/grub/menu.lst**.

DON'T USE MY PREVIOUS GRUB ENTRY, BECAUSE IT'S FROM MY LAPTOP AND WE HAVE FOR SURE A DIFFERENT SETUP...

Bye.

Hello huntz

Tnx, dual-boot kubuntu 9.04 and windows is back and running without problems.

See ya neXt time, bye

---

### Post by huntz on 2009-04-24
> **jimmyboy09 said:**
> can any help me too?

Huntz:  The farthest that I get is grub, and those commands you gave don't run in grub.  Is there anyway I can do something similar from grub itself?  

Thanks.

Hummm, if you are stuck into the Grub screen, I suppose you have a broken Grub installation.

Before any action, you must recover you Grub installation:


[LIST=1][*]Pop in the Live CD, boot from it until you reach the desktop.
[*]Open a terminal window or switch to a tty.
[*]Type "grub"
[*]Type "root (hd0,6)", or whatever your hard disk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
[*]Type "setup (hd0)", or whatever your hard disk number is.
[*]Quit grub by typing "quit".
[*]Reboot.
[/LIST]

When you are into the live CD, you can also manually edit your /boot/grub/menu.lst and fix the kernel and initrd entry with correct data, changing this

```

kernel          /boot/vmlinuz-2.6.27-11-generic root=UUID=111111111-1111-11111-11111-111111111 ro quiet splash
initrd          /boot/initrd.img-2.6.27-11-generic

```

to something like:

```

kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=111111111-1111-11111-11111-111111111 ro quiet splash
initrd          /boot/initrd.img-2.6.28-11-generic

```

PS: mind your own UUID and not my fake one :)

---

