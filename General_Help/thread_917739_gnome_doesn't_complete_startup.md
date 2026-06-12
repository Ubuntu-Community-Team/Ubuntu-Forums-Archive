---
title: "gnome doesn't complete startup"
date: 2008-09-12
forum: General Help
---

### Post by orlox on 2008-09-12
Hi!

I have installed intrepid alpha 5, and updating the system this week made gnome stop working. When I try to login The only thing I get is the backgorund image, and the mouse pointer wich I can move. And it styas at that. I can close the session by pressing ctrl-alt-backspace. Right now im working with kde4 (wich I deeply, deeply despise...)...

What I have done already is:
[LIST]
[*]Eliminating .gconf .confd .gnome2 and .gnome2_private
[*]Reinstalling every single gnome package
[*]Create a new clean user account and trying to login with it
[/LIST]

All of these didnt help at all, and I still get stuck at the bakground image...

Any help would be much appreciated...

---

### Post by orlox on 2008-09-14
Anybody???

bump (hate doing this...)

---

### Post by Neo_The_User on 2008-09-14
It is Ubuntu 8.10 Alpha 5. Not supposed to be stable.

---

### Post by orlox on 2008-09-14
I know it isn't stable, but I just want to see if someone has a solution.

---

### Post by fiddler616 on 2008-09-14
Insert Ubuntu Hardy...install...just kidding
But yeah, don't expect things to a)Work or b)Be predictable in an alpha.
I'd also recommend asking to have this moved to the Intrepid discussion, not General Help.

---

### Post by orlox on 2008-09-14
Well, I guess you're right this would fit better at Intrepid Discussion.

In any case...I installed intrepid because it had a better support for wireless. I got a broadcom working only by installing the b43-fwcutter package, wich never worked in hardy (I had to recompile ndiswrapper to make it work...And I had to recompile it every time I did a kernel update...)

---

### Post by fiddler616 on 2008-09-14
It couldn't wait 'til Beta? You could've just not done a kernel update until...October, nothing terrible would've happened.
I guess it's water over the dam though.

---

### Post by orlox on 2008-09-14
> It couldn't wait 'til Beta? 

Just why do you think alpha releases are made public???

Many bugs wich are common, are very difficult to detect and isolate for developers if they don't have a wide user base.
Thus, each ubuntu release is strongly dependent on user feedback. Where not for people who test alpha releases and report bugs each new ubuntu would be plagued with them.

Considering it takes like 2 hours to make a clean intrepid install with everything i need (including installation of the GTK styles and icons I use, latex, iraf, apache, mysql, subversion, quanta, etc...), and I have a partition where I can test this, I don't see why I shouldn't give it a try and report the problems I have. If a can get a solution for them and can continue using the new distro, even better!

If no one but developers would use alpha releases I could assure you that open source software would be way behind commercial software.

I'm not here saying "oh my god!! my system crashed, this thing sucks!!Give me a solution now!!". Neither am I expecting an alpha release to be stable and bug-free. I simply found a problem I couldn't solve and wanted to see if anyone else had a solution.

Maybe I should set this discussion on a more appropiate place. Guess I'll request help at lauchpad. Hope that there people have a wider vision about the subject, and don't simply tell me to expect other people to create great distros all by themselves.

PD: I don't have against this forums (they've helped me a lot), it's only that it surprises me that some people can act like this when someone reports a problem in an alpha release...

---

### Post by orlox on 2008-09-16
Solved this one by installing gnome-desktop-environment and nautilus. dunno why nautilus was uninstalled, but this was set as an urgent bug on launchpad:

[https://bugs.launchpad.net/bugs/219444]("https://bugs.launchpad.net/bugs/219444")

I found this bug report by issuing one myself:

[https://bugs.launchpad.net/bugs/270325]("https://bugs.launchpad.net/bugs/270325")

And there they told me that the bug was a duplicate of the one already filed...

---

