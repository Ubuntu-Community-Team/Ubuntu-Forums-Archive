---
title: "Spyware and Adware"
date: 2008-10-30
forum: General Help
---

### Post by Arukas on 2008-10-30
Just a little while ago, I a digital download of a game for about $4.00  Turns out it was a scam.  They didn't sell games.  I'm gonna call my back and file fraud and get a new credit card, but there's one thing.

I was ubuntu.  Now if that was Windows, I would be for sure I would of gotten spyware/malware/adware on my computer.  However, how do I check to see if I got anything like that on my computer.  I know linux is more secure than Windows.  

So is there a way to check or should I not worry?  I didn't install any programs or anything, so I think I am good.

---

### Post by melojo on 2008-10-30
> **Arukas said:**
> Just a little while ago, I a digital download of a game for about $4.00  Turns out it was a scam.  They didn't sell games.  I'm gonna call my back and file fraud and get a new credit card, but there's one thing.

I was ubuntu.  Now if that was Windows, I would be for sure I would of gotten spyware/malware/adware on my computer.  However, how do I check to see if I got anything like that on my computer.  I know linux is more secure than Windows.  

So is there a way to check or should I not worry?  I didn't install any programs or anything, so I think I am good.

I wouldn't worry about it.  I have been using linux for 10 years and have never had a virus/spyware/malware unlike windows.

---

### Post by Arukas on 2008-10-30
I'm really not worried.  But what makes me ask, is I don't even know how to check for stuff like that.

---

### Post by Herman on 2008-10-30
Try looking in your home/username directory and click 'View'--'Show Hidden Files', and then open your .mozilla directory and look in there. You'll find your firefox directory, and inside that there will be a directory with a unique name that looks like an md5 hash os something. Open that one and look for another directory called 'Cache'.
Your .mozilla/firefox/<uniquehash>/Cache directory is where temporary internet files are stored in Ubuntu.

One time I deliberately visited a virus site just to see what would happen, I was trying to help someone with a Windows computer that was infected with the virus and I was hoping to learn more about the virus.
The virus site left a file in my .mozilla/firefox/<uniquehash>/Cache directory but the virus wasn't able to run in Ubuntu. I presume that would be because it was a Windows virus and also because it didn't have permission, so all I needed to do was delete it.

You can install antivirus software in Ubuntu. but it's mainly for scanning Windows computers or files that we downloaded from the internet and that we might want to transfer to a Windows computer.
Ubuntu doesn't need any antivirus/antispyware for it's own sake.
I ran AVG antivirus for a while, here is the how-to I used to instal it,                                                                                          [[64-bit] Install AVG free and pro anti-virus for Ubuntu 64-bit]("http://ubuntuforums.org/showthread.php?t=622967&highlight=AVG") - Artificial Intelligence.
I think I had a 32 bit version with AVG as well, (in a different Ubuntu installation).
AVG antivirus worked well for me, it found the virus alright each time.

---

### Post by Bios Element on 2008-10-30
Simply put, Don't worry. Burn yourself a LiveCD if your that scared. Beyond that, You really have nothing to worry about. On the near impossible chance there is a virus, which is basically impossible to begin with, A LiveCD would have ya back up and running in an hour.

---

### Post by bryncoles on 2008-10-30
for reference, heres some info (you've probably already found) on security for ubuntu

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)
[http://ubuntuforums.org/showthread.php?t=671604](http://ubuntuforums.org/showthread.php?t=671604)
[http://ubuntuforums.org/showthread.php?t=823741](http://ubuntuforums.org/showthread.php?t=823741)

---

