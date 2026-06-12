---
title: "All kinds of issues...really could use some help..."
date: 2008-11-11
forum: General Help
---

### Post by mlissner on 2008-11-11
Since upgrading to Ibex a few weeks ago, I've been dealing with some issues. So far, I haven't been able to resolve a number of them, and they're rather difficult to live with. Any help would be greatly appreciated.

1) Firefox & Evolution gray-outs. For some reason these two programs gray out a lot. I'll be working on something, and the next thing I know it will freeze, go gray for about 30 seconds, and then return to normal. I've checked the logs, tried the old kernel, watched the CPU (it's not struggling), and I can't figure this out. 

2) GDM resets when I change resolution. I can connect my laptop to my monitor and change the resolution without any trouble. When I disconnect it, and try to change the resolution back, GDM gets reset, and I have to log back in, and figure out where I was in my work. This wasn't a problem with Hardy, and I have no idea how to appraoch fixing it in Intrepid.

3) Random freeze-ups requiring restart. My computer has been freezing up randomly since I upgraded. When it does, the mouse still moves, but clicking does nothing. The wireless light on the laptop blicks intermittantly as does the caps lock button. The only solution so far is to hard-reset it, which I don't really like to do.

Any and all suggestions would be more than welcome.

---

### Post by mlissner on 2008-11-12
4) Lest I forget, gksudo doesn't work either. Whenever I need to run something as root, it shows up in the task bar, tries to work, and then fails. Even sudo doesn't work like it should. It takes about a minute and a half to return a response prompt.

---

### Post by 3rdalbum on 2008-11-12
GDM restarting is a classic symptom of everyone's favourite computing problem, badly written graphics drivers. If there is a later version available from your graphics chipset's vendor, you should give it a try. It could be causing the random freezes too.

The other problems, I don't know what could be causing them.

---

### Post by CatKiller on 2008-11-12
> **mlissner said:**
> 1) Firefox & Evolution gray-outs. For some reason these two programs gray out a lot. I'll be working on something, and the next thing I know it will freeze, go gray for about 30 seconds, and then return to normal. I've checked the logs, tried the old kernel, watched the CPU (it's not struggling), and I can't figure this out.

This is a feature of Compiz (the window manager used for Desktop Effects). It is a visual representation that the window is unresponsive to window manager requests (i.e., when you get the busy cursor animation). As far as I can tell, it mostly happens when Firefox is waiting for a response from a remote server before it can finish rendering a page. It's not really anything to worry about, and you can turn it off by turning off the "Dim Unresponsive Windows" setting of the Fading Windows plugin in CompizConfig Settings Manager.

---

### Post by mlissner on 2008-11-12
Thanks guys. It's nice to have a couple ubuntu veterans on the job.

@3rdalbum, for hardware, I have the:```
Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller
```. I didn't have this problem on previous installations, so I'm befuddled why this is occuring now. Do you still think that's my problem? I thought the intel graphics cards worked pretty well? 

@CatKiller, I wish it were so easy. I spent some more time on this problem last night, and I learned that whenever Firefox grays-out, it's hung on a futex_wait, whatever that means. I think it's some kind of kernel wait message, but it's not your run of the mill wait. It happens so much that my browser usage is going to soon be switched to konqueror, which would be pretty crazy (for me). In any case, it's not the gray-out that I mind, it's the freeze/thaw.

For problem four, gksu, I noticed that it seems to be caught on a hrtimer_nanosleep, whatever that means. I learned this by running it, and then looking in the system monitor under the "waiting channel column". I had about four gksu instances sitting there waiting for the hrtimer_nanosleep to bounce back. Anybody know anything about these waits? They're my current best theory.

---

### Post by mlissner on 2008-11-12
One more update, I moved .mozilla, and then performed a sudo aptitude reinstall firefox, and the problem is still there. Very frustrating to have this slowness in my browser.

---

### Post by CatKiller on 2008-11-12
> **mlissner said:**
> @CatKiller, I wish it were so easy. I spent some more time on this problem last night, and I learned that whenever Firefox grays-out, it's hung on a futex_wait, whatever that means. 

Sorry I wasn't much help then. There's information on what *futex_wait* is [here]("http://ds9a.nl/futex-manpages/futex2.html"), but it doesn't mean much to me. Perhaps you need to file a bug against Firefox to get it fixed.

---

### Post by mlissner on 2008-11-12
Well, sadly there is a bug, but it's filed against the kernel. What's interesting is that even if I revert to earlier kernels, remove mozilla preferences, and reinstall Firefox, I still have this problem. Thanks for the link though, I hadn't found that yet. I can't say it does much for me though.

---

### Post by josephellengar on 2008-11-13
> **mlissner said:**
> Since upgrading to Ibex a few weeks ago, I've been dealing with some issues. So far, I haven't been able to resolve a number of them, and they're rather difficult to live with. Any help would be greatly appreciated.

1) Firefox & Evolution gray-outs. For some reason these two programs gray out a lot. I'll be working on something, and the next thing I know it will freeze, go gray for about 30 seconds, and then return to normal. I've checked the logs, tried the old kernel, watched the CPU (it's not struggling), and I can't figure this out. 

This issue is pretty common.  There's a good script to deal with it here: [http://ubuntuforums.org/showthread.php?t=969826](http://ubuntuforums.org/showthread.php?t=969826)  A lot of people have had it.  Apparently it has something to do with java.

---

### Post by mlissner on 2008-11-14
Unfortunately, I don't think that would have helped, since this was unrelated to flash, and had to do with the futex_wait problem. 

In the end, I just had to reinstall Intrepid and restore my data from my backup. It seems that upgrades just don't work.

---

### Post by mlissner on 2009-01-16
Just a follow-up to my follow-up, I'm still having regular futex_wait problems that cause this or that program to fail. If anybody finds any answer or understands futexes, I'd love to hear.

---

### Post by mgangav on 2009-01-31
I found this this thread while searching for a solution my own futex_wait problem.

Any solution would be greatly appreciated.

---

### Post by mlissner on 2009-02-01
Hmmm...I still haven't figured this out. I filed a bug about it on gvfs, but I haven't been able to get a stack trace, so the bug may be for nothing. 

The link is here: [http://bugzilla.gnome.org/show_bug.cgi?id=569229](http://bugzilla.gnome.org/show_bug.cgi?id=569229)

Keep me posted if you figure anything out.

---

