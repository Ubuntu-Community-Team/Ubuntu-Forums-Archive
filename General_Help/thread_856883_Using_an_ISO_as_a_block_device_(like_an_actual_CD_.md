---
title: "Using an ISO as a block device (like an actual CD drive)"
date: 2008-07-11
forum: General Help
---

### Post by DeathOnJuice on 2008-07-11
I know how to mount an ISO image. However, that only makes a mounted folder, and I want to use one like a block device. You can't rip from /media/whatever, only from /dev/scd0, for example. Is it possible to actually rip from an ISO as if it were an actual CD drive? Main reason to do this is to have an easy way to convert it to bin and cue; just make the OS think it's a CD, then use Cdrdao to rip from it.

Thanks.

---

### Post by MasterXandrex on 2008-07-11
This is how to mount an ISO from the terminal 

```

sudo mount debianetch.iso /media/isoimage/ -t iso9660 -o loop

```

There is also a graphical tool that may help you

```

sudo apt-get install gmountiso

```

---

### Post by DeathOnJuice on 2008-07-11
Thanks, but that wasn't the question. I know how to mount an ISO, but I need to have it treated like a real, physical CD. IE, I could rip from it with, say, K3B or something.

---

### Post by VMC on 2008-07-11
I'm not sure I fully know what your after. Is it you want to rip a dvd movie or how is this going to be used. Is this like the daemon tools program that Windows users have?
If you could give an example of usage that would be great.

I know what you asked, just don't think there;s is a block device for ISO's. You can extract an ISO into a folder, for example, and rebuild it using mkisofs.

What would be great if we had a loop-back with R/W capabilities.

---

### Post by DeathOnJuice on 2008-07-12
Yes, this is pretty much like Daemon Tools. This is an example:

I originally ripped a game to bin/cue with cdrdao to play it with PSX. There is a way to patch this game with user-created content, but only when it is an ISO. There is a tool called bchunk to convert bin/cue to ISO, but not to convert it back. One way would be to burn the ISO to a disk, then to use cdrdao to rip it to bin/cue. It seems like there should be a way, though, to skip the burning step. I would rather not waste a CD.

I know I could use MagicISO, but there are other cases where I need this where that wouldn't work. This was the best example I could think of.

Thanks.

---

### Post by Tomatz on 2008-07-12
Acetone iso ;)


[http://www.acetoneiso.netsons.org/viewpage.php?page_id=2](http://www.acetoneiso.netsons.org/viewpage.php?page_id=2)

---

### Post by Tomatz on 2008-07-12
Ahhhh you want to EDIT the iso....


This is what you are looking for:

[http://www.littlesvr.ca/isomaster/](http://www.littlesvr.ca/isomaster/)


It's quite good ;)

If you need help compiling just post back

---

### Post by jerome1232 on 2008-07-12
This seems to be promising, I'm taking a look at it right now

[http://cdemu.sourceforge.net/project.php#download](http://cdemu.sourceforge.net/project.php#download)

---

### Post by jerome1232 on 2008-07-12
Just got that program installed, works very nice. I can right click an iso and it auto mounts it as if it were a real block device.

---

### Post by DeathOnJuice on 2008-07-13
Well, I found that FFTPatcher can read .bin/.cue files, and DVDRip can read from a mount directory. So, I guess I don't really need this anymore.

For anyone else reading the thread, I would look into CDEmu and possible Acetone (didn't actually check what that did yet). If for some reason you need this, those may be of use.

Thanks for the help.

---

