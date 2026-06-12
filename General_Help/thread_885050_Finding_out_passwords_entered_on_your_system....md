---
title: "Finding out passwords entered on your system..."
date: 2008-08-09
forum: General Help
---

### Post by iamBevan on 2008-08-09
Just wondering if there is a way to find out used usernames and passwords on your system, or any type of key-logging software thats available?

---

### Post by spiderbatdad on 2008-08-09
[http://www.honeynet.org/](http://www.honeynet.org/)

but basically, no...I think is the answer you're looking for. Assuming you have no froward facing applications running. Usernames are accessible locally, but passwords are encrypted. So long as the passwords are strong...they are *relatively* uncrackable.

If security is your concern, it is a never ending learning curve, and no solution is available...it's a process.

---

### Post by tamoneya on 2008-08-09
Im pretty sure that discussion of keyloggers and any other spyware is not allowed in the ubuntu forums according to the code of conduct.

---

### Post by iamBevan on 2008-08-09
I am entirely within my rights to monitor what my employees do on my system.

---

### Post by Steveway on 2008-08-09
> **iamBevan said:**
> I am entirely within my rights to monitor what my employees do on my system.

Go ahead and do what you want. But you won't get help for this sort of thing here.

---

### Post by spiderbatdad on 2008-08-09
> **tamoneya said:**
> Im pretty sure that discussion of keyloggers and any other spyware is not allowed in the ubuntu forums according to the code of conduct.

What code of conduct is that? Key logging is a very useful tool, when used properly. It can reveal what attempts system crackers use to intrude into server applications.

---

### Post by tamoneya on 2008-08-09
> **iamBevan said:**
> I am entirely within my rights to monitor what my employees do on my system.

i never said you werent.  I just said it isnt to be discussed here.

---

### Post by iamBevan on 2008-08-09
You've assumed I'm using it for a pathetic reason basically, just like all the people in the other threads I have read, but that's fine.

Anyway, I have found and installed lkl - but am unsure of how to use it - If anyone could point me in the direction of a new-user-friendly howto, then that would be greatly appreciated.

---

### Post by spiderbatdad on 2008-08-09
lkl is a userspace keylogger. Any system admin could find out what activity is taking place on a computer through system logs. lkl is not likely to report accurately. It is true you should not be trying to capture passwords from employees. 
If that is your desire. Then assign passwords and accounts properly. That way everyone knows up front that this is your system and you monitor everything.

---

### Post by p_quarles on 2008-08-09
For the record, there is nothing disallowing discussion of keyloggers here, but anyone asking about them should expect to be asked and to explain their intentions. If you think it's "none of anyone's business" why you use them, you are in the wrong forum, and should go elsewhere. These are sensitive issues, and people helping have every reason to be concerned that such tools are used for legitimate purposes.

That said, the staff would appreciate it if people (I'm looking at you, tamoneya) would allow us to do the work of moderating threads. To alert us to a thread we haven't seemed to notice, please use the "report" button. Don't attempt to moderate yourself. That actually *is* in the Code of Conduct you signed, while there is nothing there regarding security software.

---

### Post by p_quarles on 2008-08-09
> **spiderbatdad said:**
> lkl is a userspace keylogger. Any system admin could find out what activity is taking place on a computer through system logs. lkl is not likely to report accurately. It is true you should not be trying to capture passwords from employees. 
If that is your desire. Then assign passwords and accounts properly. That way everyone knows up front that this is your system and you monitor everything.
This is the best advice so far. A properly configured system will not need a keylogger to retain control over user accounts.

---

### Post by mb_webguy on 2008-08-09
> I am entirely within my rights to monitor what my employees do on my system.Truuuueee.... but...  Logging what your employees are doing is one thing, but logging their keystrokes is something else entirely.  Knowing that they're accessing personal email accounts on company time is fine, but recording their usernames and passwords for those accounts?   I'm not very knowledgeable about privacy laws in the UK, but I'd imagine that might be somewhat questionable.

Besides, keystroke loggers are of limited use in a graphical user environment.  You might be able to get usernames and passwords and such, but won't necessarily be able to determine what applications or websites that information is being used for if the user got there through mouse clicks.

Considering that Linux is pretty secure when it comes to installing and running applications, I'm assuming you're concerned about Internet activity.  And when it comes to Internet security, prevention is the best remedy.  You could set up a system proxy to block undesirable websites (or conversely only allow desirable websites).

What exactly are you concerned that your employees are doing?  Perhaps we could help you come up with a better alternative than a keystroke logger.

---

### Post by sub2007 on 2008-08-09
Using a keylogger on your own personal computer is not illegal provided that anyone who is using the computer is aware that all their keystrokes are being logged and what you would do with that information. It is definitely illegal to plant one on someones computer without their knowledge or consent. 

There are serious ethical issues involved with using a keylogger, especially if you are using it to spy on people without their consent. Yes they are your employees but they are entitled to some basic privacy and stealing their personal usernames and passwords without them being aware of it would be too much of an invasion of privacy.

---

### Post by lisati on 2008-08-09
I concur with the already expressed views that you need to take a good look at why you might want to monitor a user's activity. Troubleshooting problems, protecting yourself and others from potentially harmful stuff, and accounting for computer use in a business environment are examples of a good use of such tools. Just being nosy is questionable.

---

### Post by tamoneya on 2008-08-09
> **p_quarles said:**
> For the record, there is nothing disallowing discussion of keyloggers here, but anyone asking about them should expect to be asked and to explain their intentions. If you think it's "none of anyone's business" why you use them, you are in the wrong forum, and should go elsewhere. These are sensitive issues, and people helping have every reason to be concerned that such tools are used for legitimate purposes.

That said, the staff would appreciate it if people (I'm looking at you, tamoneya) would allow us to do the work of moderating threads. To alert us to a thread we haven't seemed to notice, please use the "report" button. Don't attempt to moderate yourself. That actually *is* in the Code of Conduct you signed, while there is nothing there regarding security software.

Point taken.  Sorry iamBevan
I never intended to moderate and intentionally left my initial reply open to a correction:> Im pretty sure ... Sorry if things were taken the wrong way.

---

