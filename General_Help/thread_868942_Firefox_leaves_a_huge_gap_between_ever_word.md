---
title: "Firefox leaves a huge gap between ever word"
date: 2008-07-24
forum: General Help
---

### Post by Fufkin on 2008-07-24
(edit: goddammit my first ever thread and there's a typo in the title.  Should be 'every word' obviously)

This is the strangest problem I have ever had.

Firefox has started putting a big space between each word on every website (see attachment).  

The same thing happens with input boxes: as I type this, every time I press space the cursor jumps forward about 4 'regular' spaces.

The only thing I've changed recently is uninstalling Avant Window Navigator and installing tint2 (the problem remains when tint isn't running).

What on earth is going on? :confused:

---

### Post by Het Irv on 2008-07-24
Well, your post looks normal to me, so the problem is only on your end.
Does this only happen in Firefox?  Check your zoom under View.

---

### Post by PCessna on 2008-07-24
May also be your resolution, besides zoom setting, If not and FireFox seems to be not lucky for oyu, go to add/ remove programs from' ubuntu menu' at top right, add / remove programs, and use Konqueror. If you don't like that, Opera is also available.

Hope that helps
-PCessna

---

### Post by Fufkin on 2008-07-24
Thanks for the replies.

> **Het Irv said:**
> Well, your post looks normal to me, so the problem is only on your end.
Does this only happen in Firefox?  Check your zoom under View.

Yep, only firefox as far as I know (gedit, nautilus and open office are all fine).  

Zoom is normal (and zooming out doesn't help).



> **PCessna said:**
> May also be your resolution, besides zoom setting, If not and FireFox seems to be not lucky for oyu, go to add/ remove programs from' ubuntu menu' at top right, add / remove programs, and use Konqueror. If you don't like that, Opera is also available.

Hope that helps
-PCessna

You mean my monitor resolution?  Gave it a try but no luck.

I really don't want to sacrifice my finely-honed firefox configuration unless I absolutely have to :( .  There's no way I'm going to remember all those saved passwords!

---

### Post by Het Irv on 2008-07-24
You can save your config file for firefox,  just copy the .mozilla file in your /home folder.  That will save all of your bookmarks, add-ons, and passwords.

---

### Post by coffeecat on 2008-07-24
> **Het Irv said:**
> You can save your config file for firefox,  just copy the .mozilla file in your /home folder.  That will save all of your bookmarks, add-ons, and passwords.

It might be the config that is the problem. **Fufkin**, try renaming the folder ~/.mozilla and then start firefox. You'll go back to a default firefox (it will create a new ~/.mozilla) but at least you can see whether the problem is with the configuration somewhere in ~./mozilla or somewhere else.

If that fixes it, you won't have to re-install firefox but you will have to set up firefox the way you like it again. At least you can export your bookmarks as a .html file and then reimport them again.

---

### Post by jimv on 2008-07-24
If you look in your Firefox profile folder (~/.mozilla/firefox/yourprofile) then you'll see that your bookmarks and passwords exist in files that you can just copy into your new profile.  That way you don't have to enter them in again.

---

### Post by Fufkin on 2008-07-24
> **coffeecat said:**
> It might be the config that is the problem. **Fufkin**, try renaming the folder ~/.mozilla and then start firefox. You'll go back to a default firefox (it will create a new ~/.mozilla) but at least you can see whether the problem is with the configuration somewhere in ~./mozilla or somewhere else.

If that fixes it, you won't have to re-install firefox but you will have to set up firefox the way you like it again. At least you can export your bookmarks as a .html file and then reimport them again.

Thanks for the suggestion.  

First I renamed ~/.mozilla and got a default firefox - the problem remained.

Then I completely removed firefox with the package manager and installed it again - STILL the same problem.

If completely reinstalling didn't fix the problem then it must be something pretty serious maybe?  :(

Edit: For what it's worth I just installed Opera and that works fine, so definitely a Firefox issue.

---

### Post by coffeecat on 2008-07-24
> **Fufkin said:**
> First I renamed ~/.mozilla and got a default firefox - the problem remained.

Then I completely removed firefox with the package manager and installed it again - STILL the same problem.

If completely reinstalling didn't fix the problem then it must be something pretty serious maybe?  :(

I really don't know, but this **may** be what happened. The problem is a misconfiguration somewhere in /usr or /etc. When you renamed ~/.mozilla and restarted firefox, it created a new ~/.mozilla, but from the default configuration (now corrupted) in /usr or /etc or wherever in the non-home system it is kept. That's why the problem remained at that point.

When you completely removed firefox, did you check to make sure that the newer ~/.mozilla had been removed? If it hadn't been, the newly installed firefox would have found it, not made a new one and picked up whatever the problem is again.

This is only a theory, but the following might be worth trying:

1 Mark Firefox for complete removal in Synaptic and uninstall.

2 Check to see if ~/.mozilla is still there and remove it if it is.

3 Reinstall firefox.

---

### Post by Fufkin on 2008-07-24
> **coffeecat said:**
> I really don't know, but this **may** be what happened. The problem is a misconfiguration somewhere in /usr or /etc. When you renamed ~/.mozilla and restarted firefox, it created a new ~/.mozilla, but from the default configuration (now corrupted) in /usr or /etc or wherever in the non-home system it is kept. That's why the problem remained at that point.

When you completely removed firefox, did you check to make sure that the newer ~/.mozilla had been removed? If it hadn't been, the newly installed firefox would have found it, not made a new one and picked up whatever the problem is again.

This is only a theory, but the following might be worth trying:

1 Mark Firefox for complete removal in Synaptic and uninstall.

2 Check to see if ~/.mozilla is still there and remove it if it is.

3 Reinstall firefox.

Thanks again for the suggestion coffeecat.

I did what you said, but even after making sure ~/.mozilla was created by the fresh installation the problem still remains. 

(You were right in one sense though: after removing firefox ~/.mozilla remains, so my previous reinstall was still using the old configuration)

---

### Post by Fufkin on 2008-07-25
I guess I'll bump this one more time before giving up and switching to Opera.

This is really annoying - I can't believe an application I love has been rendered useless by such a strange problem and there is nothing I can do to fix it :mad:

---

### Post by foo.greece on 2008-09-26
Hello,

i have the same problem with fufkin and i would like to know if there is any solution given to the problem.I've posted about this yesterday in:
[http://ubuntuforums.org/showthread.php?t=929593]("http://ubuntuforums.org/showthread.php?t=929593")

Thank you all in advance.

---

