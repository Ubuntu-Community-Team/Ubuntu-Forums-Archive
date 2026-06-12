---
title: "Ubuntu Freezes at &quot;Username:&quot;"
date: 2008-07-30
forum: General Help
---

### Post by Dan0776 on 2008-07-30
Hello all,

I've searched the forums, but don't believe that my problem has been addressed.  I just installed Ubuntu on my ATI 64 3000+ Windows machine, and the installation went smoothly but I got a freeze right when "Username:" pops up.  I had to use Alt-PrintScreen-B to reboot the machine.

Then, I tried to boot differently by holding escape during boot, and selecting that 2nd option (forget the name of the mode off-hand). This time, once I hit "resume" or "continue" or whatever, Ubuntu worked 100%.   I played with it for about an hour with no issues.  I even updated to the latest versions of everything (59 downloads)

I shut down Ubuntu, and tried the regular mode again, and got a freeze.  When I tried to reboot through that 2nd option, again the OS booted smoothly and showed no problems.  I installed nothing and made no changes on that second trial run.

Now, however, in both modes for no apparent reason, I get the freeze at the "Username:" screen.  Effectively, there is no way to get back into a booted Ubuntu.

Any ideas why this would have worked then not worked, and never worked under the regular boot mode?

Thanks in advance,
Dan

---

### Post by Pro-reason on 2008-07-30
That's a strange bug.

How frozen is it?  Can you get to the TTY terminal by pressing Ctrl + Alt + F1?  In that case, you could log in.

---

### Post by Dan0776 on 2008-07-30
Unfortunately, none of the Alt-F-keys did anything.  The only option as I could tell was to Alt-Prtscrn-B to reboot.

I'm pretty new to all of this, but I know there must be a way to get it up and running.

EDIT - Oops, I didn't realize you said Alt-Ctrl-F1 which I haven't tried.  I will try it now, thanks for the suggestion

---

### Post by Dan0776 on 2008-07-30
Hmmm - Actually, no that didn't work unfortunately.

This time, though, I did the regular boot, and I was able to type in my Username.  The prompt for Password: came up, and the freeze happened there.

Seems to be no rhyme or reason to this freeze...

---

### Post by pi.boy.travis on 2008-07-30
Did you check your install CD for errors?  I had a similar problem on one of my machines when I first installed 7.10.  The faulty install disk messed up lots of things. . .

---

### Post by Dan0776 on 2008-07-30
Yeah - I burned the download-install file to a DVD using Alcohol 120%, and it verified all correctly.  Thanks for the idea though.  I bet its something simple like that.

---

### Post by Pro-reason on 2008-07-30
So, it's a 64-bit machine.  Did you use the 64-bit version of Ubuntu?

---

### Post by pi.boy.travis on 2008-07-30
Could be a GDM issue, but I'm not sure myself how to mess with it when you can't login. ..

---

### Post by Dan0776 on 2008-07-30
> **Pro-reason said:**
> So, it's a 64-bit machine.  Did you use the 64-bit version of Ubuntu?

Yeah, it's the correct version.

A new thing just happened - it allowed me to enter Username and Password, logged in for a second..  I then opened a window (Add/Remove programs) and then it froze up.

Alt-Prtscrn-B didn't work that time so I had to do a hard reset.

---

### Post by Pro-reason on 2008-07-30
I know nothing of 64-bit machines, but I seem to remember reading that you can install either version of Ubuntu on such a machine.  Different issues arise with each one.  This may be something to look for in the 64-bit forum.

I'd certainly recommend reinstalling something in any case.

---

### Post by pi.boy.travis on 2008-07-31
I have a 64 bit Intel C2D and I'm running 32 bit 8.04.  No problems here!  I'm planning on switching for 8.10 though.

If you can login and get to the desktop it definitely isn't GDM.  It has me stumped. . .

---

### Post by Dan0776 on 2008-07-31
Hmm, maybe I could try to uninstall the 64 bit version, and try the 32 bit instead?

Does anybody else run the 32-bit on a 64 bit machine?

I wonder what type of effects that sort of install would create.  Would it be buggy or slow?

Thanks everyone for all your suggestions so far.  I am determined to get to the bottom of this!

Dan

---

### Post by pi.boy.travis on 2008-07-31
I find that 32 bit runs better on my machine.  I my opinion, the only reason you would need 64 bit is if you had more that 4 GB RAM.

---

### Post by Dan0776 on 2008-07-31
Cool, I think I'll try that - This evening, I'll uninstall the 64 bit and go 32, then I'll post here if that fixed the freezing problem.

Thanks for the tip

Dan

---

### Post by Dan0776 on 2008-07-31
I tried to install 32-bit version, and unfortunately the same bug happens, freezing at Username:

I think I will try to uninstall and move on with my life...  but unfortunately again, the "Uninstall Ubuntu" app in Windows doesn't execute.  Do you all think its safe just to erase the folder, or did some things get done to the Windows Boot files that I need to fix...

---

### Post by pi.boy.travis on 2008-07-31
You installed via Wubi?  I tried Wubi out, eventhough I already had an Ubuntu installation, just as a test.  It wouldn't even boot after install.  I would try a full install if you really like Ubuntu.  My experience shows that Wubi is still a little. . . unstable. . .

---

### Post by Dan0776 on 2008-07-31
> **pi.boy.travis said:**
> You installed via Wubi?  I tried Wubi out, eventhough I already had an Ubuntu installation, just as a test.  It wouldn't even boot after install.  I would try a full install if you really like Ubuntu.  My experience shows that Wubi is still a little. . . unstable. . .

Hmm, Wubi?  I'm not sure what that is..  I went to the Ubuntu site and downloaded an ISO, then burnt that to a CD.  Then, when I inserted the CD I could choose "Install within windows" and I selected that, and put it on a different hard drive (Windows is C:, Ubuntu is J:).

Anyway, is there another more stable way to install?  I have windows stuff on my J: Drive that I don't want to erase, but I have about 55 GB free for Linux.

---

### Post by pi.boy.travis on 2008-07-31
> **Dan0776 said:**
> Hmm, Wubi?  I'm not sure what that is..  I went to the Ubuntu site and downloaded an ISO, then burnt that to a CD.  Then, when I inserted the CD I could choose "Install within windows" and I selected that, and put it on a different hard drive (Windows is C:, Ubuntu is J:).

Anyway, is there another more stable way to install?  I have windows stuff on my J: Drive that I don't want to erase, but I have about 55 GB free for Linux.

Wubi is a method of installing Ubuntu.  To make a long story short, it basically makes a sort of virtual partition stored as a Windows file.  Ubuntu resides on this.  This method is good way to try out Ubuntu. (if you can get it to work, I've never had any luck with it. . .)

Normally, you would shrink your Windows (or other) partition(s) to make unallocated space to install Ubuntu in a *real* partition. (Unallocated meaning not just free space, but no partition there at all.)

Try the Ubutnu live session.  Just reboot you computer with the disk in your drive.  If your BIOS boots Windows anyway, give us your computer model and we can help you adjust it.  The live session will let you try out Ubuntu without installing it.  You can install Ubuntu alongside Windows in it's own partition, instead of "inside" it.

Let us know if you need help with partitions, installing, etc.  Were here to help you out!  ;)

Hope this helps!

---

### Post by Pro-reason on 2008-07-31
Argh, so all this time we weren't talking about a real Ubuntu installation, but a Wubi (Ubuntu as a Windows app) installation?  No wonder there have been problems.  This should be in the Wubi forum.  I have no expertise in this.

---

### Post by pi.boy.travis on 2008-07-31
> **Pro-reason said:**
> Argh, so all this time we weren't talking about a real Ubuntu installation, but a Wubi (Ubuntu as a Windows app) installation?  No wonder there have been problems.  This should be in the Wubi forum.  I have no expertise in this.

Agreed.

Dan0776, don't give up on Ubuntu!  I was ready to give up on Ubuntu after 7.10, but 8.04 runs perfectly!  Don't give up on Linux because of one bad experience!

---

### Post by Dan0776 on 2008-07-31
> **pi.boy.travis said:**
> Agreed.

Sorry guys, I'm pretty new to all this.

As it turns out, my CPU freezes on boot of both CD versions of the OS.  When I go to "Install", it shows the desktop with that orange bird-background, a window comes up that says "Install" or something to that effect, and it freezes there.

I don't believe my computer is capable of running this OS, for some reason (AMD 3000+, 1 GB of ram, lots of disk space, etc.).

Perhaps if I get a new computer I will try again.  Thank you all for your help

---

### Post by p_quarles on 2008-07-31
Moved to the Wubi section.

---

### Post by ago on 2008-08-01
Boot in console and look at the logs in /var/log. In particular syslog and xorg

---

### Post by SR_ELPIRATA on 2008-08-11
Hello folks:

I have a similar problem with one of the computers I've installed Ubuntu via wubi. I have been spreading the word about Ubuntu since I used it for 3 months and now with the 8.04 I find that some stuff is even easier to use.

Ok, so I got this friend who has a HP Amd64 3800+ 1gb ram and told her that she could try ubuntu without losing xp media center (Im confident she may move later on) so I went and did the wubi install with the 8.04 desktop 32bit, and it did the installation just fine and when I get to the point in which you log in for the first time, enter user, enter password, and the bird appears and then it hangs/freezes there.

Alt+Ctrl+F1 didnt work.

I'm going to check those logs now, as suggested above, but this is something that it hasnt happened before to me. This would be, yes, the first 64bit amd that I get to try this software on, as the other machines were a Sempron 2400, a dual core Pentium and a Duron system.

I havent tried the 64bit ubuntu, but I fear I'd have the same problem as he described.

ELP

---

### Post by SR_ELPIRATA on 2008-08-11
I got into the recovery mode, went to the /var/log directory and I can see the syslog (and syslog.0) and the Xorg files. What Im supposed to look into them? I see a lot of stuff but to me is not understandable.

ELP

---

### Post by SR_ELPIRATA on 2008-08-11
BTW I wanted to mention that this system has a Ati radeon express 200. I just tried using the live version and it loaded up sort of well, stopped int he username and there was a counter saying that in 10 secs it would log in as ubuntu (which I know is normal, though this is the first time I see it).

Then, 10 secs go by and tries to log in and click.. its back to username section, waits 10 secs, tries again, and this time I get to the desktop sort of, it doesnt shows neither of the top and bottom bars, but I can see the normal install and examples folders in the desktop.

I then used alt+ctrl+F1 and it tried to show these top/bottom bars but it froze, the graphics looks also distorted and not the usual gray/white colors but red and green shown. You cannot see the bars as usual btw, just those odd lines.

At this point, mouse is unusable.

ELP

---

