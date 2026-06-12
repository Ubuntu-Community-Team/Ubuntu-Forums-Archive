---
title: "[SOLVED] What's Using Up All My Memory?"
date: 2008-07-14
forum: Hardware
---

### Post by HotDogBunToo on 2008-07-14
So I'm running on a system that at the moment runs on a gig of ram... so seeing how this is limited I am careful of how many programs I run at once.  

I usually start off with only 300MB of ram used when I first login.  Programs I use most often is VirtualBox, Firefox, Amarok, and Nicotine+.  However even if I close all 4 of these programs that drives my RAM usage, when I look in 'System Moniter' to look at the processes, I'm still over here using up over 900MB of ram!!

And while I'm planning on eventually adding another gig of ram on here, I'm concerned if that'll just mean that I'll just have a week before I need to hit ctrl+alt+bksp instead of every few days as it is now to clear out my memory.  Not sure why my PC is still hogging so much memory when I close everything up **_*AND*_** not showing up in 'Processes' so any help could be greatly appreciated here.

---

### Post by snowpine on 2008-07-14
VirtualBox is a memory "hog" because, however much RAM you allocate to your virtual machine, you have to subtract that from your available RAM. 

How much swap do you have available? As long as you have plenty of swap, I wouldn't worry about it too much.

---

### Post by lswest on 2008-07-14
next time you notice your system being bogged down can you run ```
free
``` in the terminal and save (or post directly) the output?  If most of that 900MB of RAM is being cached I wouldn't worry about it.  If it's actually being used then chances are the virtual machine didn't shut down right (generally choose "shut down machine" when closing virtual machine windows, I find it works best).

---

### Post by HotDogBunToo on 2008-07-14
Hey thanks for the input yall!!

Didn't think you good folks would respond so quickly otherwise I would've held off on rebooting so I might have to wait another few days for issue to arise again lol.

But once it does I'll use the **free** command to see what's going on (unlike the 'System Moniter' it seems I can also see the cached memory which might be the culprit).  I do have 2GB of swap memory allocated but I'm just concerned about still needing to rely on that once everything is closed.  Even though I'm sometimes careless in forcing VirtualBox off I do for the most part shut down properly so I'll double check to ensure that I am.  I do allocate 192MB of RAM for it so it '**may**' be possible that this is floating around after afew shutdowns here & there :\

---

### Post by hellzkeeper1216 on 2008-07-14
I use to use virtual machine and it was a memory whore. so now i use htop
code:
sudo apt-get install htop

then when you want to run it, just open your terminal and type htop.

---

### Post by HotDogBunToo on 2008-07-17
Figure I'd post now since the system is still up at 800MB being used (after 890 and things get sluggish lol).  Closed all the extra programs including VirtualBox (which I ensured I closed properly) and still going past the 800meg mark.  I typed the 'free' command and this is what I'm getting.

```

             total       used       free     shared    buffers     cached
Mem:        969984     929700      40284          0       5900      91692
-/+ buffers/cache:     832108     137876
Swap:      2104464     333248    1771216

```

Of course I'm running FireFox3 and that's only using 40MB at the moment (since I had to restart that several times).  Appreciate the help I received thus far and will continue to be receptive of anything else you good folks can figure out :)

---

### Post by stchman on 2008-07-17
> **HotDogBunToo said:**
> So I'm running on a system that at the moment runs on a gig of ram... so seeing how this is limited I am careful of how many programs I run at once.  

I usually start off with only 300MB of ram used when I first login.  Programs I use most often is VirtualBox, Firefox, Amarok, and Nicotine+.  However even if I close all 4 of these programs that drives my RAM usage, when I look in 'System Moniter' to look at the processes, I'm still over here using up over 900MB of ram!!

And while I'm planning on eventually adding another gig of ram on here, I'm concerned if that'll just mean that I'll just have a week before I need to hit ctrl+alt+bksp instead of every few days as it is now to clear out my memory.  Not sure why my PC is still hogging so much memory when I close everything up **_*AND*_** not showing up in 'Processes' so any help could be greatly appreciated here.

Are you using 64 bit OS?  If yes then that is a culprit.  64 bit OS uses a lot more RAM that 32 bit OS.

---

### Post by him610 on 2008-07-17
Take a look at the dynamic usage of your cpu, memory, buffer, and swap activity by your entering from a terminal CLI:

```
top
```

You will also benefit from a display of the running processes and the demands each is making on system resources.
 
Cheers.

---

### Post by HotDogBunToo on 2008-07-18
Thanks folks

Well yesterday when I had a problem I had used the **top** command which showed me that compiz.real was using like 65.1 for MEM%

So even though I'm seeing that compiz.real is only using afew megs of ram in System Moniter, the MEM% is showing that this is the actual culprit?  If it is then how would I free these resources away from Compiz?  Would I have to turn off advanced desktop settings then turn them back on to restart it or something?

---

### Post by HotDogBunToo on 2008-08-21
Well, after continual runtime of not running Compiz, I guess I can now say with confidence that Compiz is the problem application that leaks memory like crazy.  So since this topic asks the question of "what?" and I have that answered - I can now mark this topic as resolved and [made a separate thread for Compiz itself here]("http://ubuntuforums.org/showthread.php?p=5635916#post5635916")

---

