---
title: "Firefox done went nuts!"
date: 2008-08-28
forum: General Help
---

### Post by lsutiger on 2008-08-28
I am having a very very strange problem with firefox.

There is one site that I am visiting (hotair.com) where all I am getting is links and text, though the site is content rich (running 7.10 - FF2). Thought it might be a cache problem, so I deleted it. Didn't fix it. So I remote into my machine at work and start up firefox. No problem (8.04 FF3).
Then when I click on an html link from a file on my hard drive on my 7.10 computer, it opens in FF3 (which I have on the hard drive, but not active - I did not d/l from the repositories, I manually installed to try it). I also tried deleting the profile in order to create a new one. But what I get in response it that "Firefox is currently" running or something to that effet. I pull up the system monitor and it is not to be found!!!!!!!!!

What could be causing such a problem? I uninstalled FF2 and reinstalled and deleted the FF3 directory, to no avail!

Help me stop ](*,) !!!

---

### Post by Crafty Kisses on 2008-08-28
Have you checked your FirFox error logs, if not can you post them?

---

### Post by lsutiger on 2008-08-28
This is what is in the error console:
Error: uncaught exception: Permission denied to call method Location.toString

What does that mean?

Thanx for the response!

---

### Post by Crafty Kisses on 2008-08-28
This definitely sounds like some sort of Java issue. Perhaps it's in one of the external JavaScript files, or it also could be Cross-domain scripting for some reason, that's the only thing that comes to mind. Have you tried removing and reinstalling all the Java packages and dependicies?

---

### Post by lsutiger on 2008-08-28
No I have not...could you give me some instruction on how to uninstall java?

---

### Post by lsutiger on 2008-08-29
Well, I uninstalled the sun-java packages then reinstalled, but it did not fix the problem.
I used  Synaptic to uninstall. It only uninstalled 2 total packages...what other files should I have marked for deletion?
Also same effect in Opera and IE6 in wine

---

### Post by lsutiger on 2008-08-29
Anybody? This is driving me up a wall!

---

### Post by Crafty Kisses on 2008-08-29
Try reinstalling those packages, see what happens.

---

### Post by lsutiger on 2008-08-29
I already have

---

### Post by Ms_Angel_D on 2008-08-29
Did you do an uninstall or complete removal? If not try the complete removal then re-install.

---

### Post by lsutiger on 2008-08-30
complete removal

---

### Post by lsutiger on 2008-08-30
anybody??

---

### Post by lsutiger on 2008-09-06
OK new info here.
We had that hurricane come through a week back or so ago. Of the power went out. I also had a generator, so I was able hook up through cat5 cable to my cable modem.

All of a sudden I could load the site hotair.com correctly. After I got the power back up, I pulled the ethernet cable from the modem, logged on wireless.

Now the problem has arisen again. When I go to the site hotair.com, none of the styles load and I get a basic html page. There is another site on the same server [http://michellemalkin.com/](http://michellemalkin.com/), that the same thing happens.

What could be causing this?

---

