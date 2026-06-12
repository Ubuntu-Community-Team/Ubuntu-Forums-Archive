---
title: "[SOLVED] Log-in Screen resolution way too high"
date: 2008-08-03
forum: General Help
---

### Post by Joselito84 on 2008-08-03
Hi again,

have gotten all my video card drivers installed and all is good once im into Ubunto all effects working good and all, just one problem...

When booting up, when i get to the log-in prompt its right at the bottom right hand corner of the screen and i can only JUST see it, like as if the screen resolution MASSIVE, when im in Ubunto my resolution is at 1600x1200 and that is beautiful, just the log-in screen is annoying me!

any ideas?

---

### Post by CatKiller on 2008-08-03
There is a program called startupmanager that should let you change the resolution of the login screen (amongst other things). It's in the Universe repository. You can install it with Synaptic. I haven't used it, but it might help.

---

### Post by Joselito84 on 2008-08-04
Installed startup manager but nope, there is no setting that i could see to change log-in screen resolution unfortunately...

any other ideas?

---

### Post by rats54 on 2008-08-04
Well I tried it and it did not work for me.  Also, the man page is crap NO HELP WHAT SO EVER.

This is getting to be an old story with Hardy.

---

### Post by Novus on 2008-08-04
you can edit /etc/gdm/gdm.conf donno if you can set a res in there but you can change where the login window appears on the screen.

```
gksu gedit /etc/gdm/gdm.conf
```

search for SetPosition

---

### Post by trevelyan on 2008-08-04
I remember i had this problem and all i did was change the resolution in the xorg file to something else, then log out, then log back in and change the resolution to what i wanted, then log out and back in... and that was it.

---

### Post by CatKiller on 2008-08-04
> **Joselito84 said:**
> Installed startup manager but nope, there is no setting that i could see to change log-in screen resolution unfortunately...

any other ideas?

As far as I know, the only resolution settings that will affect GDM are the framebuffer resolution, that determines the resolution of the startup display and the virtual consoles (tty1-6), and the resolution of the X server.

You've already said that your X server resolution is fine, and the framebuffer resolution can be easily changed with startupmanager. If changing the resolution in startupmanager hasn't helped, then the problem might lie with your X configuration.

You say that when you're logged in, your resolution is set at 1600x1200. Are higher resolutions listed as available? GDM is likely to use the highest available resolution, and lower resolutions can be set on a per-user basis.

---

### Post by Joselito84 on 2008-08-04
1600x1200 is the highest res available.

hmm... we'll i'll keep trying to play around with the settings and hopefully i get it right i guess...

---

### Post by CatKiller on 2008-08-04
The only other thing I can think of is the DPI setting. I know that for a while (becasue my video card wasn't passing EDID numbers from the monitor) if I let X use the highest resolution that my monitor could do, the text on the login screen was _tiny_. The image was fine though, so I couldn't really say that yours is the same problem. In the end I told X how big my monitor was by putting ```
        DisplaySize     402 300
``` in my xorg.conf. The numbers are in millimetres.

---

### Post by derrick81787 on 2008-08-04
> **Joselito84 said:**
> Hi again,

have gotten all my video card drivers installed and all is good once im into Ubunto all effects working good and all, just one problem...

When booting up, when i get to the log-in prompt its right at the bottom right hand corner of the screen and i can only JUST see it, like as if the screen resolution MASSIVE, when im in Ubunto my resolution is at 1600x1200 and that is beautiful, just the log-in screen is annoying me!

any ideas?

This was a common bug in the beta and the early release of Hardy.  I thought it had been fixed in an update, though. Unfortunately, I didn't experience this bug, so I don't really know what the solution was. Are you using an Nvidia or ATI graphics card?  I think those users (mostly Nvidia but some ATI) were the ones affected.

- Derrick

*****Edit:**

Here are some links to some possibly related bugs on launchpad:
[LIST]
[*][https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/16472](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/16472)
[*][https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/216871](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/216871)
[/LIST]
And here are some links to possible solutions that I found:
[LIST]
[*][https://help.ubuntu.com/community/FixVideoResolutionHowto#GDM%20uses%20a%20different%20Resolution%20than%20my%20Desktop](https://help.ubuntu.com/community/FixVideoResolutionHowto#GDM%20uses%20a%20different%20Resolution%20than%20my%20Desktop)
[*][http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg916661.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg916661.html)
[*][http://ubuntuforums.org/showthread.php?t=383492](http://ubuntuforums.org/showthread.php?t=383492)
[/LIST]
This is probably the best solution, assuming you have Nvidia and are runny Hardy:
[LIST]
[*][http://ubuntuforums.org/showpost.php?p=4782971&postcount=10](http://ubuntuforums.org/showpost.php?p=4782971&postcount=10)
[/LIST]
If you don't have an Nvidia card, you might want to try the first line anyway.

I hope this helps.

---

### Post by Joselito84 on 2008-08-05
Thanks heaps for your help people! that last suggestion fixed my problem!

log-in screen went back to normal after typing:

> 
sudo dpkg-reconfigure xserver-xorg
sudo nvidia-xconfig


however, when i logged into ubuntu settings were changed back to 800x600, doing a quick search of the forums i came accross someone with the same problem then ran:

> 
gksu displayconfig-gtk

and found my monitor wasnt selected, it was just using a generic monitor, selected my monitor and guess what!? back to 1600x1200.

once again you've all been a great help! thanks alot!!

adios! :guitar:

---

