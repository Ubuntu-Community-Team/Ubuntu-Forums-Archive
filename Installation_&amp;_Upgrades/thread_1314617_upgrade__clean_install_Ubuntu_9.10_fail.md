---
title: "upgrade / clean install Ubuntu 9.10 fail"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by cooper.z on 2009-11-04
Hi guys,

My PC was running Ubuntu 9.04 quite happy. 

After I upgrade to 9.10 and reboot, I only can see a dark white ubuntu logo in the middle of the screen. Then, nothing happen.

After that, I tried to do a clean installation. I got a black screen after I choose "install ubuntu".

I have googled a lot. It seems like many people are struggled on the new version.

Can anyone help me, please? I can not even get into my old ubuntu (9.04).

Thanks in advance.

---

### Post by jjcv on 2009-11-04
Did you boot of the 9.10 live CD and get a live working desktop?

Really needs some more details to be able to help.

---

### Post by cooper.z on 2009-11-04
> **jjcv said:**
> Did you boot of the 9.10 live CD and get a live working desktop?


I booted from 9.10 live CD to install 9.10. But I even can not get the live ubuntu work. I got a black screen after I chose "run ubuntu without changing your system".

Thanks

---

### Post by mathspeedy on 2009-11-04
That's why I always wait 2-3 weeks before upgrading.;)

---

### Post by grumpyoldgit on 2009-11-04
I came across Ubuntu a few days before 9.10 was released. While I was using 9.04 for those few days I had no real problems.
My mistake seems to have been to upgrade. I have faffed about with 9.10 for a few days now but just cannot get it stable.
A soft reboot is normally OK but a hard reboot is similar to that described above.
I get the white circle, a blinking cursor in the top left side of the screen and then just a black screen.
The only way out seems to be to keep pressing the esc key on boot up.
I briefly see a message about not being able to mountall followed by a message that it is going to reboot.
As this is a soft reboot it generally is then O.K. ....... for a while.
The system tends to freeze when it feels like it at irregular intervals, sometimes a few minutes, sometimes hours.
I then have to repeat the hard boot soft boot routine before the system is up and running again.
My family are not impressed with a PC that now runs a lot faster than under XP but which requires frequent interventions by myself to keep it running.
I have scrubbed the disk completely and done a clean install with Ubuntu taking up the whole disk but the situation has not improved.
I would like to see all the messages but have not been able to work that out yet.

---

### Post by mathspeedy on 2009-11-04
Grumpyoldgit, What GRUB version you have; GRUB Legacy or GRUB 2 ?
It's maybe the reason of the drives loading problem...:?

---

### Post by cooper.z on 2009-11-04
> **mathspeedy said:**
> What GRUB version you have; GRUB Legacy or GRUB 2 ?
It's maybe the reason of the drives loading problem...:?

I think it is GRUB2 since I upgrade to 9.10. 
I was pretty keen on ubuntu. But now, It push me to go for fedora. Fedora 12 is coming in 13 days...

---

### Post by jjcv on 2009-11-05
> **cooper.z said:**
> I booted from 9.10 live CD to install 9.10. But I even can not get the live ubuntu work. I got a black screen after I chose "run ubuntu without changing your system".

That would be a good reason not to install that version of Ubuntu.  If the live CD does not work then the chances that it will install and work are slim.

It does sound like a grub problem to me but without more detail I cannot tell.   If you upgraded then the old grub would have remained.  If you do a new install then grub 2 would have been installed.

You may have to go back to 9.04 until these issues have been sorted out.

---

### Post by mathspeedy on 2009-11-05
> **cooper.z said:**
> I think it is GRUB2 since I upgrade to 9.10. 
I was pretty keen on ubuntu. But now, It push me to go for fedora. Fedora 12 is coming in 13 days...

Sorry, This was the question for grumpyoldgit.
--
Like JJCV said if I were you I'll just stick to the 9.04 version for now(2-3 weeks at least) and verify if someone have found problems, a way to fix thoses ...;).         
Just like me, because last time I lost everything. :mad:

---

### Post by cooper.z on 2009-11-05
> **mathspeedy said:**
> Sorry, This was the question for grumpyoldgit.
--
Like JJCV said if I were you I'll just stick to the 9.04 version for now(2-3 weeks at least) and verify if someone have found problems, a way to fix thoses ...;).         
Just like me, because last time I lost everything. :mad:

I should read your suggestion before upgrade :( 
I wont sacrifice myself...

---

