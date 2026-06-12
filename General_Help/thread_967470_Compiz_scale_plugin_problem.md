---
title: "Compiz scale plugin problem"
date: 2008-11-02
forum: General Help
---

### Post by Z_o-s-o on 2008-11-02
I've got an interesting and annoying issue with the scale plugin in compiz.

Back in previous versions, assigning a keyboard button (I use the home key) to expose all open windows, one click on the button would expo the windows, and you'd click the window you wanted to return to a regular view.

In 8.10, if I assign expo all windows to the Home key, I have to hold it down to keep the windows expose'd or it'll go back to normal by itself. The only way to get what I want is to enable a screen corner to expose the windows, and if I do that, it behaves correctly.

Is this a bug or am I missing a setting somewhere?

---

### Post by loomsen on 2008-11-02
Seems to be a bug indeed. Same behavior here.

---

### Post by rafaelcapanema on 2008-11-02
Same here. Scale is really useful, I use it all the time. Hope it gets fixed soon.

---

### Post by maxhax on 2008-11-02
I noticed something like this as well.  I've got amd64 8.10 with the Nvidia drivers and scale will actually crash.  I have scale set to initiate all windows on all desktops and if I use the left or right arrows to select a window it may crash.  I've noticed it more when I hold down the left or right arrow keys to quickly go from the left or right side of the screen to the other side. Days before when the box was running 8.04.1 it did not do this.  

I've also noticed that if you go into expo mode and hit <ctl><alt> Left or right it will cause compiz to crash...I found that by accident, but it shouldn't crash.  

Your mileage may vary, so what happens when any of you do these things?

---

### Post by Depressed Man on 2008-11-02
I don't have the Expo problem (with the ctrl + alt+ left or right while in Expo mode). But I do have the scale key assignment problem (I have to hold it).

---

### Post by loomsen on 2008-11-03
Me neither, Expo working fine.

[[img]http://img262.imageshack.us/img262/8595/screenshot45xd4.th.png[/img]](http://img262.imageshack.us/img262/8595/screenshot45xd4.png)

But I pulled it from git, so dunno how the repo version is.

---

### Post by berman56 on 2008-11-03
I have the same problem.  Love the scale windows management, hope someone can figure this out soon.

---

### Post by Z_o-s-o on 2008-11-07
There were compiz updates this morning, which I hoped would fix this issue, but no dice.

The button to activate scale doesnt keep the windows scaled...if I let go of it the windows go back to normal.

The only way for me to scale my windows correctly right now it to use a screen corner. That works 100%.

:confused:

---

### Post by Recognition101 on 2008-11-07
Yep, upgrading to 8.10 messed this up for me as well. I did some digging and found [this thread (http://forum.compiz-fusion.org/showthread.php?p=67739)]("http://forum.compiz-fusion.org/showthread.php?p=67739").

So it seems the Compiz-Fusion people are aware of this and at least that person has patched it. I found that thread a few days ago and I hoped that today's update was including the little "toggle" and "non-toggle" modes described in the post, but I can't find them in the CCSM anywhere.

So... who do we tell to get the Ubuntu maintainers to include the post 0.7.8 patch?

---

### Post by Z_o-s-o on 2008-11-07
Im not sure who we need to get in contact with...

Maybe file a bug report?

---

### Post by jtdgrz on 2008-11-07
Same problem here.  If you're a fan of using the mouse, the mouse works just fine for this.  Just initiate the window picker with the edge you like.

Very annoying bug, though.  If you use a more complicated key command (I hate reaching across the keyboard, so I have bound it differently) such as "SUPER + LETTER" then you can let go of the letter, too, and just hold on to the WinKey/super button, as well.  That's what I'm doing for a temporary fix.

---

### Post by Recognition101 on 2008-11-07
I think it already has been reported as a bug, I dug around and found [this (url)]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/281911"). I commented on it with the information I have here, but the bug is kind of stale and has no "importance", so I'm not sure it'll catch the eye of a developer any time soon. 

It's a shame, too, because it seems like it'd be an easy fix (just integrate what that person made) that nearly makes a whole compiz-fusion plugin worthless.

I think all we can do is report that it "affects me too" on the bug list, which I did.

---

### Post by rafaelcapanema on 2008-11-22
Nothing yet? It's a shame. That plug-in is really useful.

---

### Post by fatalGlory on 2008-11-24
I have this problem too, just thought I'd add my name to the list.  Is there an official bug report somewhere already?  Or should I be the one to submit it?

---

### Post by loomsen on 2008-11-24
> Or should I be the one to submit it?

WHY? To make them guys developing software for free even more (absolutely unnecessary) work? You've been pointed to the patch, you've been told that they ARE aware of it, and that the only problem there was a missing option to chose between toggle and hold. 

So, what (or, more likely WHO) exactly is the bug here? 
You unable to apply a patch?

---

### Post by fatalGlory on 2008-11-24
It seemed to me that the patch had been applied upstream by the compiz-fusion devs, but it would be beneficial for whoever is maintaining ubuntu's compiz package to integrate that patch so that the fix is actually in the Ubuntu repositories.  The report would need to go to the package maintainer - not to the actual development team.

I can apply the patch just fine, but plenty of the people I recommend ubuntu to (and who I show off the scale feature to) would not have the necessary expertise.

---

### Post by loomsen on 2008-11-24
Well, you could either do a HOWTO then, or just tell everyone how to do it, don't you think? Would probably have the (effect of filing a bug)³

---

### Post by fatalGlory on 2008-11-25
No, that wouldn't have the same effect.  Compiz-fusion and ubuntu in general are big on usability.  Me writing a HOWTO for applying a specific patch from upstream for ubuntu users does not help ubuntu become a more user-friendly and accessible distro.  The distribution package of compiz-fusion getting the patch in it does.

May I politely ask, why is this a big deal to you?  I'm a developer, I like feedback, I see no problem with telling the package maintainer about this one.  I don't quite understand, why do you feel we should keep quiet about it and just apply the upstream patch individually?

---

### Post by lamps06 on 2008-11-25
I could definitely use a "how to" on fixing this bug.  I followed this [link]("http://gitweb.compiz-fusion.org/?p=compiz;a=commit;h=d2bd7d5f1adb93481fcb8917b5e480e45bce4d48") and I see three files but I do not know what to do with them.  I tried searching for them on my ubuntu drive but I cannot find them to replace.  Could anyone give me a hand, please?  Thanks!

---

### Post by damis648 on 2008-11-25
I am aware of this bug also, but have just put up with it. I figured that in a couple weeks the devs would fix it... I guess not. Oh well... right now I am just using a hotcorner for scale.

---

### Post by Recognition101 on 2008-11-25
lamps06, there's a howto here (read Vermind's topmost post): 

[http://backports.ubuntuforums.com/showthread.php?p=6121196]("http://backports.ubuntuforums.com/showthread.php?p=6121196")



However, that's really just a macro hack. It'll work, but it isn't optimal. As I pointed out before, there is a fix (it's those three files you had), but the ubuntu people have to include the build of compiz compiled with those three files. The reason you couldn't find those files (at least, this is my guess) is because they're part of compiz. To fix it with those files, you'd need to download the compiz source, recompile compiz with those files, and reinstall it. Not something I want to do. Nor do I want to do the macro hack, I agree with loomsen that this is a major usability pain and even worse, it has an easy fix (for ubuntu developers).

---

### Post by lamps06 on 2008-11-25
Ahhh, OK, that makes sense.  No, I do not feel like compiling anything either, nor do I want to use the macro work around.  Ugh.  Hopefully this issue is resolved soon...

I will keep an eye on this thread.

---

### Post by Recognition101 on 2008-12-23
They fixed it: [link]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/281911")

However, it looks like they fixed it in jaunty, and us intrepid users are left out in the cold. There's been a request to backport it to intrepid, but who knows if anyone will hear/do that.

---

