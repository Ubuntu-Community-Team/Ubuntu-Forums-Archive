---
title: "Can't back up DVD?"
date: 2006-02-19
forum: Hardware &amp; Laptops
---

### Post by SolidAndShade on 2006-02-19
I've been trying to back up my DVDs but for some reason the DVDs I create aren't playable. The first time I did it, I tried using K3b to copy the DVD. K3b said that it couldn't copy encrypted DVDs. So I ripped the .iso image from the DVD, then tried to burn it on a DVD+R. The DVD+R was dual layer and all the data was copied over all right, and I checked the file system to make sure nothing was missing. However, this DVD copy would not play in totem, ogle, mplayer or anything else I tried. It said "The source seems to be encrypted, and cannot be read. Are you trying to play an encrypted DVD without libdvdcss?" I do have libdvdcss and the original DVD played just fine.

So I tried using dvdbackup to rip the video_ts directory from the original DVD. That went without a hitch, and I was able to play the copied directory with ogle as if it were a real DVD. No more encryption problems, or so it seemed. I used mkisofs to turn the ripped directory into an .iso image and burned it to a DVD, and the DVD wouldn't play and totem gave me the same message as last time.

Does anyone know what's going on here? Is there some essential step I'm overlooking to create a working DVD copy? Thanks.

---

### Post by SVFUSiON on 2006-02-19
have you tired xdvdshrink? :-k

---

### Post by SVFUSiON on 2006-02-19
actually here is more info about it,

XDVDShrink is a project in BASH and Perl-Gtk2 that allows you to create fair-use archival copies of DVD content on single-layer writable DVDs.

# Command-line and graphical interface
# Scriptable
# Copy single movies
# Copy multiple episodes
# Selectable audio stream (AC3 only)
# Option for one subtitle stream per DVD title

[http://dvdshrink.sourceforge.net/]("http://dvdshrink.sourceforge.net/")

---

### Post by SolidAndShade on 2006-02-19
I'm using double-layer DVDs, so the size of the files isn't a problem... the 6 gigabyte .isos have burned just fine.

---

