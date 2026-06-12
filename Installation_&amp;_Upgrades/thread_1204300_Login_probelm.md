---
title: "Login probelm"
date: 2009-07-04
forum: Installation &amp; Upgrades
---

### Post by star_teck on 2009-07-04
This is my first post here so if I make a mess of it please be understanding.  I have had a quick look at the forum and didn't see anything similar to my problem.
 
I am operating Ubuntu as the first operating system along with XP home edition.
 
Today I upgraded to 9.04 and every thing has gone smoothly untill the reboot.  It asked for a Username and pass word.  Out with the trusty note book and I put in the username/pass I chose for the last upgrade a couple of weeks ago.
 
I used a username with all caps and a pass all lowercase I've tried just about every combination of upper and lower case and I'm still locked out.
 
Is there a back door I can use to get in and manage the accounts?
 
Star Teck
aka 
Noel

---

### Post by merlinus on 2009-07-04
Can you select recovery mode at the grub menu?  If not, when you get to the user/password screen, try pressing Alt+Ctrl+F2, which will hopefully get you to a CLI.

Then enter 

```
passwd username
```

and put in a new password.

---

### Post by star_teck on 2009-07-04
Thanks Merlin I'll give it a try
 
Noel

---

### Post by star_teck on 2009-07-04
No Joy!
 
I tried the recovery mode nothing in there to manage pass words.
 
Then I tried the Cntl > Alt > F2 and got a cursor with the Words...
Work - Living Room> Username:
 
What I really need is a back door or root username and pass
 
Noel

---

### Post by merlinus on 2009-07-04
There is nothing there to manage passwords.  What you want is a CLI (command line interface) where you can type the command I gave, same as though it was in a terminal window.

From recovery mode, once it finishes loading, you should be able to drop into a root shell prompt.

---

### Post by star_teck on 2009-07-04
Merlin what can I say...  When it comes to Linux I'm a newbie spelled with all caps 

Nuff' of that

I found the CLI and of course put in the command > passwd username

Then, when it replied unknown username, I figured out it was supposed to be my user name (said I was green to this)  I then tried all the user names I had in my book until I struck pay dirt!

I'm making this reply on the Ubuntu OS so as you can see it's working properly.

Many thanks

I have marked the subject line solved.  I hope this is the way to close a successful thread

star_teck
aka
Noel

---

### Post by merlinus on 2009-07-04
Glad you got it working.  Often the best way to learn is to try, and try again.  No mistakes, only learning opportunities.

Have fun!

---

