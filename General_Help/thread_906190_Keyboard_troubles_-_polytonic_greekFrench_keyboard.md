---
title: "Keyboard troubles - polytonic greek/French keyboard"
date: 2008-08-31
forum: General Help
---

### Post by dinofelis on 2008-08-31
Hello,

I'm having the following problem.  I use 8.04 and the Gnome desktop.

For different reasons, I need to have 3 different keyboards active on my system: US international keyboard (I'm the user), and the standard French keyboard and also the Greek polytonic keyboard (my wife uses both).

Now, I applied the tricks on [http://simos.info/blog/archives/639](http://simos.info/blog/archives/639)
and lo and behold, Greek polytonic works now.  However, what doesn't work anymore, is the circumflex accent in the French keyboard.  The rest of the French keyboard is ok, but the composed characters with the circumflex accent don't work anymore.

Now, the funny thing is that if I use SCIM input method (available in gedit - I don't know how to activate it in Writer) then the French circumflex works, but this time the Greek polytonic doesn't work anymore...
In any case, I don't know how to activate SCIM in Writer (in gedit, a right mouse click lets you choose...).  

If I understand well, in 8.10, this will be somehow fixed ?

---

### Post by simosx on 2008-08-31
Why does circumflex stop working when you enable Greek Polytonic, following the instructions at [http://simos.info/blog/archives/639](http://simos.info/blog/archives/639) ?

On a Linux system there are several files with Compose sequences, such as
/usr/share/X11/locale/en_US.UTF-8/Compose
/usr/share/X11/locale/el_GR.UTF-8/Compose

If your system locale is el_GR.UTF-8, then the system uses the second line.
Actually, there are only a handful of these Compose files because most locales simply reuse the "en_US.UTF-8" file.

The quick n dirty way to get Greek Polytonic to work is to replace the en_US.UTF-8/Compose file with the Greek version. The Greek version has the full instructions for Polytonic and covers most of the standard latin sequences.

The problem with circumflex is that the Greek Polytonic Compose file is not fully updated and does not include the sequences for circumflex.

So, what do you do? You can try by merging together the two Compose files.
I have not tried this, so if you can test it and report back, it would be really great.

1. We are going to make a custom Compose file, ~/.XCompose
This file overrides the system files. If you have several Linux accounts, you would need to copy this to each one of them.

2. Copy the en_US.UTF-8/Compose compose file to ~/.XCompose,

cp /usr/share/X11/locale/en_US.UTF-8/Compose.ORIGINAL ~/.XCompose

3. Dump on top of that file the Greek compose sequences,

cat  /usr/share/X11/locale/el_GR.UTF-8/Compose  >  ~/.XCompose

4. You may have to logout to have these settings activated.
As long as the variant GTK_IM_MODULE is set to "xim", all these should work.

There is some effort to get Greek Polytonic to work out of the box. The main issue for this is that there are three different packages (gtk+, Xorg, xkeyboard-config) that have to be in sync. I do not know which versions Ubuntu 8.10 is going to take and I am trying out these now.

---

### Post by dinofelis on 2008-09-01
Thanks!  I will try that out as soon as I find some "playing time" - probably this evening (I'm in France), so + 10 hours from this post's time stamp on.

---

### Post by dinofelis on 2008-09-01
BRILLIANT.  It works!

Just a small correction, it is of course:

cat .... >> ~/.XCompose 

and not cat ... > ~/.XCompose which simply overwrites it.

---

### Post by simosx on 2008-09-01
> **dinofelis said:**
> BRILLIANT.  It works!

Just a small correction, it is of course:

cat .... >> ~/.XCompose 

and not cat ... > ~/.XCompose which simply overwrites it.

Thanks for the feedback. I will update my post with these instructions.

---

