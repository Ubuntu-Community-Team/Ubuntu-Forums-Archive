---
title: "CDs/DVDs unmountable due to Invalid Mount Option"
date: 2007-10-31
forum: Hardware &amp; Laptops
---

### Post by thelostgraviton on 2007-10-31
I've seen similar posts so please forgive my ignorance if I've somehow missed the solution to my problem. I've been able to get around this problem by typing the following in a terminal...

[COLOR="Red"]sudo mount -r /dev/hdc /media/cdrom0[/COLOR]

...and when I'm finished...

[COLOR="Red"]sudo eject /media/cdrom0[/COLOR]

I'm unsure if this is relevant but thinking it was a permissions problem I opened the file browser as root...

sudo nautilus

...and the device isn't even shown (it's perfectly visible in the User's File Browser).

As I'm not at the problem box at the moment I'll have to post the results from fstab a little later this evening. In the meantime I can tell you this much... the DVD-ROM is set to Cable Select and is in the Master position on the second IDE Channel, no problem there I can see...

In an otherwise WONDERFUL distro this is the only "issue" I've found, ANY advice is highly appreciated...

- Kell
[http://www.myspace.com/mr_mondo]("http://www.myspace.com/mr_mondo")

---

