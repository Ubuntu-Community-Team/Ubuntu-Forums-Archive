---
title: "Grey Screens!  Help!"
date: 2008-08-25
forum: General Help
---

### Post by Gobbie on 2008-08-25
Hi all,  

I've been running Ubuntu for about 6-ish months and I've noticed the frozen grey screen appearing more and more over the last few months.  Originally, it would happen when I'd been on a site like Youtube for a good while and it would get bogged down....from all the vids I looked at, I guess?  It's got to the point where it could happen much quicker now when just e-mailing.  The whole system craps out to a grey screen sometimes never to return.

It seems clear that my install is screwed up somehow and something is dragging it down progressively.  I've got no idea how to sort it.  Predictably, I'm an ex-windows guy who still really doesn't know his way round the technical side of Ubuntu.  I had always install the updates it gave me although for the last month or so I haven't because I don't know if that's been part of the problem.

I really need to get it fixed as my wife is using it more for her playgroup committee stuff.....obviously it's all my fault when we get the grey screen!   

The computer is a reasonable spec.  Can't remember it now but it's not too old and ran fine before.

Can someone help me here?  Do I need to reinstall?  Is there rubbish on there slowing it all down?  Should I move to a newer version?  And, I don't really know how to do any of these things!

---

### Post by Gobbie on 2008-08-25
Bump!  I'm getting swallowed up here and could really do with someone's help.

---

### Post by prshah on 2008-08-25
> **Gobbie said:**
> Bump!  I'm getting swallowed up here and could really do with someone's help.

Look through your system log (System-Administration-System Log)-"messages", and see if you can find any clue in that. Post any suspicious looking lines here for an explanation/solution.

---

### Post by mssever on 2008-08-25
Are you running Compiz? That's what it sounds like to me. Go to System > Preferences > Appearance > Visual effects and choose None. If the problem goes away, then it's got something to do with Compiz. (By disabling Compiz, you'll be reverting to Metacity, and might lose some features that you like. Also, Firefox crashes for me when switching between Compiz and Metacity, so be warned.)

---

### Post by Gobbie on 2008-08-25
Thanks guys.  I'll have a look.

---

### Post by Gobbie on 2008-08-26
Hi again,  
I've switched off visual effects (I miss my wobbly windows!) and it seemed fine although I didn't get to test it fully.  We'll see how it goes.  

On the updates side, should I be installing whatever Ubuntu throws at me, including the new version?

---

### Post by mssever on 2008-08-26
> **Gobbie said:**
> Hi again,  
I've switched off visual effects (I miss my wobbly windows!) and it seemed fine although I didn't get to test it fully.  We'll see how it goes.  

On the updates side, should I be installing whatever Ubuntu throws at me, including the new version?
Go ahead and install the updates. I'm not sure what you mean by "new version," though. Do you mean that you're currently running Gutsy, and update-manager is offering to upgrade you to Hardy?

When a program stops responding for some reason, Compiz turns their windows gray. This is probably what you were referring to, since it stopped happening when you turned off visual effects. You can go ahead and re-enable them if you want, because Compiz probably isn't causing the problem, but only making the fact that it's happening more obvious. I presuming that without Compiz running, windows sometimes stop responding for a while (if this isn't the case, then Compiz is probably to blame).

What I can't tell you, though, is what's causing these problems in the first place. Figuring that out would involve using gnome-system-monitor, htop, and/or some other similar tool to see which processes are consuming your resources. It might also require guesswork and luck. :(

---

