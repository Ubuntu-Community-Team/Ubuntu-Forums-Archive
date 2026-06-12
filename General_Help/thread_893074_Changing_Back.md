---
title: "Changing Back"
date: 2008-08-17
forum: General Help
---

### Post by wow_it_esploded on 2008-08-17
Hey there! I am new to the forums but I have been using ubuntu ever since the beginning of 2005.

I recently upgraded to hardy and am having nothing but success from it!

My friend's brother's computer is running windows xp, and may I say very slowly.

Stats:
128mb ram
40 gig hd
either 64mb or 128mb video ram (not exactly sure, but I know it is low)
not sure on processor speed or type (i believe it is an intel pentium 2)

I asked if he had anything on the computer that he needed to save and he said no. Then I asked if he wanted the computer to run substantially faster. He said yes. So, basically, I am switching him to ubuntu.

Since he is an XP user and always has been I looked into a few things to make the transition as smooth as possible, aka, so I do not have to re-invent the wheel with him. I found xpGnome and tried it on my machine and loved the likeness to XP.

Unfortunately, before I ran the script I did not see the disclaimer:
> Note: There isn't any way to restore your settings easily - Gotto do it all manually

How exactly would I go about putting the whole system theme back to the normal hardy heron?

Thanks for the help!

---

### Post by pytheas22 on 2008-08-17
First of all, see if you can switch back to the original theme using the utility at System>Preferences>Appearance.  If you don't have that menu available anymore, you can still launch the utility manually by typing at a command line:
```

gnome-appearance-properties
```

If that doesn't help, you could probably fix it by moving your .gnome and .gnome2 folders in your home directory, which would dump you to the default Gnome settings and theme.  To do that, run:
```

mv ~/.gnome ~/.gnome-OLD
mv ~/.gnome2 ~/.gnome2-OLD
```

Note that this may change other Gnome settings.  It's easy enough to reverse if there's a problem, though, so let us know.

Also, I don't think Ubuntu or even Xubuntu would run too well on a 128 megabyte machine.  You may want to think about a lighter distribution for your friend, like [DSL-N]("http://www.damnsmalllinux.org/dsl-n/"), [Arch Linux]("http://www.archlinux.org/") or [Puppy Linux]("http://www.puppylinux.org/").  They're not as pretty or easy-to-use as Ubuntu, but they'd be a lot faster on an older machine.

---

### Post by wow_it_esploded on 2008-08-19
Well his brother, the user of the old computer, is a complete idiot and needs to be spoon fed. That is why I was thinking about ubuntu. I have run the live cd on that computer with mild success so installation should let it run a little better.

Besides, his current computer takes 26 minutes to completely boot up and then open firefox so any less than that should be an improvement.

Should they be pasted and entered on different lines? I think that is the standard way of doing it so when I pasted them I got this:
```
john@john-desktop:~$ mv ~/.gnome ~/.gnome-OLD
mv: cannot stat `/home/john/.gnome': No such file or directory
john@john-desktop:~$ mv ~/.gnome2 ~/.gnome2-OLD
john@john-desktop:~$ 

```

Nothing changed, but I think that I might just live with the XP theme as I already got used to it.

---

### Post by pytheas22 on 2008-08-19
You seem to have copied and pasted the commands correctly.  I don't know why it doesn't know where the .gnome folder is, but maybe it never existed for you.  I'm not sure what the XP theme changed; it may have altered more than a normal theme change.  You could probably create a new user account, though, and have the default settings on that.

---

### Post by billgoldberg on 2008-08-19
Install fluxbox and idesk an put some icons on his desktop (link to file manager, browser, ...)

It will fly on his computer.

---

