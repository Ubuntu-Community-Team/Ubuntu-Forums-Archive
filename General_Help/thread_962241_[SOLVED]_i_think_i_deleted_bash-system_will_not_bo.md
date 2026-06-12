---
title: "[SOLVED] i think i deleted bash-system will not boot"
date: 2008-10-29
forum: General Help
---

### Post by jaikat on 2008-10-29
well, i was having problem trying to install thinliquidfilm (video conversion tool). so this web-page ([http://linuxappfinder.com/blog/create_video_for_an_ipod_using_thinliquidfilm](http://linuxappfinder.com/blog/create_video_for_an_ipod_using_thinliquidfilm)) says:

-----------------
Thin Liquid Film expects the default shell to be Bash and won't work properly with Dash, Ubuntu's default shell. To change it type the following two commands:

sudo rm -f /bin/sh
sudo ln -s /bin/bash /bin/sh
--------------------

i copied the commands into my terminal and they executed without a problem

now i can't boot, at all, no command line, nothing..
help please.](*,)

---

### Post by cevans on 2008-10-29
Those instructions are rather irresponsible. The correct way to fix this problem would be for the writer of the software to use #!/bin/bash instead of #!/bin/sh; expecting sh to be bash is not proper, and one instruct users to do something that will have major effects on their systems even if it does work (I think that using bash as sh can make things significantly slower for all scripts run on the system) instead of taking the 30 seconds it would take to fix the non-compliant scripts. 

However, my rant above won't help you much. There are several ways to fix your issue. If you have a livecd, it should be relatively simple to boot into it, mount your hard drive, and fix the problem. In fixing it, you can try 'ln -s /PATHTOROOT/bin/dash /PATHTOROOT/bin/sh', which will try to restore the original link. If that doesn't work, you can copy the dash and bash executables from the livecd filesystem, and then restore the bin/sh link. I suppose you can also just copy either dash or bash to sh, instead of linking, which might work if linking fails, but I can't see why that would happen.

If you don't have a livecd or other way of modifying the file system externally, you can probably boot by adding "init=/bin/bash" into the kernel options before booting, which will give you a rudimentary root shell. However, be aware that this shell will have some peculiarities, like a complete lack of job control (Ctrl-Z won't work), and a variety of things won't run---basic utilities like ln will be fine, however.

---

### Post by jaikat on 2008-10-29
first of all, thanks for the quick reply.

i thought i smelled something fishy about the "solution" provided by that page, but to be honest i just didn't think it would result in a complete breakdown. i also did some googling before i posted my problem here, but i seem to be the only one..wierd huh!

anyway, i have a question:

i understand the part about copying the executables back into the system and creating a "new" link to get things back on track. but wouldn't it be possible to delete the link i created(which caused the problem) to solve this.. what i'm trying to say is, in case i followed your first solution (ln -s /PATHTOROOT/bin/dash /PATHTOROOT/bin/sh), would the troublesome link still be there?

ps: i'm just trying to understand how these things work thats all ):P

---

### Post by cevans on 2008-10-29
One of the things that makes the instructions particularly bad is that you weren't actually creating a new link; you were instead replacing an existing link, which made /bin/sh point to /bin/dash, with a different one. Removing the new link will just make things worse, because a large number of scripts rely on /bin/sh existing, and working.

However, I do notice that my first solution I gave you won't actually work, because the problematic link is already there. You can use sudo ln -sf instead of sudo ln -s to overwrite the bad link, however, or you can just remove the link and then add back the original one.

---

### Post by jaikat on 2008-10-30
thank you very much, i'm back to earth..finally.

but i still have a couple of questions if you don't mind..

#1 using the command 'ln -s /bin/bash /bin/sh' , would the link be stored in the 'bin' folder or elsewhere?

#2 in my first attempts to create a new symlink to solve the problem, i used the full path in the command like this:
 'ln -sf /mnt/mountpoint/bin/dash /mnt/mountpoint/bin/sh

but that didn't work.
then i browsed to the path, and simply created the new link like this:
 'ln -sf dash sh'

which solved the problem.

so my question is, why wasn't the first form successful?

---

### Post by cevans on 2008-10-30
> **jaikat said:**
> thank you very much, i'm back to earth..finally.

but i still have a couple of questions if you don't mind..

#1 using the command 'ln -s /bin/bash /bin/sh' , would the link be stored in the 'bin' folder or elsewhere?

#2 in my first attempts to create a new symlink to solve the problem, i used the full path in the command like this:
 'ln -sf /mnt/mountpoint/bin/dash /mnt/mountpoint/bin/sh

but that didn't work.
then i browsed to the path, and simply created the new link like this:
 'ln -sf dash sh'

which solved the problem.

so my question is, why wasn't the first form successful?

I'm quite sorry, I forgot that this was a symbolic link. For hard links, which are made by default by ln, the link is stored at the second argument, and links to the file that the first argument lists. For symbolic links, however, which are made by -s, the link is stored at the second argument, but it makes the link point the first argument's *path*, whether or not it is actually valid or a file. Thus, when you created the link with my instructions, it created a link called sh that linked to path /mnt/mountpoint/bin/dash, not the file. When you restarted, it didn't work because in your real system, there was no /mnt/mountpoint/bin/dash. When you created the link while in the bin folder, it made a link which was also valid in your real system.

---

### Post by Leechpool on 2009-02-26
Has anyone managed to get thinliquidfilm working properly in intrepid yet? i.e. xvid and h264 etc. If so how? It was all working great in Hardy but doesn't work anymore. Won't even open video files saying they are corrupt or something.
Thanks
:p

---

