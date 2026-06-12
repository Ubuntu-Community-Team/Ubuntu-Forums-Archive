---
title: "JavaScript not working in web browser."
date: 2008-11-18
forum: General Help
---

### Post by Th3Professor on 2008-11-18
At the moment I'm using Mozilla Firefox. I'm unable to access a javascript app on a webpage.

I'm trying to log into a site that I have an old account on, though forgot the log-in/password.

I clicked on their "forgot your name or password?" link.

Where I enter username it has one of those anti-spam verification features (the javascript). It says "enter the words or numbers that you see or hear" basically. Though it just sets there with "loading..." (doesn't show it).

So, I clicked on the links that had help on getting it to work, though they were all javascript.

I was only able to find this for an independent install:
[http://code.google.com/p/recaptcha/downloads/list?q=label:java-Latest](http://code.google.com/p/recaptcha/downloads/list?q=label:java-Latest)
from:
[http://recaptcha.net/resources.html](http://recaptcha.net/resources.html)

A zip file has ".java", ".xml", and ".jar" files, though I'm not sure what to do with them.

Is there a package in the package manager that enables javascript in the web browser?

---

### Post by jespdj on 2008-11-18
That download you found does not have anything to do with the problem. It's a library for programmers who want to add a CAPTCHA to their website. It's not something that you can use to make some website work.

Are you talking about Java or JavaScript? Those are two totally different things. JavaScript is enabled in Firefox by default, and it would be really strange if it is disabled in your Firefox. But you can check: in Firefox, go to Edit / Preferences / Content and see if "Enable JavaScript" is checked.
> Where I enter username it has one of those anti-spam verification features (the javascript).
How do you know it's JavaScript?

It might just be a problem with the website. Try again in a few hours if the website still doesn't work.

---

### Post by Th3Professor on 2008-11-18
It says javascript on the bar at the bottom of the browser, something like "javascript:name_name(name)". (Name = something else.)

I tried 2 or 3 days ago, last night, this morning, this afternoon, still no luck.

The firefox java & javascript settings are all enabled.

---

### Post by lobo235 on 2008-11-18
Can you give us the location of the website you are having problems with so we can give it a try or is it something that you don't want to give out freely?

---

### Post by Th3Professor on 2008-11-18
sure :) it's:
[https://secure-web2.secondlife.com/account/request.php?lang=en](https://secure-web2.secondlife.com/account/request.php?lang=en)

---

### Post by lobo235 on 2008-11-18
It looks like it's a problem with their site and not just specific to Ubuntu or Firefox. I tried it in Opera and saw the same problem.

If you notice on the page it says "This reCAPTCHA key isn't authorized for the given domain." Perhaps they have not configured their reCAPTCHA script properly and that is what the problem is.

If the site has a way for you to contact them you can email them about the problem.

---

### Post by Th3Professor on 2008-11-18
Yep, I emailed them. Tehy require a phone call, lol. C'est la vie.
:)

---

### Post by easoukenka on 2008-11-19
You could also try yahoo.com hover over something on right menu like mail, messenger etc if something slides down you have javascript working.

---

### Post by scliburn on 2008-11-19
I was having the same problem in Firefox3 and Opera.

Downgraded to Firefox 2 and i dont have javascript hangs anymore.
This was happening on anysite with javascript calls within their links.

I even posted about this here:
[http://forums.cerb4.com/showthread.php?t=1473&highlight=javascript](http://forums.cerb4.com/showthread.php?t=1473&highlight=javascript)

---

