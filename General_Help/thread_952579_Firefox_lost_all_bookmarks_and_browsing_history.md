---
title: "Firefox lost all bookmarks and browsing history"
date: 2008-10-19
forum: General Help
---

### Post by bjornolai on 2008-10-19
Hi

I dont' know exactly how it happended but suddenly some weeks ago Firefox 3 would not show any of my bookmarks or browsing history. Furthermore I could not save new bookmarks or navigate pages using back or forward buttons. I was thus forced to use other browsers for a while. However, I decided to tackle the problem, and found a solution which I taught might be of interest to some other users.  

First of all I knew my profile hadn't been deleted (/home/myusername/.mozilla/firefox/ko2hizp5.default/). However, I found that the ownership had been changed to root. This command changes the ownership of all files to your user:

```
sudo chown -R yourusername.yourusername .mozilla/firefox
```
 
After running this command firefox is back to normal.

_Note:_
I do not know whether some of the files in .mozilla should be owned by root. So as always do this at your own risk. If anyone can see a possible security risk please add a post.

---

### Post by shawnrgr on 2008-10-19
I always was under the impression that ANYTHING under ~/ was owned by the user, not root. How it changed is beyond me, but chowning it back to your user shouldn't cause any problems, your running firefox as your user anyway

---

### Post by Mr_JMM on 2008-10-19
Can't help with history but for future reference I recommend an add-on called "Foxmarks". It stores all your bookmarks on a server. Your bookmarks can follow you whichever PC you're on.

[https://addons.mozilla.org/en-US/firefox/addon/2410]("https://addons.mozilla.org/en-US/firefox/addon/2410")

---

### Post by bbjeg on 2009-01-16
Thanks bjornolai. I was starting to freak out a bit.[-o<

---

### Post by sdb2028 on 2009-01-18
Good work bjornolai! I've been chasing this problem all weekend, even did a complete remopval and reinstall of firefox (several times) with no luck. I finally found your thread, entered the code, and it worked. I now have my firefox back. Many thanks to your genius.

---

### Post by danduq on 2009-03-04
Erk! Not sure what happened, but I managed to rootify a few files in my ff directory today too.

God knows how long it would have taken to find out that simple problem without this thread!

:D

---

### Post by aklilom on 2009-04-03
Thanks a lot. This saved me a lot of time. 

Can you give me some ideas on how I can avoid falling into this error now and then. This firefox error has happened to me for the third time now.

Aklilom,

---

### Post by syga on 2009-04-05
THANKS!!!

I lost my bookmarks also. Got them back with your help...



> **bjornolai said:**
> Hi

I dont' know exactly how it happended but suddenly some weeks ago Firefox 3 would not show any of my bookmarks or browsing history. Furthermore I could not save new bookmarks or navigate pages using back or forward buttons. I was thus forced to use other browsers for a while. However, I decided to tackle the problem, and found a solution which I taught might be of interest to some other users.  

First of all I knew my profile hadn't been deleted (/home/myusername/.mozilla/firefox/ko2hizp5.default/). However, I found that the ownership had been changed to root. This command changes the ownership of all files to your user:

```
sudo chown -R yourusername.yourusername .mozilla/firefox
```
 
After running this command firefox is back to normal.

_Note:_
I do not know whether some of the files in .mozilla should be owned by root. So as always do this at your own risk. If anyone can see a possible security risk please add a post.

---

### Post by fabiops on 2009-10-12
Thank you very much, [bjornolai ]("http://ubuntuforums.org/member.php?u=105944")! Exactly the same thing just happened here, but I got it solved with your tip. Really strange why the owner change happened...
Anyway, thankyou again!

---

### Post by unicahija on 2010-03-23
Hi all,

Where will I put the code/command?  Please assist step by step.  I am not a technical person.
Thank you so much.

---

### Post by mkvnmtr on 2010-03-23
Sounds like you might have had a power outage. I had one today and sometimes they can cause strange problems. You might wish to copy your .mozilla file somewhere safe and just replace it if there is a problem. I have moved mine from done distro to another a few times.

---

