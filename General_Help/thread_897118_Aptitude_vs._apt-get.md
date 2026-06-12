---
title: "Aptitude vs. apt-get"
date: 2008-08-21
forum: General Help
---

### Post by lorgonjortle on 2008-08-21
So I don't get what the different between aptitude and apt-get is...

Could you say:

apt-get install build-essential

and

aptitude install build-essential

???


Or are they only used for certain things?:confused:

---

### Post by Unanimated on 2008-08-21
They are virtually the same thing, just a different interface when it's installing something, and apt-get asks different questions than aptitude does.

---

### Post by pparks1 on 2008-08-21
Both of those commands would install the package indicated.   In years prior, aptitude handled removing dependent packages which were no longer needed.  However, recent updates to apt-get have added that functionality.

I typically use aptitude when I go to install something and it says there are recommended updates.   In this case, i so something like
sudo aptitude install --with-recommends package_name

apt-get gets about 95% of my business day-to-day.

---

### Post by iaculallad on 2008-08-21
Here, try reading this [thread]("http://ubuntuforums.org/showthread.php?t=379804").

---

### Post by mb_webguy on 2008-08-21
Aptitude and apt-get are separate but nearly identical programs.  While you can usually substitute "aptitude" whenever you see a command with "apt-get", I would suggest sticking to apt-get.  Because they are separate programs, if you switch back and forth between them you may have problems with one not recognizing packages installed or removed with the other.  I recommend apt-get instead of aptitude only because Synaptic is a front-end for apt-get, so using aptitude and Synaptic runs the same risk of problems as using aptitude and apt-get.

---

### Post by lorgonjortle on 2008-08-21
Jeeze... based on the poll on [THIS]("http://ubuntuforums.org/showthread.php?t=379804") thread, it seems pretty close, and since I am a newbie, I'm not sure what to pick. I think I'll go with apt-get, since I use Synaptic sometimes and I don't want a clash. Thanks for all of the answers everyone.

Cheers,

Jesse

---

### Post by hyper_ch on 2008-08-22
aptitude will also the recommended packages... apt-get will not.

---

### Post by lorgonjortle on 2008-08-22
> **hyper_ch said:**
> aptitude will also the recommended packages... apt-get will not.

IN SIG: There are 10 different kind of people! Those who understand binary and those who don't!

Hah, I have that on my MySpace. Such a good quote. Thanks for the tip. Aptitude sounds more ideal, but I use Synaptic too... Maybe I'll just stop using Synaptic.

---

### Post by bodhi.zazen on 2008-08-22
As has been pointed out there are minor differences these days between apt-get and aptitude. There a few options unique to one or the other and the configuration files are somewhat different.

If you want to know, read the man pages. If the man pages are too difficult or too much effort the it is safe to assume they are essentially the same.

---

