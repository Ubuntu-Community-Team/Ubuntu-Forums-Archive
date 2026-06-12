---
title: "ssh problem, can't find $TERM"
date: 2008-11-09
forum: General Help
---

### Post by prinny42 on 2008-11-09
Okay, so I though I might participate in the devnull Nethack tournament for the first time this year.  I went to the site and registered and everything.  So when I go to the command line I type ```
ssh (my username)@nethack1.devnull.net : 22
``` and enter my password only to have it report:

> clear: No value for $TERM and no -T specified


Welcome, (my username), to the NetHack Tournament 2008

NetHack help can be obtained by pressing the '?' key
during a game session

This session will be recorded for posterity; after the session you will be given a playback file identifier by which you can refer to it from the /dev/null/nethack site.

Here is a nice login message for you ...

Be careful in there.


And upon hitting enter:

> Press <Return> to begin.
Happy gaming!
--More--clear: No value for $TERM and no -T specified
NetHack (gettty): Operation not supported
NetHack (settty): Operation not supported
Can't get TERM.
Thank you for recording your gaming session.
The stored file for that session is "(my username).2008-11-09-17-22-27", should you care to publish it for others' entertainment.


One last enter (*1):

> Would you like to return to NetHack?(y/n)  This is a nice logout message for you ...

Have another day.


And then I'm back in my home directory.  However, if I type "y" before I hit enter right *before* this prompt came up (back at *1), then instead of ejecting me, it would start all over from the first quote.

So after a bit of looking around, I tried a few things.  First, I made a file titled "config" at ~/.ssh.  I made the contents simply:

```
SendEnv TERM
```

That didn't help at all so I tried changing "TERM" to "$TERM", then to "TERM=xterm" and "$TERM=xterm", and none of that worked.  So I deleted ~/.ssh/config and tried simply adding the SendEnv stuff to the end of the ssh command.  That didn't work either.

I looked around the internet a bit, and the only thing that looked relevant was [here]("http://bbs.archlinux.org/viewtopic.php?pid=343292#p343292"), and it looks like it might actually be what I need.  Unfortunately, I don't understand what I'm supposed to *do* with that.

It can be inferred from earlier in my post, but just to make it clear, my terminal is xterm.  Also, I don't think it's a serverside issue, because I tried another server as well and got the same problem.

Anyway, how can I connect?  What's wrong and how do I fix it?

Sorry for making such a long post, but I'm not very technically savvy, and I worried that if I left anything out of those quotes earlier I might end up taking out some information that would help in identifying my problem.

Thank you very much.

---

### Post by prinny42 on 2008-11-11
Bump.

---

