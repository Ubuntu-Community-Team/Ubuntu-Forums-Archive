---
title: "Synergy slow, num lock always on"
date: 2008-04-26
forum: Hardware
---

### Post by Svip on 2008-04-26
I recently upgraded to Heron.  And what has become a tradition with each upgrade, there are things that worked perfectly before which I relied heavily on, but are no longer working.

Both involve input.  I don't use my laptop's own keyboard.  Because it is no more.  Instead, I use a wired Apple keyboard.  It worked perfectly fine with Ubuntu until the upgrade.  Then it can only accept what is normally the fn num pad.  And I cannot turn the num lock off with it, but I can turn it on with it.

At home, my laptop is connected to my desktop with synergy.  It used it as smooth as it could be, but now it appears to be slow, coughy and unresponsive.  Both involving mouse movement and keyboard input.  It gets through, but this is not a frame buffer from 1980, kthx.

I realise the num lock issue can be fixed by turning num lock off at start, but what if I accidentally clicks it while working?  I cannot turn it off, I'll have to get another keyboard.  I want key input to be normal, this is not a laptop keyboard, this is a full sized keyboard.

---

### Post by Fitzsimmons on 2008-04-27
Same problem.  Watching topic in hopes of replies for solution.  Between this and horrible font problems I would call this upgrade a failure.

---

### Post by hopfrog238 on 2008-04-27
I had the same issue.  Running synergyc as root (not terribly convenient) seems to fix the issue.  I saw the solution on this thread [http://ubuntuforums.org/showthread.php?t=767236&highlight=synergy](http://ubuntuforums.org/showthread.php?t=767236&highlight=synergy) .

I had no idea how much I depended on synergy until this hiccup!

---

### Post by Fitzsimmons on 2008-04-27
This is a well known bug and apparently there's a fix in the pipe:

[https://bugs.launchpad.net/bugs/194029](https://bugs.launchpad.net/bugs/194029)

---

### Post by Svip on 2008-04-27
> **Fitzsimmons said:**
> This is a well known bug and apparently there's a fix in the pipe:

[https://bugs.launchpad.net/bugs/194029](https://bugs.launchpad.net/bugs/194029)

Compile my own kernel?  Argh :(  Well, if it must be so, then it must be so.  However, no one have commented on my keyboard issue (unrelated to synergy).  Because that is quite annoying when I am not using my laptop at home.

---

### Post by moon2js on 2008-04-27
I'm running synergyc with sudo, and it seems to work fine that way. It is annoying though, and I hope an update fixes whatever kernel scheduler is interfering.

---

### Post by Zoxive on 2008-04-28
I have the same problem, but running as sudo does not fix it completely. It only helps a little but, but there still are times where it is completely unresponsive.

The Server is on Windows XP, and client is the new Ubuntu 8.04

---

### Post by LeeU on 2008-04-29
Same problem here. Running it as root does work, I'm just not sure why others would find it annoying. (Maybe I'm missing something.)

---

### Post by moon2js on 2008-05-01
> **LeeU said:**
> Running it as root does work, I'm just not sure why others would find it annoying. (Maybe I'm missing something.)

[[IMG]http://imgs.xkcd.com/comics/sandwich.png[/IMG]]("http://xkcd.com/149/")

---

### Post by Svip on 2008-05-01
What worked best was running the entire thing on an earlier kernel.  Additionally, that also made my keyboard work.  So I guess I won't be using a newer kernel until these issues are fixed.

Thank you for your suggestions.

---

### Post by toarlach on 2008-05-01
If anyone has the solution to this problem, can they post it here?

I've tried 'sudo synergyc synserver', and it still doesn't work :(

---

### Post by Svip on 2008-05-01
> **toarlach said:**
> If anyone has the solution to this problem, can they post it here?

I've tried 'sudo synergyc synserver', and it still doesn't work :(
Like I said, using an older kernel may help.  I am not sure how to download an older one, but it should be possible.  Alternative you could compile one yourself.  You could of course just wait till they fix the issue in the next release of the kernel.

---

### Post by Martysnarf on 2008-05-01
Yeah I have the same issue- mouse a REAL hassle to use with Synergy.  Didn't have this problem in Fedora, but I like Ubuntu 8.0.4 so much better that I'll just deal until the fix comes.  Thanks for posting about this; was a big help. THANKS!

---

### Post by helpdeskdan on 2008-05-14
"Nicing" it works well for me, as another user reported:

sudo nice -n -20 synergyc <server IP>

---

### Post by chris.innove on 2008-08-13
Guys, a little solution for the num lock thing on a laptop + other interesting info:

[http://rfdlinux.wordpress.com/](http://rfdlinux.wordpress.com/)

And I am actually writing with my apple keyboard :D

See ya



===============
[email]chris.innove@gmail.com[/email]

"Knowledge speaks, but wisdom listens" Jimmy Hendrix

---

### Post by kubuntuuser on 2008-11-05
Possible Solution:
I remembered on Hardy that I had to turn off "Pointer can be controlled using the keypad" by going to system->keyboard->Mouse Keys tab in order to use my number pad correctly. That seemed to be a feature of the upgrade, the same happended to me with intrepid.

I couldn't use my number pad in gnome or using on any synergy desktop and the above sorted me right out. Let me know if this was what you were looking for. 

Kris

---

