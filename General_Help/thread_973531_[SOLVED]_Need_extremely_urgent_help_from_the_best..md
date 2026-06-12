---
title: "[SOLVED] Need extremely urgent help from the best. EVERYTHING is broken! 8.10 killed"
date: 2008-11-06
forum: General Help
---

### Post by Spades_Neil on 2008-11-06
Problem solved, but I'm leaving my post just in case someone else had a similar melt down.

Solution on Page 3.

> **soro2005 said:**
> You know how you changed it, but we don't. So it's difficult to have a guess at what's the problem, with that little information. Upon upgrading, the xserver (graphics server) has configured itself to meet the specs and methods of its new version, and my guess is that that has gone wrong, possibly because there was an old config file in the way. You could verify this by starting the computer from an Intrepid Live CD and see whether you have all the desktop effects, etc.

What graphics card do you have, anyway?



The step-by-step instructions are the same as above, really:
1. Start the computer from the harddrive, NOT from the live CD.
3. At the login window, flickering or not, hit, at the same time, ctrl+alt+F1. This key combination should get you to a black window with a login prompt ("terminal"). If it doesn't, try ctrl+alt+F2.
4. At the login prompt, log in with your username and password.
5. type ```
sudo dpkg-reconfigure xserver-xorg
``` Follow the instructions. Just accept the defaults by hitting <enter>.
6. Once all questions are asked and you're back at the command prompt, type ```
sudo reboot
```

If you're lucky, you have your graphics server back.

This is how I did it.

--------------------------------------------

Upon installing 8.10 on my computer, I had problems right away. The login screen started scrolling rapidly and insanely and the screen rez was ruined.

I posted here for help, but no one told me how to figure out anything about my system or my monitor, so I was screwed and had to do it myself.

My theory was the screen hertz (or whatever it's called) was too high. I went to change it, and the screen went black. **What's *supposed* to happen, is I get 15 or so seconds and it resets!** Yea, it didn't do that. I waited way longer than 15 seconds. I was forced to reboot. I started up again, EVERYTHING WAS RUINED. I cannot use my computer AT ALL now.

Right now I'm resorting to a 7.10 disk to salvage files. Major problem though, I cannot get all of my files. For some idiotic reason, files that I never told to do this, are somehow locked and have "none" for accessibility. Valuable files will be GONE if I don't find a way around this.

Right now, everything is being moved to a flash drive and onto a safe computer. The stupid 8.10 is what caused this mess, and I want to go back to an older version WITHOUT losing my old files. How can I possibly downgrade without breaking my screen again? I want it all to be set back to 60 Hz because that worked absolutely fine.

> 
**This issue so far has been solved.**
If all else fails, I want my files back. I can't get them through this disk however. I know there's got to be a way to bypass this, but what is it?
[B]Solution: gksu nautilus, home folder -> media -> disk -> and I have all my files from all my settings.
Hmmm... I wonder if I could use this same method to rescue another computer, Windows OS, that I once killed.[/B]

> 
**Sorta-solved.**
In addition, how do I get my old 'favorites' off of Mozilla Firefox from my old settings? Again, Mozilla folder is cut off and thus unusable. Again, I need a way around this, but even past that point, I don't know what to do next.
**In theory, copy/paste the old files from the .Mozilla folder, save them, then paste them back into the folder when you reinstall Ubuntu. BACK UP THE ORIGINAL FILES THOUGH JUST IN CASE!! It's only a theory!!**

I'm in need of very urgent help. Screw simplifying things, throw whatever tech talk you have to at me to fix this. Just try to at least go through it by steps.

My first priority is rescue all of my files.

---

### Post by Spades_Neil on 2008-11-06
Also, don't hold back any system abilities 'too powerful for a noob' because at this point I really don't care. I have nothing else left to screw up.

---

### Post by exploder on 2008-11-06
I do not know the size of the files you have but here is an idea. E-mail your important files using the Live CD to your other pc. I have used this method before with success. If I think of any better ideas, I will post back.

---

### Post by Spades_Neil on 2008-11-06
> **exploder said:**
> I do not know the size of the files you have but here is an idea. E-mail your important files using the Live CD to your other pc. I have used this method before with success. If I think of any better ideas, I will post back.

I'm already moving the files I can, but that is not my problem.

This is my problem.

[IMG]http://i38.tinypic.com/2co52bk.png[/IMG]

Anything with a little orange X, I can't copy, move, send, or view.

---

### Post by cariboo on 2008-11-06
To move files you don't have perrmissions for, use nautilus in root mode. To do this press Alt-F2 and type:

```
gksu nautilus
```

This will open Nautilus in /root, so you will have to navigate to your home directory in order to move any files.

Jim

---

### Post by exploder on 2008-11-06
Try "gksu nautilus" in the terminal. You should have access as root.

---

### Post by Spades_Neil on 2008-11-06
gksu nautilus doesn't work. It only works for the uninstalled root folder, not the one already on my computer that has everything in it.

This was my first guess, but it still doesn't work...

Like I said, give me the most potent stuff you have. I don't care what files I lose now because whatever I can't save anyways, then it was worth a try.

---

### Post by sirebral on 2008-11-06
Maybe you can grab a lesson in terminal.

Alt - F1 on the machine that is screwed should get you there.  Mount a drive and have a day!

You might also try fixing your install from the Virtual Terminal.  Sounds like the problem is a Video Card driver, or maybe it is your resolution.

---

### Post by Spades_Neil on 2008-11-06
Is there any possible way to (force) return my computer to the 60 Hz resolution that it once was?

If I could even do that, all of my problems would be solved. However, I know nothing about this computer's functions, and I don't think I can even do anything without logging in... which is impossible.

> You might also try fixing your install from the Virtual Terminal. Sounds like the problem is a Video Card driver, or maybe it is your resolution.

I really think that is the problem.

---

### Post by Spades_Neil on 2008-11-06
> **sirebral said:**
> Maybe you can grab a lesson in terminal.

Alt - F1 on the machine that is screwed should get you there.  Mount a drive and have a day!

You might also try fixing your install from the Virtual Terminal.  Sounds like the problem is a Video Card driver, or maybe it is your resolution.

Alt - F1 at what point? Before the computer starts up? If it's anywhere past the login screen, there's nothing I can do.

---

### Post by exploder on 2008-11-06
After using the command mentioned above, can you right click on the folder and change the permissions? The whole problem is permissions.

---

### Post by Spades_Neil on 2008-11-06
> **exploder said:**
> After using the command mentioned above, can you right click on the folder and change the permissions? The whole problem is permissions.

If you're talking about gksu nautilus, the answer is no.

---

### Post by Spades_Neil on 2008-11-06
Hang on a second guys. I have a theory.

"disk" which leads to my regular disk, is now nothing but a 'media' type. I'm currently hunting for a way to bypass everything and get to it despite gksu nautilus being in the way of that.

**Edit:** ...Ok, after screwing with it even more, I think I found a bypass to the problem. I'm working on rescuing files right now.

---

### Post by Spades_Neil on 2008-11-06
Ok, how can I retrieve the bookmark files from FireFox on my old disk?

I can get into the folder now, but I don't know what files I should save.

---

### Post by HyperHacker on 2008-11-06
You're not the only one who had the 8.10 upgrade screw everything up. Anyway, I suggest copying the entire .mozilla folder in your home directory. Then when you get it working again, copy back anything that looks like bookmarks. Just make sure you rename files before overwriting them in case they're not the right ones.

---

### Post by Spades_Neil on 2008-11-06
> **HyperHacker said:**
> You're not the only one who had the 8.10 upgrade screw everything up. Anyway, I suggest copying the entire .mozilla folder in your home directory. Then when you get it working again, copy back anything that looks like bookmarks. Just make sure you rename files before overwriting them in case they're not the right ones.

8.10 update needs help... Why is it reminding me of stuff Microsoft sent out and it was all borked? -_-; Ah well. It's an open source community for a reason. Unlike Microsoft, we can at least fix the problems one way or another on our own, for free, and if in doubt we can just kill the hard drive and reinstall everything again.

Did past new upgrades ever have serious malfunctions that messed them up for a good while?

---

### Post by soro2005 on 2008-11-07
To copy your Firefox settings, navigate to the home folder of the user that was using the firefox (with gksu nautilus to /home/yourusername), then hit ctr+h to unhide hidden files, then locate the folder called ".mozilla" as specified above and copy it. It contains all the settings, plugins, etc, and you can actually even migrate your settings to Windows by copying its contents to the right location. For good measure, check out whether there's .mozilla-firefox or .firefox there as well. By the way, most of your other settings and customizations should also be visible in the same folder if you unhide them. Ctr+h toggles hide/unhide in Nautilus.

---

### Post by wersdaluv on 2008-11-07
Do you have a separate home partition for you to expect that the reformat won't delete your files? Are you sure that you didn't reformat the partition with your /home folder?

---

### Post by soro2005 on 2008-11-07
And to get your display back, try changing to a terminal *before* you log into your Gnome session, and reconfigure the graphics server.

To change into a terminal: Press alt+ctr+F1 simultaneously. Log in. If you want to get back to the graphical interface, press alt+ctr+F7. Circle through the F keys if you don't find the window you are looking for.

To reconfigure the graphics server, try:
```
sudo dpkg-reconfigure xserver-xorg
```
This has to happen from the installation, not from the live CD.

By the way: From what you tell, your system is not screwed up. Only the graphics server is misconfigured. This may not comfort you, and perhaps you've already panicked and deleted some essential stuff. But with a little patience, you can achieve many things without a graphical interface (like copying/backing up files; search for a tutorial on rsync, for instance).

It would be easier to see what went wrong if you gave more specific details on what you did, and to what result. How did you change the refresh rate?

---

### Post by Spades_Neil on 2008-11-07
> **soro2005 said:**
> And to get your display back, try changing to a terminal *before* you log into your Gnome session, and reconfigure the graphics server.

To change into a terminal: Press alt+ctr+F1 simultaneously. Log in. If you want to get back to the graphical interface, press alt+ctr+F7. Circle through the F keys if you don't find the window you are looking for.

To reconfigure the graphics server, try:
```
sudo dpkg-reconfigure xserver-xorg
```
This has to happen from the installation, not from the live CD.

By the way: From what you tell, your system is not screwed up. Only the graphics server is misconfigured. This may not comfort you, and perhaps you've already panicked and deleted some essential stuff. But with a little patience, you can achieve many things without a graphical interface (like copying/backing up files; search for a tutorial on rsync, for instance).

It would be easier to see what went wrong if you gave more specific details on what you did, and to what result. How did you change the refresh rate?

Don't worry, I've deleted nothing yet. Why bother?

I know how I changed the refresh rate, and I thought I already explained that. However, for the login window and my sister's profile, the refresh rate changed on it's own upon upgrading. I manually changed the refresh rate on my own settings from 60 to 40 Hz.

As for this new code, how would I go about doing it then? What do you mean from the 'installation' not the 'Live CD'? Some step-by-step instructions would be good.

---

### Post by Spades_Neil on 2008-11-07
> **soro2005 said:**
> To copy your Firefox settings, navigate to the home folder of the user that was using the firefox (with gksu nautilus to /home/yourusername), then hit ctr+h to unhide hidden files, then locate the folder called ".mozilla" as specified above and copy it. It contains all the settings, plugins, etc, and you can actually even migrate your settings to Windows by copying its contents to the right location. For good measure, check out whether there's .mozilla-firefox or .firefox there as well. By the way, most of your other settings and customizations should also be visible in the same folder if you unhide them. Ctr+h toggles hide/unhide in Nautilus.

Do I have to worry about 'downgrading' if I do this? I was on Firefox 3x before it died. Should I just reinstall that version before I replace it's files? (Of course, backing up the existing files just in case.)

---

### Post by soro2005 on 2008-11-07
> **Spades_Neil said:**
> As for this new code, how would I go about doing it then? What do you mean from the 'installation' not the 'Live CD'? Some step-by-step instructions would be good.

You know how you changed it, but we don't. So it's difficult to have a guess at what's the problem, with that little information. Upon upgrading, the xserver (graphics server) has configured itself to meet the specs and methods of its new version, and my guess is that that has gone wrong, possibly because there was an old config file in the way. You could verify this by starting the computer from an Intrepid Live CD and see whether you have all the desktop effects, etc.

What graphics card do you have, anyway?

> **Spades_Neil said:**
> As for this new code, how would I go about doing it then? What do you mean from the 'installation' not the 'Live CD'? Some step-by-step instructions would be good.

The step-by-step instructions are the same as above, really:
1. Start the computer from the harddrive, NOT from the live CD.
3. At the login window, flickering or not, hit, at the same time, ctrl+alt+F1. This key combination should get you to a black window with a login prompt ("terminal"). If it doesn't, try ctrl+alt+F2.
4. At the login prompt, log in with your username and password.
5. type ```
sudo dpkg-reconfigure xserver-xorg
``` Follow the instructions. Just accept the defaults by hitting <enter>.
6. Once all questions are asked and you're back at the command prompt, type ```
sudo reboot
```

If you're lucky, you have your graphics server back.

---

### Post by CaptSaltyJack on 2008-11-07
> **sirebral said:**
> Maybe you can grab a lesson in terminal.

Alt - F1 on the machine that is screwed should get you there.  Mount a drive and have a day!

You might also try fixing your install from the Virtual Terminal.  Sounds like the problem is a Video Card driver, or maybe it is your resolution.

Isn't it Ctrl-Alt-F1? (and I think F2, F3, etc. also work, up to a certain point.. F6 or F7 is usually the X desktop)

---

### Post by Spades_Neil on 2008-11-07
**IT WORKED!!! :D**

I can only offer one 'thanks' thing, but this is worth at least a hundred. I have irreplaceable files back, and now I have the usability of my system without killing it.

> **soro2005 said:**
> You know how you changed it, but we don't. So it's difficult to have a guess at what's the problem, with that little information. Upon upgrading, the xserver (graphics server) has configured itself to meet the specs and methods of its new version, and my guess is that that has gone wrong, possibly because there was an old config file in the way. You could verify this by starting the computer from an Intrepid Live CD and see whether you have all the desktop effects, etc.

What graphics card do you have, anyway?



The step-by-step instructions are the same as above, really:
1. Start the computer from the harddrive, NOT from the live CD.
3. At the login window, flickering or not, hit, at the same time, ctrl+alt+F1. This key combination should get you to a black window with a login prompt ("terminal"). If it doesn't, try ctrl+alt+F2.
4. At the login prompt, log in with your username and password.
5. type ```
sudo dpkg-reconfigure xserver-xorg
``` Follow the instructions. Just accept the defaults by hitting <enter>.
6. Once all questions are asked and you're back at the command prompt, type ```
sudo reboot
```

If you're lucky, you have your graphics server back.

Funny thing is, I went to do this, and somehow my computer screen wasn't allowing the last line of text to appear. :\ I tried it a few times and then just tried typing blind. I got into the xserver-xorg thing, and then I *STILL* had no idea what to do! At that point, I just messed with it for a while, kept pressing buttons until something happened, gave up, and left.

Then I used sudo-reboot, restarted, and reached the login window and at first I noticed, "Hey, my mouse cursor isn't smushed... Wait, does that mean..?!" Surely enough, **"YES!! IT WORKS!!!!!!"** *squee of joy* XD

Thanks for the help though. When I get the chance, I'm going to update my Ubuntuforums profile and put on the signature section, *"When in doubt, keep pressing buttons until something happens!"*

---

### Post by Spades_Neil on 2008-11-07
Bump for glory, as the problem is solved. Hope someone else can find this info useful.

Feel free to post any alternative methods.

---

### Post by soro2005 on 2008-11-07
Oh, believe me, we've all been there with a broken X server! Actually, it got much easier lately.

For the future: You may want to familiarize yourself with the ways to use your linux system without a graphical interface. It is extremely reassuring to know that there's no danger to your data if the screen goes all weird. As for the thanks: Thanks for thanking, and whatever else you feel you owe, you can give back to the community by passing on your newly acquired knowledge. O:)

---

### Post by Spades_Neil on 2008-11-07
> **soro2005 said:**
> Oh, believe me, we've all been there with a broken X server! Actually, it got much easier lately.

For the future: You may want to familiarize yourself with the ways to use your linux system without a graphical interface. It is extremely reassuring to know that there's no danger to your data if the screen goes all weird. As for the thanks: Thanks for thanking, and whatever else you feel you owe, you can give back to the community by passing on your newly acquired knowledge. O:)

[CENTER][IMG]http://i37.tinypic.com/14bqkqw.jpg[/IMG]

Need I say more? XD Even got a sig for it now.[/CENTER]

---

