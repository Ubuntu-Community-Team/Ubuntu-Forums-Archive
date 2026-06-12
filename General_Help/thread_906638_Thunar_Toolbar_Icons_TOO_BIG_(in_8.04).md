---
title: "Thunar Toolbar Icons TOO BIG (in 8.04)"
date: 2008-08-31
forum: General Help
---

### Post by ivansf92 on 2008-08-31
Does anyone using Thunar in Ubuntu 8.04 Hardy Heron have any problems with the Thunar when it's in "Toolbar Style"?

Because for me, the icons on the toolbar look like they are 48x48 pixels, and it should be smaller than that.

Many people seem to be having the same problem:
[http://ubuntuforums.org/showthread.php?t=689422](http://ubuntuforums.org/showthread.php?t=689422)
[https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/203236](https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/203236)
[http://bugzilla.xfce.org/show_bug.cgi?id=3971](http://bugzilla.xfce.org/show_bug.cgi?id=3971)

But there aren't many posts and I was wondering if anyone has a solution to such a problem.

There has to be SOMEONE who solved the problem, right? Because if no one did, then no one would be using Thunar in "Toolbar Style" in Hardy Heron.

I wanted to use the patch that was mentioned in the last 2 links above, but I would have to compile it from source and alter the code, and I don't really know how to do that.

I would really love to use Thunar in "Toolbar Style", but this is stopping me from it. Any help would be greatly appreciated.

Screenshot:
[IMG]http://img168.imageshack.us/img168/144/screenshotzf4.png[/IMG]

---

### Post by Excalibre on 2008-09-28
I'm bumping this because I'd like to know too. If someone could give an explanation of how to apply that patch, I'd be most appreciative.

---

### Post by wattz3 on 2009-10-31
would also like to know how to make the Thunar Toolbar icons smaller!

I'm using Ubuntu 9.10

---

### Post by ubername on 2009-11-26
same problem in Lucid

---

### Post by B.Hat on 2010-03-11
Same problem still in Karmic with Thunar 1.0.1

I'm a fool when it comes to that .patch file as well. I figure I need to download the thunar source code and then move the patchfile into that directory and do some trickery such as:

```
patch -p0 < filename.patch
```

I am concerned that I can only find the older Thunar 1.0.0 for download and I am not sure if it is appropriate to just uninstall thunar, then patch and install this older version, and everything will be back in place with thunar as the default file manager. 

Additionally, if thunar is installed in this manner will updates be applied as they are found by the update manager as normal?


I wonder why this hasn't been addressed sufficiently yet. . .

---

### Post by woodyg on 2012-02-15
> **B.Hat said:**
> I wonder why this hasn't been addressed sufficiently yet. . .

It's now 2012 and the problem still seem to be there. I'm running Ubuntu 11.10 and just installed Thunar and couldn't help noticing those huge icons. Is there a simple way to fix this?

---

### Post by aeiah on 2012-02-15
looks like this works unless you're using gnome3
[https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/203236/comments/19](https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/203236/comments/19)

---

### Post by overdrank on 2012-02-15
Hi and please start a new thread with your issue. Thread closed.

---

