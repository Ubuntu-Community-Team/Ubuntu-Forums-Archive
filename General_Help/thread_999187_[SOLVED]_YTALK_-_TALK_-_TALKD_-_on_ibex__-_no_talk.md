---
title: "[SOLVED] YTALK - TALK - TALKD - on ibex  - no talk daemon - tried everything"
date: 2008-12-01
forum: General Help
---

### Post by euphemus on 2008-12-01
[SIZE="3"][/SIZE]I was running an old machine with Hardy: I've upgraded to 64 bit Ibex (and a really nice machine).

When on Hardy - ytalk/talk would not inform me about talk requests - did what I could - added "mesg y" to .bashrc - couldn't fix it, so worked around it by getting ssh users to drop "eyes" onto tty7 - not exactly great but it let me know they were there so I could talk them.

Now on ibex, I can't get any ytalk/talk to work. Whenever I try to "talk" it opens the interface, delay and then tells me [COLOR="Indigo"]**"No talk daemon on euphemus"**[/COLOR].

I have checked all the treads/post here and Google - nothing.

I really like using ytalk (that is the one I need help with). I have the latest ytalk and talkd - I have tried older versions and even got the updates from different mirrors (not my local) - nothing.

Can someone help? It all seems to come down to talkd - which seems to give other users trouble too.

:(

---

### Post by euphemus on 2008-12-13
CRANKY N00b WARNING!:-({|=

Well thanks for the help Ubuntu "community" (everyone is a community these days).

I am a TOTAL n00b - I love Ubuntu and am learning fast (the hard way) - I had debian-0.0.0?? for years - it just ran - I didn't know how it ran and didn't ask - not even its release version. My friend Patrick lived with me, and he had it set up when I got it and he kept it running. 

Two things first: 
- n00bs have no idea what you are saying Linux-geniuses - so make it really, really simple and explain every move (don't expect me to know what "you need to fix your init.d" means!)
- for other n00bs - use Google to search this site - the in-built search is not so great.

Now for the ytalk/talkd thing: After buggering about with changing nobody.tty and other stuff in /etc/inetd.conf, and knocking about in /etc/services, installing and reistalling talk, ytalk, dtalk, inetutils-inetd, restarting them and reloading them, and going from help page to help page, I thought I'd give up.

Then my friend old friend Patrick (a Linux superhero) ssh'd in and solved it in half an hour: 
HERE! [http://ubuntuforums.org/showthread.php?t=936465](http://ubuntuforums.org/showthread.php?t=936465).

For the n00bs: It would seem that talkd (the daemon that runs talk) is running in IPV4 "4" (just accept that as fact (I don't really understand what that means)) and /etc/inetd.conf (the thing that gets talk daemon going) is using IPV6 "6" - one is "4", the other "6" - not the same language. So you need to force /etc/inetd.conf to run talkd in IPV4 by changing the /etc/inetd.conf file (the post above has the lines to add - changing "upd" to "upd4" basically).

Why are they not the same?: IPV6 is newer and talk hasn't caught up (because no-one cares about talk).

Why hasn't someone in the Ubuntu community updated the ytalk install in the registry to fix this? (Same).

I am one cranky little n00b:mad::!:

---

### Post by kkady32 on 2009-03-27
i have the same problem,talk daemon is not on ant talk or ytalk not work

i find this and now not have daemon error,but i dont have somebody to probe when work now or not
[https://bugs.launchpad.net/ubuntu/+source/inetutils/+bug/232051](https://bugs.launchpad.net/ubuntu/+source/inetutils/+bug/232051)

---

### Post by euphemus on 2009-03-27
Hey,

Are you running a 64bit system? I think that is important for this problem.

What exactly is the problem? Do you get the error "No talk daemon"? Or is it something else?

==================
Did you try changing /etc/inetd.conf?
Mine looks like this:

#/etc/inetd.conf
talk   dgram   udp4   wait   root   /usr/sbin/in.talkd   in.talkd
ntalk  dgram   udp4   wait   root   /usr/sbin/in.ntalkd  in.ntalkd
#end

(PUT TABS WHERE NEEDED! - and - Any OTHER reference to talk/talkd/ytalk/ntalk... etc should be pounded ("#") out of action.)

===================
Also: check your /ect/services. Mine looks like this (under heading "# UNIX specific services"):

talk  517/udp
ntalk 518/udp

(PUT TABS WHERE NEEDED - and - Any reference to other talk/ytalk/dtalk/ntalk... etc services should be "#" out of action.)

================
Doing both the above did allow me (at first) to talk others except for one problem: when someone "talk" requested me, I heard a beep but got no message (couldn't seem to fix my msg/mail daemon (I TRIED AND TRIED)) - it would seem that the Ubuntu x desktop is loggged into tty7, and, any console/terminal I activated, as pts/0... - BUT when the talk daemon requested the message daemon to notify me, the message/mail daemon tried to send it to tty7 (which of course is the desktop - which of course wouldn't work), rather than sending it to pts/0 which was my concole. I just lived with it: I could "talk" request others without a problem - even when they were ssh'd in on another tty (simply because they WERE on another tty). I suspect another programme changed something, somewhere, sometime that messed up the mail daemon.

This problem solved itself some weeks ago when I crashed the whole system (I reloaded XP onto another partition and it stuffed the grub dir.) - corrected itself when I reloaded xp FOLLOWED BY INSTALLING Increpid.

All works great now - but you must adjust the 2 /etc files above. So - do the above and at the very least you should get talk (maybe without the messages).

Good tester - create a test user - log them into tty6 and try talking to yourself (but don't do it too often you may go mad!)

Oh 8.10 Icrepid-Ignoramus - I am so hanging out for 9.04 Jaundiced-Jackass!

e

---

### Post by kkady32 on 2009-03-27
yes i use 64 bit,i change in inet.conf and now i dont have error with talk daemon,
how make u this?:))i become an mesagge that is interesting

i make the test but appear that  " [email]test@localhost.locald[/email]omain#tty6 refusing messages "
i will try again and when find somenthing than i tell u and maybe make an test togheter :))

---

### Post by euphemus on 2009-03-27
OH yeah that - I forgot that...

When you log in as "tester" type this:

mesg

> you should get reply:

is n

> mesg: means "am I accepting messages from the system?"
> n: means "no!"

> so...

> type:

mesg y [ENTER]
mesg

> you should get reply:

is y

> mesg y: means "turn messages on"
> mesg n: means "turn messages off"
> y: means "yes!"

Sorry I forgot to mention that.

e

---

### Post by kkady32 on 2009-03-27
thanks a lot for u help,euphemus

---

### Post by go_beep_yourself on 2010-11-06
Is this still working for you in Ubuntu Maverick? It's not for me. I can't get talkd to run at all, followed everything.

I don't want to use ssh each time I run talk with my friend, so I try to connect talk username@ip. In order for my friend to respond to the request, he says I need to be running the talkd daemon as well. Is this true?

---

