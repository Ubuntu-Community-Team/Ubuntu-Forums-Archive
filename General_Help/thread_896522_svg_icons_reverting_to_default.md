---
title: "svg icons reverting to default"
date: 2008-08-21
forum: General Help
---

### Post by Stunts on 2008-08-21
Hi all.

I've had this issue for a while now. I've posted before on absolute beginners talk, but nobody had an answer for me. Maybe I'll have better luck here.
Here is my original post:

			 			 		   		 		 		> Hi all!
I've been having this strange issue with Gnome.
Here's how it goes.
I've tried to add a few new icon themes to my installations, but I have noticed a glitch.
In some of the iconsets some icons would not display (would revert back to gnome's default). At first I thought that they were simply missing from the set I had downloads, so I changed the icon theme and that was it.
But recently I downloaded a few new ones (Very nice, crystalline btw) that were supposed to be complete. I found it odd that some icons such as the folders in Nautilus were missing (reverted to gnome original).
Well I looked deeper into it (the ~/.icons and the respective text file with the icon references) and here's what I found. When an iconset uses scalable icons these don't display. I'm only getting the .png ones.
I'm currently using a full .png iconset, but it's sort of heavy (90Mb) and I really feel the slowdown on boot.

Anybody got any ideas on what could be wrong?
I'm using X86_64 Ubuntu.
I can post anymore info if required.
Do you think I should file a bug report on launchpad? Or is this somewhat common?

Thanks!

The problem seems to be with the .svg icons only...

The said themes can be found here, in gnome look:
[http://www.gnome-look.org/content/sh...?content=27166]("http://www.gnome-look.org/content/show.php/Glossy-Glass?content=27166")
[http://www.gnome-look.org/content/sh...?content=72273]("http://www.gnome-look.org/content/show.php/newblack?content=72273")

Can anybody help?

BTW I've also submitted a bug in launchpad, but nobody made a reply...
[https://bugs.launchpad.net/ubuntu/+bug/256603](https://bugs.launchpad.net/ubuntu/+bug/256603)

Thanks!

---

### Post by pauper on 2008-08-21
It's not a bug.

[This document](http://standards.freedesktop.org/icon-theme-spec/icon-theme-spec-latest.html) states that SVG icons support is optional and look up is done in
the following order: PNG, SVG, XPM (see algorithm in pseudocode).

You may question the validity of it. Personally, I can't tell how close GNOME
or KDE work with freedesktop.org standards.

For example, set to Human theme, run "alacarte" and select gedit's properties
from Accessories, click on icon. Mine (gutsy) points to this image:
/usr/share/icons/gnome/scalable/apps/accessories-text-editor.svg

---

### Post by Stunts on 2008-08-22
Hi and thanks for your reply!
I've read your link and read the file. Very enlightening. I mean it.
I've also been to "alacarte" and checked out the proprieties of icons that changed and icons that didn't.
Some of the icons that were reverting to defaults are .png.
Some of them change to the new theme and some don't. an example is the gnome- terminal. This one gets the new theme, but gedit doesn't. They are both define by the same line in index.theme and the both exist on the same folder.
It's really strange. It means that the problem is not only on the .svg icons, but on .png icons too.
I'm really confused now.
I've checked filesizes too, but that's just not it...
Any ideas?
BTW, did you try the themes yourself? Do they work for you?
Thanks.

---

### Post by pauper on 2008-08-22
It seems quite close:
[http://library.gnome.org/devel/icon-theme-spec](http://library.gnome.org/devel/icon-theme-spec)

Try rearranging the order of "Directories=" in your custom index.theme. Push
directories with SVG icons up front, i.e. instead of
Directories=8x8/stock/generic,12x12/stock/generic,..
make:
Directories=scalable/actions,scalable/animations,..

Make sure those directories actually exist.

Compare basenames of icons between themes: rename custom icons, if needed, to
match the names of their equivalents from some generic theme.

Might need to edit "Inherits=" order.

As a last resort you can overwrite those stubborn icons with your custom ones.

The standard says about the icon size (24x24 pixels) look up not a file size
(1kB).

The Human theme example is just to show that SVG images, in case of gedit's
icon as example, are being used. Do you get any of them when you revert to
Human theme?

I've tried several custom themes, as I matter of fact I'm currently using one
of them,--none are absolutely content, i.e. they borrow icons from other themes
(all applets, xterm). I can live with that.

---

### Post by Stunts on 2008-08-23
OK, so I've tried to mess with everything in my index.theme file.
The theme clearly has the icons since I can see them in the respective folders, just like indicated by index.theme.
Furthermore I have found that no custom theme I have is actually loading all the icons. It's just more evident in some then in others.
This means that either I'm bugged, or the themes are.
I can see icons in the themes' folders that are not showing up on my system. This seems to be somewhat random.
I am 100% out of ideas...
I'm starting to think that my only chance is to actually overwrite the original theme files. But that could bring some more trouble down the road, and tons of work just to get a new theme, as you can guess...
Any more ideas?

---

### Post by Stunts on 2008-08-23
Hi again.

I've delved into the issue a bit more, and here's what I've found:
If I rename my theme files _exactly_ as the original gnome theme, they work. Just that simple.
Do you think this could be an ubuntu bug?
This would normally not be an issue, but some icons in .svg in gnome are .png in the new theme and vice versa.
I'll add this to my launchpad bug and see if I get anyone's attention.
I'm not even sure this is a bug...
Thanks for all your help!
Before I mark this solved, just let me know your thoughts on this please.

---

### Post by pauper on 2008-08-24
Well, if basenames don't match some pattern, then these icons won't be used--
as simple as that. So, yes, renaming to match original is the only way to have
an option of being picked up--you should notify that custom theme author about
any incorrect names.

See, to be sure whether it's a bug or not, you should make your custom icon
theme 100% identical to the generic one in terms of directory tree structure.
Meaning that, if the original theme has 22x22 icons, then you should create a
set of those as well--only images should differ but not their names, icon
sizes, locations. Otherwise some icons might be borrowed elsewhere--refer to
the look up scheme.

An example:
```
Human/8x8/stock/generic     Human/24x24/status
Human/12x12/stock/generic   Human/24x24/devices
Human/16x16/status          Human/24x24/filesystems
Human/16x16/devices         Human/24x24/categories
Human/16x16/filesystems     Human/24x24/actions
Human/16x16/categories      Human/24x24/stock/generic
Human/16x16/actions         Human/24x24/emblems
Human/16x16/stock/generic   Human/24x24/apps
Human/16x16/emblems         Human/24x24/places
Human/16x16/apps            Human/48x48/status
Human/16x16/places          Human/48x48/devices
Human/22x22/status          Human/48x48/filesystems
Human/22x22/devices         Human/48x48/categories
Human/22x22/categories      Human/48x48/actions
Human/22x22/actions         Human/48x48/stock/generic
Human/22x22/apps            Human/48x48/emblems
Human/22x22/places          Human/48x48/apps
Human/32x32/status          Human/48x48/places
Human/32x32/actions         Human/48x48/mimetypes
Human/32x32/apps            Human/scalable/actions
Human/[highlight]scalable/status[/highlight]       Human/[highlight]scalable/emblems[/highlight]
Human/[highlight]scalable/devices[/highlight]      Human/[highlight]scalable/apps[/highlight]
Human/scalable/filesystems  Human/[highlight]scalable/places[/highlight]
Human/[highlight]scalable/categories[/highlight]   Human/[highlight]scalable/mimetypes[/highlight]

```

Plus anything else it inherits from Tangerine and gnome themes. Then custom
index.theme "Directories=" order must match original.

That's quite a task!

The theme I'm using has a single parent directory scalable/ with several
sub-directories ([highlight]highlighted[/highlight] in the example) that populated with 32, 48, 128,
256 pixel PNG and SVG icons--contrary to the original, which keeps only SVG
images under scalable/ tree.

Remember that some applications have their icons compiled into binaries,
others--keep in different locations: a general place to check--/usr/share/pixmaps;
Firefox--/usr/share/firefox/icons and chrome/icons/default;
Firefox' extensions-- $HOME/.mozilla/firefox/*.default/extensions/* (sometimes
in .jar files);
wine programs--$HOME/.local/share/icons; etc.

A search should reveal all that:
```
:~$ find / \( -iname "*.png" -o -iname "*.svg" -o -iname "*.xpm" \
> -o -iname "*.gif" -o -iname "*.jpg" \) -printf "%h\n" 2>/dev/null \
> | uniq >$HOME/new_file
```

> I'm currently using a full .png iconset, but it's sort of heavy (90Mb)...

Having only SVG is quite tricky, depending on its original size. You might end
up with more disk space spent.

---

### Post by Stunts on 2008-08-27
Thank you for your reply!
It was very complete.
I have in fact tried to rename all the icons, create all the folders and linked missing files to existing ones (if applicable). I've also edited the index.themes file in order to match the original ones.
My result after 3 nights of work:

It's pointless. If an icon is missing, well, it's going to remain missing until the author (as opposed to the user) does something about it.

I really do appreciate your effort. But this is just pointless. I lost 3 nights trying to make it work and I just bluntly failed.

It's either all this, or it's just me. =-)
I'm updating my bug at launchpad.
I feel however that I have not only learned a lot (like I "leveled up"), I also had some fun doing this. I used to be hardcore gamer. But when you have Linux to tinker with, who cares about games?
Thanks for your replies once again. Like you said - It was quite a task.

By the way, I'm now using the "JiniBlueSky" icon theme despite the missing ones (some are more flagrant than others).
If you want to try it, here it is - [http://jini.kldp.net/](http://jini.kldp.net/)

---

### Post by Keen101 on 2008-10-17
is your problem the same as mine?

[http://ubuntuforums.org/showthread.php?t=942735](http://ubuntuforums.org/showthread.php?t=942735)

---

### Post by Stunts on 2008-10-18
Hi!
My problem is similar to yours, but my issues were with downloaded icon sets, not the default human iconset.
As you can see from my post, I went trough a lot of work to get most icons (90%) working properly.
I don't know the solution for your restart issues, but for the missing logout icons, all you have to do is change the filenames of the human iconset to the exact same filenames and locations you will find in the gnome iconset...
I hope that was clear enough, if not, just let me know and I'll try to improve my explanation.
Anyway, good luck!

---

