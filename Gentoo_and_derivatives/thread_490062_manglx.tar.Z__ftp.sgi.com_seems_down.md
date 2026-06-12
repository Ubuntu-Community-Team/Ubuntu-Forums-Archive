---
title: "manglx.tar.Z  ftp.sgi.com seems down"
date: 2007-07-02
forum: Gentoo and derivatives
---

### Post by benjo316 on 2007-07-02
The server seems to be down at ftp.sgi.com and so I can't get the man pages.
Does anyone know where I can get them or have the file I need so that I can just put it in manually?
The file I need, specifically, is 'manglx.tar.z'.

Thanks. ^.^

(Just now trying out Gentoo. It seems like a great distro, as long as you are relatively patient. I've installed
it in a VirtualBox virtual machine[had to try a couple of times because I had made the drive too small. x.x]
and it seems pretty nice. Can't wait until I get everything up. ^.^)

Edit: Also, if there is a way to bypass the install of that package(app-doc/opengl-manpages-20001215) temporarily,
until the server is back up or I can get the file some other way, that would be a big help. :)

---

### Post by benjo316 on 2007-07-02
Well, since nobody seems capable of helping me, or they just don't feel like it. I guess I'll just help myself and
whom-ever might have the same problem as I did(At least a temporary fix).

Since I don't have the file, and the server still appears to be down, I just removed 'doc' from my 'USE=' tags.
It's not the fix that I wanted to use, since now I'll only get some documentation, but it works for now. I knew
that I could do this before posting here, but I wanted to ask the community if they had any ways other than
this to work around this problem. Thank you, those of you who read this, I hope it helped in some way(But it
probably didn't, because if you're using Gentoo, you probably already knew how to do that).

This is probably not the case, but I'm really aggravated that 16 people read this and not one of them knew of
a way to fix the problem or they just didn't feel like posting the solution.

I'm still waiting for who-ever might have another solution for this, I'll keep checking back until it's solved.
If anyone has even a clue as to what to do, that is enough to at least help anyone who is new to Gentoo.
If you aren't willing to help new Linux users, then you aren't willing to help Linux grow.

Thanks for reading and have a nice day.

---

### Post by jkeyes0 on 2007-07-05
I mean no offense by this, so please don't take it as such.... but if you're having a problem installing Gentoo, wouldn't it make sense to check on a Gentoo forum, rather than claiming that we "aren't willing to help new linux users"?

[http://forums.gentoo.org/](http://forums.gentoo.org/)

---

### Post by coffeecat on 2007-07-06
> **jkeyes0 said:**
> ....if you're having a problem installing Gentoo, wouldn't it make sense to check on a Gentoo forum....

A good point.

**benjo316**, you might want to read the first post of [this thread]("http://ubuntuforums.org/showthread.php?t=82471"), about zero-reply threads.

---

### Post by benjo316 on 2007-07-08
I do understand that this is not an official Gentoo support forum, and because of that I didn't really expect the most help(I figured I'd give it a try anyway though, since this isn't necessarily something that I have to rely on Gentoo in order to fix).

I apologize to you for my previous statement, it was not meant to cause harm. I was just making a statement(Sometimes my statements get a little out of hand. x.x).

As far as the Gentoo forums are concerned, they don't seem set up well to me and I couldn't quite find a place I felt comfortable posting my question. I thought about putting it into the 'Other Things Gentoo' forum, but wasn't quite sure it was really directly related to Gentoo(Since it has more to do with downloading a required file[not from their repositories either] not the actual program which installs[builds] the programs). EDIT: The required file, btw, is downloaded automatically by the package installer. The reason I don't believe it is directly related to Gentoo is because it is from an external repository, and therefore not maintained by Gentoo.

Thank you for your responses, both of you. I'll still check back here for other replies, but I'll again consider posting in the Gentoo forums and make a link to that post if I do get any help there. ^.^

---

### Post by coffeecat on 2007-07-08
> **benjo316 said:**
> As far as the Gentoo forums are concerned, they don't seem set up well to me and I couldn't quite find a place I felt comfortable posting my question. I thought about putting it into the 'Other Things Gentoo' forum, but wasn't quite sure it was really directly related to Gentoo

Don't hesitate to post on Gentoo forums. They're really quite friendly with many knowledgeable and helpful members. I'm a member myself (I use a different moniker there - 'coffeecat' was already taken) and have had my problems answered. Don't be put off by the l33ts and twits who infest any forum. I would have thought 'Other Things Gentoo' would have been just the place to have put it. The mods there are active and helpful and will usually move a misplaced post to the correct forum if necessary. 

> **benjo316 said:**
> The reason I don't believe it is directly related to Gentoo is because it is from an external repository, and therefore not maintained by Gentoo.

Well - app-doc/opengl-manpages-20001215 is in the portage tree so it is certainly Gentoo related. Is it from an external repository? I don't know - I would have thought it would be downloaded with emerge from a Gentoo repo. I haven't tried installing it myself but when I did 'emerge -p opengl-manpages' it didn't come up with an error and it would have installed it, I guess, if I had taken the -p (pretend) flag off. Have you tried a simple emerge?

---

### Post by benjo316 on 2007-07-08
How simple do you mean? I have tried emerging other programs and it does work when I do. I'll also post in the Gentoo forums, as you suggested, and see what help I get there.

Here's a snapshot of what it does: [image]("http://i47.photobucket.com/albums/f179/benjo316/Gentoo_emerge.png")
It just does that about 5 times then quits.

here's the end of that and beginning of me emerging nano(Which I figured out was already emerged, so it was pointless): [Image 2]("http://i47.photobucket.com/albums/f179/benjo316/Emerge_Nano.png")

And another of me emerging 'games':[Image 3]("http://i47.photobucket.com/albums/f179/benjo316/emerge_games.png")

Sorry about the first image, I forgot to crop it. x.x

Gentoo post here: [link]("http://forums.gentoo.org/viewtopic-p-4135237.html")

---

### Post by benjo316 on 2007-07-08
I've found out what it is. >.<

Seems that an IP blocker that I had installed is blocking the site. I had almost forgotten about it. I think I'm going to uninstall it. It doesn't really help much and I'll just end up with another problem like this where I forgot about it and didn't know what the problem was.

Thanks for the response, and sorry for the trouble. ^.^

---

### Post by coffeecat on 2007-07-09
No problem. Glad you've got it sorted.

---

