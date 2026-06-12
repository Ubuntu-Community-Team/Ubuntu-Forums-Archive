---
title: "Problems after CHOWN"
date: 2018-05-23
forum: Hardware
---

### Post by ethicalnoob on 2018-05-23
I do not know what I did but when I type 

```

sudo chown -R frank:frank /../../

```

everything just stops working so I restart my laptop, but now nothing is display. I somehow open up a terminal and manage to login. Everything is &#8220;normal&#8221; except no displays AT ALL. I would like this to be reverse is there ANY POSSIBLE solutions ?? 
Help me All of You

---

### Post by lisati on 2018-05-23
Hello ethicalnoob

I've changed the title of your thread to help attract someone who might be able to give appropriate help.

Use of chown neeeds a bit of care, as it can mess up your system's ability to function properly. Hopefully someone will see your thread and be able to guide you through to a solution that doesn't end in you having to backup what you can and then reinstall.

---

### Post by QIII on 2018-05-23
Yes.  There is a possible solution.  It depends on whether you have good backups of your important files.  Where on Earth did you find instructions to do that?

The inode leading to the parent directory of any directory has the ".." name.  What you've done is recursively changed pretty much everything from your home directory *backwards* in a line all the way to /.  The problem is that your system depends on specific users owning specific directories/files.  Most of what you probably got above your /home would probably be root and you could conceivably change everything above that to be owned by root ... but you'd be taking your chances.  Fortunately this is probably less than the total disaster you'd have if you had recursively changed permissions.  

A mistake of that magnitude is really handled best by grabbing your backups (or backing up what you need now, since you own everything...) and reinstalling.

---

### Post by Irihapeti on 2018-05-23
I did something similar a number of years ago. (Not sure what I was thinking at the time.) I discovered that CHOWN-ing everything above the home directory to root does NOT work. The only way out is to reinstall.

If you don't have a backup, it should be possible to use a liveCD or liveUSB to copy your home directory files to another device.

---

### Post by ethicalnoob on 2018-05-24
> **QIII said:**
> Yes.  There is a possible solution.  It depends on whether you have good backups of your important files.  Where on Earth did you find instructions to do that?

The inode leading to the parent directory of any directory has the ".." name.  What you've done is recursively changed pretty much everything from your home directory *backwards* in a line all the way to /.  The problem is that your system depends on specific users owning specific directories/files.  Most of what you probably got above your /home would probably be root and you could conceivably change everything above that to be owned by root ... but you'd be taking your chances.  Fortunately this is probably less than the total disaster you'd have if you had recursively changed permissions.  

A mistake of that magnitude is really handled best by grabbing your backups (or backing up what you need now, since you own everything...) and reinstalling.

I was downloading some tools for playing and it was in the “computer” section of the file. When I try to run it, it saids something like a file does not belong to you. So I search up some solution and found out about chown(I already know Chmod). The solution said something like sudo chown -R user:user file. I notice that I need to somehow get to the / directory if I want to change the permission of that file. However, I decided to try to take it out of “root” directory and change it; it didn’t work. Now I basically did what I though of before,but to make sure it works I did sudo chown -R frank:frank /../../; it did work, but by the time I notice it works, my computer stops working and here I am.

I decide to reinstall the system as you told me ( I didn’t have a backup because I think I am too smart for that ) and everything works fine now. Thanks

---

