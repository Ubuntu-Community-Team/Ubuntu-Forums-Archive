---
title: "Password Manager (Solved)"
date: 2005-11-24
forum: General Help
---

### Post by Roman27 on 2005-11-24
I'm trying to switch from Windows to Ubuntu.  In the process, I have to change many of my former applications to ones that work in Ubuntu.  In Windows, I use [Password Agent]("http://www.moonsoftware.com/pwagent.asp").  It has many handy features, like the ability to create categories, password expiration warnings, ability to add additional notes to each entry, etc.

I'm having a hard time finding something to replace it in Ubuntu.  I did a search for "Password Manager" in Synaptic and found 4 different ones in the repository.  I installed 3 of them, but only one added a link in the menu.  The other two, I started from the terminal, but they look like junk.  The only one worth anything was [Revelation]("http://oss.codepoet.no/revelation/about/").  Unfortunately, it doesn't support any of the features I mentioned about Password Agent above.  :( 

I searched via Google and found one that really interested me called [GPass]("http://projects.netlab.jp/gpass/en/").  On the download page, it says that someone made a Debian package for it.  But when I click on the link, it take me [here]("http://packages.debian.org/unstable/gnome/gpass").  What am I supposed to do now?  :( 

**EDIT:**
OH MAN!  You gotta be kidding me...  I just did a search for GPass in Synaptic and *POOF* it's there!  Why didn't it come up on my original search for "Password Manager"?  Grrrr...  :x

Ok, well...  I'm gonna post this thread anyway in case someone does a search for password manager on the forums.  GPass looks to be the best to me.  It just stinks that I didn't search for it specifically earlier.  	](*,)

---

### Post by VicVega on 2005-11-24
Thanks Roman27,

I also use Password Agent and have been looking for a linux equivalent. I will try Gpass. 

Cheers,
Vic

---

### Post by Roman27 on 2005-11-25
By the way, these were the other Password Managers that I took a look at:

These are listed in Synaptic:
[LIST]
[*][Revelation]("http://oss.codepoet.no/revelation/about/") - I mentioned this above in my first post.  It's nice looking, is included in Synaptic, but doesn't have category functionality, an area for notes, or the ability to set an expiration date.
[*][FPM]("http://fpm.sourceforge.net/") or Figaro's Password Manager - It looks ugly, in my opinion ([screenshot]("http://freshmeat.net/screenshots/2651/2651/")).  But it is included in Synaptic and has category ability.  I'm not sure whether it has an area for notes or some of the other features I'm looking for.
[*][MyPasswordSafe]("http://www.semanticgap.com/myps/") - Looks decent and is included in Synaptic.  The downside to this one is that it doesn't generate passwords with special characters (IIRC), and doesn't support expiration dates.  It's a bit too simple for me and hasn't been worked on since February 4th, 2004.
[*][ZSafe]("http://z-soft.z-portal.info/zsafe/") - It's included in Synaptic.  It's a port of a PDA password manager.  No category feature and looks ugly.
[/LIST]

Not included in Synaptic:
[LIST]
[*][GPassman]("http://gpasman.sourceforge.net/") - It looks ugly and simplistic.
[*][Password Manager]("http://www.geocities.com/ramix_info/passwordmanager.html") - It which works on nearly all OSes, which is nice.  The downside is that it doesn't have a nice tree-view category display, and it isn't in Synaptic.
[*][PwManager]("http://passwordmanager.sourceforge.net") - This one looks great.  The downside is that it looks like it's more for KDE and it also isn't in Synaptic.
[*][Password Gorilla]("http://www.fpx.de/fp/Software/Gorilla/") - It doesn't look that great either and isn't in Synaptic.  But, it does support categories.
[/LIST]

That's about all I could find.  Unfortunately nothing with the feature set matching Password Agent yet.  :(

---

### Post by tim15856 on 2005-11-25
Some of those look good however, I needed a password manager that could use the same data file in both WindowsXP and Linux. I've been using Password Safe in XP for awhile. MyPasswordsafe is the Linux equivalent. Even though it's old, it still works fine with my Password Safe 2.0 data file.

---

### Post by djlosch on 2005-11-25
hehe... never needed a pword manager.  i find this scheme works to make up a password that is easy to remember, and is unique for every single service.

1) pick a totally made up word. and double one of the letters in it.  lets take *fajoo* for example.  you need a double letter in the word to eliminate keyboard printing (see the movie national treasure)
2) pick a 2 digit number. lets use *44* for instance.
3) look at the name of the service.  we'll use *ubuntu forums* for instance.  shorten this based on syllables, making *ubtfr*
4) pick your favorite symbol.  dont use common delimiters and shifts (like: ' " / space \) as they bork some stuff up.  we're gonna use the underscore.
5) concatenate these together: *fajoo44ubtfr_* (you can do it in a diff order if you want, but often a alphachar has to be first)

when u start using this kind of scheme for multiple services, u remember the method REALLY fast, and you get a pretty strong pword that's not hard to remember.

---

