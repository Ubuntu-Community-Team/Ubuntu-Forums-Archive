---
title: "[SOLVED] Help! - I've crippled my Ubuntu!"
date: 2008-09-24
forum: General Help
---

### Post by Saiyan on 2008-09-24
Hey All,

I'm relatively new to Ubuntu and i've messed something up really badly.

I went into VirtualBox to install Vista (don't ask why ;)) and it asked me to install something VirtualBox needed, so I went into the synaptic manager and I clicked on a few of those module packages (I didn't know which one to choose). 

Then that menu came up (three way merge, Keep old, Keep new) so I decided to be an idiot and clicked on three way merge to see what would happen (even though it does say "experimental") and from there everything went wrong.

First of all on the startup screen I had two progress bars - even though only one got filled and then my resolution went wrong... and now my sound and wireless have completely stopped working, but my resolution seems to be fine.

When I click on the volume icon I get "No volume control GStreamer plugins and/or devices found".

And my wireless card disappeared.

What have I done ? :(

(I'm using a XPS 1510 laptop - Ubuntu 8.04)

Any help would be greatly appreciated!

Thanks!

---

### Post by soho2014 on 2008-09-25
I'm really new to Ubuntu too, but can you go to the history of Snyaptic under the file menu, and find that last install, such that you can uninstall it?

There is also a "fix broken packages" command that might hel.:)

---

### Post by prshah on 2008-09-25
> **Saiyan said:**
> 
 clicked on three way merge to see what would happen (even though it does say "experimental") and from there everything went wrong.



Can you boot using a previous kernel? From the GRUB menu, go you have any listings for a previous kernel? Try to boot off that, and post back for further troubleshooting.

---

### Post by Saiyan on 2008-09-25
Thanks for the replies! - soho2014, I already tried doing that ;) lol.. I tried undoing everything I did... but it didn't really work.

prshah, I did what you told me to do - and you were right! - thanks alot.

On the top of the list was Ubuntu 8.04.1, kernel 2.6.24-21-386 and that's the one that was all buggy

and two places below it was Ubuntu 8.04.1, kernel 2.6.24-21-generic - which i'm assuming was the correct one - it worked! - my sound and wireless are functioning again!

How did that 386 one make it to the list anyway? - lol - I should remove it from the list? right?

Thanks again! :D

---

### Post by kokkus on 2008-09-25
Each kernel is a new update you do with the update manager. If your pc is buggy after you updated the system using update manager you can go back in time to before you did that.
All it does is to skip the new installed packages.
You can use Startup Manager to remove the useless kernels (if you know you don't need them) [COLOR="Red"]And do not delete the wrong one.[/COLOR]

---

### Post by prshah on 2008-09-25
> **Saiyan said:**
> 
How did that 386 one make it to the list anyway? - lol - I should remove it from the list? 

 
Probably was put in when you blindly installed stuff from synaptic. For example, in virtual box, instead of selecting the "generic" module, you may have selected the "i386" module, which would have dragged in the entire "i386" kernel as a dependency. (Just a guess).

So I guess you should remove it; but as a pointer:" If it ain't broke, don't fix it". I suggest you just change the default option and leave it at that: Press Alt+F2, give the command ```
gksudo gedit /boot/grub/menu.lst
```, look for a section like > ## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# default		2
 From the last line of this section ("#default 2"), remove the "#" (hash) from the beginning of the line, and then change the "2" to whichever line you are using in GRUB to boot (the first line is 0). Then, save, exit, open a terminal (Applications-Accessories-Terminal) and give the command```
sudo update-grub
```

Now, when you reboot, it should boot the kernel you selected.

If you still want to remove the i386 kernel, delete the lines related to it in the (above-referenced) grub menu file, save and update grub as shown above.

Do either one or the other, don't do both.

If you want to remove the i386 kernel from your system entirely, post back the entire kernel line from the grub menu file for instructions.

---

