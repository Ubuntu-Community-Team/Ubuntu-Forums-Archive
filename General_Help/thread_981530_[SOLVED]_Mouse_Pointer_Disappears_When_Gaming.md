---
title: "[SOLVED] Mouse Pointer Disappears When Gaming"
date: 2008-11-13
forum: General Help
---

### Post by lrs52200 on 2008-11-13
Hi all.  And thank you in advance because I know you're going to have the resolution to the following problem:

  I am running Ubuntu 8.04.  I have an HP Vectra VL420 (about 6 yrs. old).  The only changes I made to the computer since I purchased it several years ago is that I installed an nVidia GeForce2 graphics card, and threw in 2 new HDDs.  Everything on this machine has worked flawlessly........until recently.  
  I downloaded and began playing Tremulous.  No problems.  However, several minutes into the game (maybe 15?) my computer decided it was time to move from full screen to window (it did this on its own without any help from me).  Then my mouse disappeared.  That is, my mouse pointer disappeared.  I could still hear sound and see active graphics (I was killed by some nice passerby), but I was unable to interact with the computer in any way.  I was, and still am, clueless.  I moved the mouse, clicked the mouse, clicked ESC.......all to no avail.  My computer seemed like it would respond, if only I had a mouse.  I even unplugged the mouse to see if the machine would somehow magically "find" the mouse again.  No dice.  Nothing.  Zip.  Nada.  
  What to do?  I couldn't even shut down the machine.  I could do absolutely nothing.  I even waited for about 1/2 hour to see if maybe the thing would just come back on its own, but it didn't.  
  The only thing I could do was a hard shutdown.  Big mistake.  On reboot, I received the oft dreaded "disk died exit status 8" error.  It gave me the option of Ctrl D to continue the boot.  Well, that did nothing for me except give me the black screen with a logon prompt (I think that's the shell?)  Anyway, being entirely unfamiliar with how to login this way (because using my username and password didn't seem to get me where I wanted to go) I used the Live CD to try to boot.  I wasn't able to successfully boot no matter what I tried.
  My problem is that I don't know how to interact with the shell to get me back into my desktop.  Can you help me?  I didn't know how else to correct this problem so I ended up reinstalling the operating system.  Problem is, that the mouse issue is unresolved so I'm sure it will happen again as soon as I begin playing another game.  Please note that when I play the games that came with Ubuntu (tetravex, mahjongg, etc) I do not experience this problem, only when I play 3D games).  I need to know not only how to fix the mouse issue, but more importantly, how to interact with the shell in this situation so that I can log back into my desktop.
  So that you know, I am running the "restricted" drivers for the card and using the "extra" visual effects.  
  Please remember that I am very, VERY new to Linux & Ubuntu and haven't mastered your 'lingo,' and unfortunately - as seen by my drastic fix of the problem - am really quite a noob.  If I haven't provided you enough information, please let me know.  
  Again, I thank you.
Pam

---

### Post by jpkotta on 2008-11-13
Do you have an NVidia or ATI graphics card?

In Trem, you can get your mouse back when the console is down.   Get the console with '`' (just below ESC, shifted it's '~').  You can make it start windowed with ```
tremulous +set r_fullScreen 0
```

---

### Post by lrs52200 on 2008-11-13
Hi jpkotta-

  I have an nVidia GeForce2 MX/MX 400.

So, if I understand you correctly, when my screen downsizes & my mouse disappears, if I click the ~ key, the terminal comes up and I type: tremulous +set r_fullscreen 0   -   and my screen will return to full screen.  But will this make my mouse reappear as well?

---

### Post by jpkotta on 2008-11-14
> **lrs52200 said:**
> 
So, if I understand you correctly, when my screen downsizes & my mouse disappears, if I click the ~ key, the terminal comes up and I type: tremulous +set r_fullscreen 0   -   and my screen will return to full screen.  But will this make my mouse reappear as well?

No.  You launch trem with the command I gave.  That will make it windowed, and hence more well-behaved in my experience.  If you add "set r_fullscreen 0" to your ~/.tremulous/base/autoexec.cfg, or type it in the console, it will have the same effect.

When you press '~' or '`' in game, it drops down the console.  When the console is down, it frees the mouse.  Otherwise the game grabs the mouse.

It's kind of lame to have a windowed game.  What I did was set the resolution to the same size as my monitors', and told my window manager not to draw a title bar and borders around the tremulous window.  I had to do this because I have dual screens and fullscreen is buggy with them.

---

### Post by lrs52200 on 2008-11-14
Thank you again for your help!!! :)  I will definitely try this today.  You're awesome!!

---

### Post by lrs52200 on 2008-11-14
jpkotta-

  It works perfectly.  No errors at all.  Yes, you are right that playing in a window isn't as much fun.........but it's more fun than not playing at all!!!  :)

  Thank you!!!!!

---

