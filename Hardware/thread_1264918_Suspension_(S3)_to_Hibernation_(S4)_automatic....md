---
title: "Suspension (S3) to Hibernation (S4) automatic..."
date: 2009-09-12
forum: Hardware
---

### Post by ^_Pepe_^ on 2009-09-12
Hi all!

I have now my new Dell E4200, and I'm very happy with it. Currently is working with W'Vista, but it will be Ubunted soon. I have read that almost everything is working properly. 

But my question is: With Vista, when I close the lid, system goes to Suspension (S3 state) quick to resume, and reasonable to battery drain. Very useful for check mail, wiki, open, close, open close. But, if I "forget" the laptop, after some time (declared in energy policies), system goes to Hibernation (s4) automatically. 

It's fantastic to me. Any idea to do this in Ubuntu?

Is it a good idea for the sandbox (new ideas for new versions)?

Thanks
Pepe

---

### Post by ^_Pepe_^ on 2009-10-05
Hi!

Let me put a bump here!

I've been thinking about including a script to be automatically ran. Can anybody help me?

Basically this script should do following:

1. Calculate a particular amount of time (suppose 2 hour), but it have to do it during suspension.
2. After this time, wake up the computer
3. Hibernate it.

And if suspension is broken by lid or button, restart the timer.

Will it be difficult? To me, now is Sci-Fi... :-/ :confused:

Thanks for any help!

---

### Post by ^_Pepe_^ on 2009-10-15
Hi again.

Last bump, I swear.

Does anybody know if is there a space where I can hire professional services to a Linux programmer for a reasonably price. 

I think I could pay for this functionality.

Thanks!

---

### Post by bohemier on 2010-04-24
Hello Pepe,

How did you end up with this issue? I am looking for the same thing. Creating a script would probably do it but I am sure it was done before... Anyone has a hint?

Thanks

---

### Post by ^_Pepe_^ on 2010-04-26
Not really.
:confused:

When I was working with W' Vista, starting up was a mess so I used suspend (closing the lid) and hibernate a lot; but, to be honest, with 9.10 and 10.04, my computer starts in less than 20 sec, and shuts down in less than 5.

I finally forget the topic. But, if you reach a solution, please post. I don't like to give up!!

:)

Regards

> **bohemier said:**
> Hello Pepe,

How did you end up with this issue? I am looking for the same thing. Creating a script would probably do it but I am sure it was done before... Anyone has a hint?

Thanks

---

### Post by bohemier on 2010-04-27
Allright, thanks for the followup. I'll post my findings here. Cheers!

---

### Post by ^_Pepe_^ on 2012-11-03
Hi all, 

Let me bump an old post here. 

I'm trying to automate suspension to hibernation again, now from my new thinkpad X200. 

Hibernation works fine, from menu.

I have found this script, [http://askubuntu.com/a/33192/60629](http://askubuntu.com/a/33192/60629), and this is how behaves:

1. Script wakes up the laptop, fans start after time in script.
2. After 5 sec, system sleep again in suspension
3. When I open the lid, the system wakes up from suspension...and goes to hibernation!
4. Power on to the button, brings me to a normal hibernation wake up.

I'm almost there...but... any clue?

---

