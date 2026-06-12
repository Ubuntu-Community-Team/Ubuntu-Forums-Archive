---
title: "Installing Stata 10 with the Windows license"
date: 2008-07-25
forum: General Help
---

### Post by Reisen 2 on 2008-07-25
This is kind of a shot-in-the dark question, I hope I'm in the right forum.

I've been considering switching back to Ubuntu, but I have an absolutely-must-run-daily program, Stata 10.  The program CD comes with all the versions on it: Windows, Linux, etc..  However, the license I bought is for the Windows version (it says so specifically on the license paperwork).  

Does anybody know if Stata will install and be usable without having to buy another license key for the Linux version?

I'd try it out myself, but it'd be a big hassle to go through installing Ubuntu just to find out I can't use it, then uninstalling it.

Thanks

---

### Post by SOULRiDER on 2008-07-25
If youre talking about
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=7684](http://appdb.winehq.org/objectManager.php?sClass=application&iId=7684)

It seems like it does.

---

### Post by Reisen 2 on 2008-07-25
Nope, different program.  Although it looks like Stata is actually in the wine appdb ([http://appdb.winehq.org/objectManager.php?sClass=version&iId=12690&iTestingId=27492](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12690&iTestingId=27492))!  Could have sworn it wasn't there an hour ago... I must have had a typo.

Thanks!

---

### Post by gaussian on 2008-07-26
> **Reisen 2 said:**
> This is kind of a shot-in-the dark question, I hope I'm in the right forum.

I've been considering switching back to Ubuntu, but I have an absolutely-must-run-daily program, Stata 10.  The program CD comes with all the versions on it: Windows, Linux, etc..  However, the license I bought is for the Windows version (it says so specifically on the license paperwork).  

Does anybody know if Stata will install and be usable without having to buy another license key for the Linux version?

I'd try it out myself, but it'd be a big hassle to go through installing Ubuntu just to find out I can't use it, then uninstalling it.

Thanks

Not probably the answer you were looking for, but might be relevant information: I converted my Windows Stata license to Linux about four years ago. Stata was really reasonable about it, they charged something really nominal ($50 if I remember correctly, compared to several hundreds for single user new license). Linux version of Stata has all the features AFAIK as Windows version.

---

### Post by Reisen 2 on 2008-07-26
Thanks!  I'll probably go that way about it since it's fairly reasonable.  Nothing wrong with having totally legit software.

---

### Post by chamb244 on 2009-05-19
For what it's worth, I use Stata 10 under wine and it mostly runs fine. The major issues I have are with graphical rendering.  Still, it is nice to be able to run Stata without having to reboot into windows.

---

### Post by motorhead_1 on 2009-11-11
> **chamb244 said:**
> For what it's worth, I use Stata 10 under wine and it mostly runs fine. The major issues I have are with graphical rendering.  Still, it is nice to be able to run Stata without having to reboot into windows.
have you had issues with the [FONT=monospace]file [/FONT]isstata.100 ? I need this file in order to run stata after the wine installation. the problem is reported [here]("http://appdb.winehq.org/objectManager.php?bShowAll=true&bIsQueue=false&bIsRejected=false&sClass=version&sTitle=&sReturnTo=&iId=12690").
could someone send me this file please?

---

