---
title: "Perhaps DVD/CD unit gone bad ?  or not ?"
date: 2015-03-30
forum: Hardware
---

### Post by michael-piziak on 2015-03-30
Ubuntu 12.04 LTS

If I put in a non copyrighted DVD to play it and the dvd drive spins up to what sounds like it's maximum speed.  After about a minute a loud crashing sound ends the spinning and I can remove the disk.  If I try to eject the disk while it's spinning, it makes the crashing sound also.

However, if I put an audio cd in and play it, no problem.  If I put a blank CD in and burn data to it, also no problem.

Time for a new drive or could it be software ?  I rarely use the drive and may decide to do nothing.

---

### Post by Vladlenin5000 on 2015-03-30
No, time to read this: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by michael-piziak on 2015-03-31
ok, I think that particular dvd was the problem as I've tried others and it doesn't do that.

however, I am interested in getting commercial dvd's to play.

I read your link.  I have previously installed ubuntu-restricted-extras and VLC.

Therefore, should I skip the first terminal line and type the second one in:
[COLOR=#000000]```
[/COLOR][COLOR=#333333][FONT=UbuntuMono]sudo /usr/share/doc/libdvdread4/install-css.sh[/FONT][/COLOR][COLOR=#000000]
```[/COLOR][COLOR=#333333][FONT=UbuntuMono]

[/FONT][/COLOR]?

---

### Post by Yellow Pasque on 2015-03-31
> Therefore, should I skip the first terminal line and type the second one in
Yes.

---

### Post by michael-piziak on 2015-03-31
Thanks folks, works great.
Marking this thread as solved.

---

