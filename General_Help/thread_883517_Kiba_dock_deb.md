---
title: "Kiba dock deb"
date: 2008-08-08
forum: General Help
---

### Post by poot on 2008-08-08
can someone be kinda enough to point me in the direction of a deb package for the kiba dock with phisics please? i tried using the svn tutorial but i could never get it working. running hardy heron with compiz fuszion.

thanks in advance ^_^

---

### Post by northern lights on 2008-08-08
Googling "kiba dock physics deb" gives [http://ubuntuforums.org/showthread.php?t=728231]("http://ubuntuforums.org/showthread.php?t=728231")as the first result.

Does it need to be kiba?
As AWN is in the repos and cairo-dock can be easily added...

---

### Post by ayampanggang on 2008-08-08
has kiba stopped being developed?

until now the svn repo is still at revision 862, which is already several months old :/

i use kiba until now just because that's what i have and its working quite fine (though sometimes need restarting esp. after i switched back and forth between metacity and emerald)

any particular reason/feature in awn worth switching?

---

### Post by northern lights on 2008-08-08
I don't think you may label the project 'discontinued' yet, but the latest new releases certainly are a while back.

I dunno about AWN. I've seen the latest cairo-dock and it looked quite impressive. Appearance and usability wise.

Plus, they're installable via repositories. None of that building from source hassle.

---

### Post by ayampanggang on 2008-08-08
hmm i've just tried cairo dock for a few secs, but i feel like kiba's animation and icon morphing (e.g. bouncing) are smoother

---

### Post by northern lights on 2008-08-08
Fair enough.

All three have their perks and downsides. The best choice is obviously the candidate that best suit your individual needs/preferences.

I'd opt for checking out all, which in the case of AWN and cairo-dock is rather quickly done nowadays.

Anyway, the physics plug-in is not supported in the latest kiba release due to stability problems.

---

### Post by poot on 2008-08-08
yea i have AWN and i'm not that impressed with it...i was looking to try kiba and see how it was. I havent even began to try cario dock though...i might now ^_^


thanks for the link btw :)

---

### Post by poot on 2008-08-08
sorry for the bouble post but i looked in apt get and in synaptic and couldnt find cario dock...is it beacuse i'm running 8.04 hardy?

---

### Post by northern lights on 2008-08-08
> **poot said:**
> I havent even began to try cario dock though...i might now ^_^

thanks for the link btw :)

Here's another:
[https://help.ubuntu.com/community/CairoDock]("https://help.ubuntu.com/community/CairoDock")

---

### Post by poot on 2008-08-08
thanks for the link ^_^ we posted at the same time lol i'll be sure to try it out...the link for the deb packages arent for hardy i dont think...i tried installing them but it diddnt work

---

### Post by poot on 2008-08-08
ok just 1 more thing...i have cairo dock now and i like it...but when i want to use it i have to type cairo-dock into the terminal..and when i close the terminal it closes cairo dock. How can i make it so i can run it without having the terminal open?

---

### Post by northern lights on 2008-08-08
Instead of running it from terminal, you can either

- create a launcher on panel/desktop and put 'cairo-dock' in the command entry

- press Alt+F2 and run it from the "Run" dialog instead of the terminal

- run it from the terminal with 'cairo-dock &'
--> the & puts it in the background and you can close the terminal without the dock disappearing

Or, simply navigate to "System > Preferences > Sessions" and add it to the Startup Programs - that way it'll start automatically at bootup.


As an aside: Theoretically, the debs work in hardy also.

---

### Post by poot on 2008-08-08
oh ok thanks! it works.

and i'll keep playing around with the debs...maybe i can get it to work

---

