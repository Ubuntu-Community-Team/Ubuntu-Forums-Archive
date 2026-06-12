---
title: "Compiz cannot disable shadows"
date: 2008-10-15
forum: General Help
---

### Post by spybart on 2008-10-15
Hello, I am running Compiz fusion as my window manager and I am unable to disable shadows. If I go to the Settings manager (via the Compiz Fusion Icon), and go to the Window Decoration properties, no matter what I put in the "Shadow Windows" box or even if I leave it empty, the shadows won't go away.

If I switch over to the Metacity Window manager, the shadows are gone, but they won't go away on Compiz. Also, if I turn off Window Decorations all together, the shadows do go away but so does the top of windows.

I know I can just move the shadow radius and opacity to 0.1, but I'm trying to disable the shadows all together in hopes of getting a little performance boost (I have a laptop with Intel Extreme Graphics 2).

I looked all over the internet with no solution to be found. Anyone have any ideas?

---

### Post by Ub1476 on 2008-10-15
Well, I'm on Ubuntu right now, or have a clear picture of it in my head, but I believe that there are two input boxes at the bottom, which has "any" written in it. Personally I disable shadows for dropdownmenus, and then I write "any !dropdownmenus".

So if you write "!any", it should be disabled, I think.

---

### Post by spybart on 2008-10-15
> **Ub1476 said:**
> So if you write "!any", it should be disabled, I think.

It should, but its not!

However, I discovered something new just now. If I leave the shadow radius and opacity at their default values, my shadows are gone! Even if I have shadows as "any" or "!any" they are gone now! (which is what I want). But if I change the default values of the radius and opacity to anything else, the shadows come back, regardless of what is written in the shadow box :-k

I have a slight suspicion that the problem isn't completely fixed, and I'm afraid those shadows are going to creep up on me real soon!

---

### Post by spybart on 2008-10-15
The shadows are back. I think they were gone temporarily when I uninstalled the compiz-gnome package. With this package gone however, after my next restart I was unable to turn on any effects. Once I reinstalled it, I could enable effects but the shadows were back ! grr.

Someone help meh!

---

### Post by loomsen on 2008-10-16
Well, you gotta make sure you're using your relations right. So, it actually does matter what you put in.

Otherwise you might specify, for example, every window called "Contact List" and belonging to window class nautilus to drop shadow/not drop shadows -- tho what you intended was disabling any nautilus and any contact lists. 

First case would be: (any) &!(Class=nautilus & Title=conky)
While it should actually read: (any) & !(Class=nautilus) & !(Title=conky)

So make sure you're using your and/or relations right, and also your brackets don't mess things up. There's also a howto on the compiz-fusion homepage somewhere.

And, if the problem still persists, you might consider posting your config here, tho guessing is kinda fun too ;)

You won't get help until you tell something about your hardware/software you're using.

Anything you'll get are just hypocritic mercies, nothing more nothing less.

---

### Post by nasar2k2000 on 2008-12-10
> **spybart said:**
> Hello, I am running Compiz fusion as my window manager and I am unable to disable shadows. If I go to the Settings manager (via the Compiz Fusion Icon), and go to the Window Decoration properties, no matter what I put in the "Shadow Windows" box or even if I leave it empty, the shadows won't go away.

If I switch over to the Metacity Window manager, the shadows are gone, but they won't go away on Compiz. Also, if I turn off Window Decorations all together, the shadows do go away but so does the top of windows.

I know I can just move the shadow radius and opacity to 0.1, but I'm trying to disable the shadows all together in hopes of getting a little performance boost (I have a laptop with Intel Extreme Graphics 2).

I looked all over the internet with no solution to be found. Anyone have any ideas?

i also wanted to do the same thing. well not exactly the same as i only wanted the shadows off conky. i successfully did that and i would suggest you dont manually put in a parameter in the Windows Decoration settings. Use the 'grab' button to grab the wondow type | name | title that you dont want shadows for.
if you want them off complately then !any should work.

---

### Post by anthony.hook on 2008-12-15
> **nasar2k2000 said:**
> i also wanted to do the same thing. well not exactly the same as i only wanted the shadows off conky. i successfully did that and i would suggest you dont manually put in a parameter in the Windows Decoration settings. Use the 'grab' button to grab the wondow type | name | title that you dont want shadows for.
if you want them off complately then !any should work.


Yeah, I only wanted it to /not/ shadow for conky, and I was able to with this line in "Shadow Windows"


> (any) & !(class=Conky)

---

