---
title: "Wacomcpl not saving settings"
date: 2009-03-25
forum: Hardware
---

### Post by shatterblast on 2009-03-25
Thanks for any advice.  I run a system with Intrepid 8.10, and I followed the advice from the [[color=#FCD116]C[/color][color=#6B8E23]o[/color][color=#FCD116]m[/color][color=#6B8E23]m[/color][color=#FCD116]u[/color][color=#6B8E23]n[/color][color=#FCD116]i[/color][color=#6B8E23]t[/color][color=#FCD116]y[/color] [color=#6B8E23]w[/color][color=#FCD116]i[/color][color=#6B8E23]k[/color][color=#FCD116]i[/color]]("https://help.ubuntu.com/community/Wacom") for installing my tablet.  It works fine with all features detected after editing xorg.conf.  Typing wacomcpl in a terminal displays all the basics, and the interface accepts configuration changes just fine.  The odd part happens after a reboot:  all the settings convert to default.

I reinstalled the wacom drivers a couple of times, once with the 10-wacom.fdi file and another with out.  I rebooted after each install just to be thorough.  Lastly, I tried "sudo wacomcpl" just to see what might happen, but I didn't notice any obvious differences.

The only other thing I can mention is that I tend to put a lot of system-related software into the operating system.  I have no idea if something might conflict.  Thanks again.

*Edit:*  Upon further investigation, a "how to" page of the [[color=#B22222]L[/color][color=#0099CC]i[/color][color=#B22222]n[/color][color=#0099CC]u[/color][color=#B22222]x[/color] [color=#0099CC]W[/color][color=#B22222]a[/color][color=#0099CC]c[/color][color=#B22222]o[/color][color=#0099CC]m[/color] [color=#B22222]P[/color][color=#0099CC]r[/color][color=#B22222]o[/color][color=#0099CC]j[/color][color=#B22222]e[/color][color=#0099CC]c[/color][color=#B22222]t[/color]]("http://linuxwacom.sourceforge.net/index.php/howto/wacomcpl") states that I might need to add a script for some reason.  I think I will follow up with that first.

---

### Post by Favux on 2009-03-25
Hi shatterblast,

LWP is correct.  Wacomcpl generates a file called .xinitrc.  You just have to put it in Sessions to run it each boot after making it executable.  See section 3 on this HOW TO:

[http://ubuntuforums.org/showthread.php?t=1038949]("http://ubuntuforums.org/showthread.php?t=1038949")

I hope this is helpful.

---

### Post by shatterblast on 2009-03-25
Okay, thanks.  I'll check into that.

---

### Post by shatterblast on 2009-03-25
I had to tinker a bit, but it worked successfully.  I had to rename the ".xinitrc" file in my home folder to "xinitrc.sh", and I put it into its own folder just so I wouldn't have to stare at it occasionally.  (Things mysteriously disappear that way. :lolflag:)  Also for some reason, I had to remove the last line in the file to "/etc/X11/xinit/xinitrc", but that change might not have been necessary.  I just did it since the script constantly looped.

I'll have to copy and paste in the future for adjusting settings, but it does the job.  And.....  thanks one more time!  :biggrin:

---

### Post by Favux on 2009-03-25
Hi shatterblast,

Sounds like you had a little struggle.  Not sure why.  Somehow the terminal command didn't make .xinitrc executable?

Look at post #21 on the same thread as the HOW TO see if that explains your loop.  For some reason in "/etc/X11/xinit/xinitrc" occasionally you'll find:
```
# invoke global X session script
. /etc/X11/Xsession
```
if you comment it out like:
```
# invoke global X session script
#. /etc/X11/Xsession
```
That fixes things.  Is that what happened?  I have know idea how the line gets placed there.

Well anyway you got it working.  Good job.

PS:  I guess my concern is that if you use wacomcpl it won't save to your new file.  It will still save to /home/username/.xinitrc and you'll have to manually copy things over.

---

