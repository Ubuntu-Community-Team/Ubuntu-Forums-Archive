---
title: "Go From 9.04 to 9.10?  Total Disaster!"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by oldefoxx on 2009-11-04
I spent all evening trying to go from Ubuntu 9.04 to the new 9.10, and it was a total disaster.  First, I tried it with the Upgrade Manager that told me I could upgrade just by clicking, so I tried it.  It looked okay to start, but I wanted to change the background.  Immediately it told me I did not have the complete language package (I assume English), and offer to get it for me.  It got my password, but then it froze.  I had to power off my PC.  Trying to boot up, it went through the same process again.  It made a bit more gain, but froze up again.  Oh, and it did tell me that some of my folders were misnamed.  Seemed that it wanted my /home/user/Desktop to become /home/user/Download, but I already had a subfolder named Download.  So I said to keep the old names.  That didn't work.  Then next time I told it to rename them, and it hung up just as bad.

I'd already burnt some CDs with the ISO, so I decided to try installing that way.  Strange, instead of colored progress bar and symbol, it was like looking and an old black and white episode of an interrogation room in the near dark with one overhead light.  Almost ghostly, not attractive at all.  And the boot process from CD took at least 6 times longer than when I booted up 9.04 from the CD.  That's progress?  Anyway, again the whole issue of wanting to rename folders, but nothing about missing parts of the language package.  So I am finally looking at the desktop.  But then I want to go to Computer under Places, and everything locks up again.  That is definately not good.

Oh yes, I selected manual mode with the partitioner and did not want to reformat my / drive.  Reason?  I still hoped to find my prior work on the drive after the install.  Anybody that changes folder and subfolder names or locations of key files should be blindfolded and forced off a diving ramp from the top of a tall ship.  And yes, it first removed 27 so-called obsolete packages, than another 83 towards the end of the install, while installing 307 new ones.  I have no idea what was lost in the process.

The recovery modes in the boot process did no good.  Not even sure how to start up Gnome after you try to get it to repair packages.  Had to enter sudo shutdown -r now and just have it reboot.  I doubt that did any good anyway.  Even trying to revert to an earlier kernel release proved to no avail, as the new install of 9.10 had changed too much, and I would just end up with a bare white screen, nothing else.  So you screw around with the settings that took so long to get right?  What are you people, Democrats?  You don't get my vote.

Now I am going to try a reinstall of 9.04 and just hope tht somehow it will get back on course, and that by not reformating the / drive I will be able to recover what my user had there.  I could have done a backup first, but after four versions of Ubuntu, I though I could trust your work, and the lavish praise I read in three articles (with Windows 7 and Ubuntu 9.10 pretty much in a tie with each other), made me overconfident.  Now I know better, not that it helps much.

Real bummer.  I hope this helps others from being too rash in their efforts to move forward.  At worse, I guess a reformat of the root (/) partition will let it install, but it is definately not an upgrade for 9.04.  That means starting over.

---

### Post by Roasted on 2009-11-04
For one, it's always advisable to do a fresh installation of Ubuntu. Doing updates in Ubuntu is just as risky as it is in Windows. I wouldn't even consider it in Windows, at the same token, I wouldn't even consider it in Ubuntu. 

Secondly, Ubuntu gets released on 6 month intervals. That's wicked fast for developers. I too had problems with Karmic. But don't be blinded to assume that Karmic is the only version of Ubuntu out there. For insane stability, try the current LTS release - 8.04.3. Otherwise, stick with 9.04.

We as Ubuntu users are very blessed, and most people don't even realize it. We get new releases every six months, and each release is stabilized with patches and updates just WEEKS after their release. Our system32 colleagues are stuck waiting 3-5 years for a new version and even at that, it often takes a good 12-18 months for that new release to stabilize.

In short:

Stick with 9.04.
Don't do upgrades.
Check 9.10 in a month.

---

### Post by oldefoxx on 2009-11-08
Oh, I quite agree with you, particularly about how quickly the committee moves forward to bring fixes and upgrades to Ubuntu, and how laggadly and inattentive that Microsoft has shown itself to products already sold and expected to be replaced eventually by new versions.

I mean, all that is very apparent.  All I was tryng to do is capitalize on my own mistakes and oversights to make others aware of how vulnerable they might be or might become if they take no precautions beforehand.

---

