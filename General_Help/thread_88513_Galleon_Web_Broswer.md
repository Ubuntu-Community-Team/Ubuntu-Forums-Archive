---
title: "Galleon Web Broswer"
date: 2005-11-10
forum: General Help
---

### Post by eyebrowman92 on 2005-11-10
Ive added galeon web browser using the add applications tool under applications.  everytime i try to start it it shows it loading on the bottom task bar but it never comes up. does anyone know why?

---

### Post by jeffreyvergara.NET on 2005-11-10
same here... so I just gaved up on Galeon and stayed with Firefox, i dont have any regrets. ^_^

---

### Post by eyebrowman92 on 2005-11-10
alright but its too bad we dont know whats causing it.:(

---

### Post by Lambert on 2005-11-10
Not sure if this works but I've used it for a couple other applications like opera.

From a terminal type

```
galeon --debug
```

It may give you some lines of error to help troubleshoot what's happening.

---

### Post by bonzodog on 2005-11-10
try executing it from a terminal with '$galeon', it will tell you why it isn't opening..

---

### Post by etc on 2005-11-10
I just installed galeon to see what's up, and running galeon --debug, I got this:
```
** (galeon:8826): WARNING **: I could not load the bookmarks file, will load the default bookmarks from /usr/share/galeon/default-bookmarks.xbel.
INTERNAL ERROR on Browser End: JavaPluginFactory5 init - no agent?

System error?:: No such file or directory

```
If thats any help.

---

### Post by eyebrowman92 on 2005-11-10
alright well i did everything in a term and nothing fixed it. ill just stick with firefox.

---

### Post by 23meg on 2005-11-10
[QUOTE=eyebrowman92]alright well i did everything in a term and nothing fixed it. ill just stick with firefox.[/QUOTE]
If you don't state what exactly you did and the exact error output you got noone can be of any help. Why don't you paste the output you're getting on the console, if any?

---

### Post by eyebrowman92 on 2005-11-10
i get this when i start it in a terminal. ```
[B]
** (galeon:11954): WARNING **: I could not load the bookmarks file, will load the default bookmarks from /usr/share/galeon/default-bookmarks.xbel.









[/B]
```thats all i got then it dissappears. i can briefly see something else but dont have time to read or copy it.

---

### Post by etc on 2005-11-10
[https://launchpad.net/distros/ubuntu/+source/galeon/+bug/3747](https://launchpad.net/distros/ubuntu/+source/galeon/+bug/3747)
galeon seems to do this when you have j2re-1.4 is installed.

---

### Post by eyebrowman92 on 2005-11-10
how do i upgrade? what is the next upgrade from that?

---

### Post by 23meg on 2005-11-11
[http://www.ubuntuforums.org/showthread.php?t=76754](http://www.ubuntuforums.org/showthread.php?t=76754)

---

### Post by eyebrowman92 on 2005-11-11
alright thanks. ill try it. also is galleon a desent browser?

---

### Post by 23meg on 2005-11-11
It uses Gecko like Epiphany and Firefox so it's exactly as good at rendering pages; it has a few advanced features that don't exist in Epiphany. After its next version it will be dropped; Galeon programmers will start working on Epiphany instead.

---

### Post by eyebrowman92 on 2005-11-11
..why? is it galleons programmers who work for whatever make epiphany

---

### Post by 23meg on 2005-11-11
I don't exactly get your point, but Epiphany was actually a project that branched from Galeon.

[http://www.ubuntuforums.org/showthread.php?t=82375](http://www.ubuntuforums.org/showthread.php?t=82375)

---

### Post by eyebrowman92 on 2005-11-11
alright so basically the student surpassed the master since theyre giving up on galleon right?

---

### Post by 23meg on 2005-11-11
Right, kind of.

---

### Post by eyebrowman92 on 2005-11-11
but i dont understand...why are they giving up on galleon?

---

### Post by 23meg on 2005-11-11
The reasons are well detailed [here]("http://gnomedesktop.org/node/2450").

---

### Post by eyebrowman92 on 2005-11-11
thanks. hopefully the newer versions of epiphany are better than the current one.

---

### Post by heavyt on 2005-12-01
[QUOTE=eyebrowman92]Ive added galeon web browser using the add applications tool under applications.  everytime i try to start it it shows it loading on the bottom task bar but it never comes up. does anyone know why?[/QUOTE]

This help me with my galeon. It my help you. 
                                                                 
"Re: galeon fails to start if j2re-1.4 is installed Posted by chpe at 2005-11-27 20:48:15 UTC

Ok, I've tracked it down. Add this line to the ~/.galeon/mozilla/galeon/prefs.js file:

user_pref("general.useragent.vendorSub", "1.3.21");"

---

### Post by webguy on 2005-12-01
I used sudo apt-get install galeon and have had no problems. 

Webguy

---

### Post by missmoondog on 2005-12-30
through synaptic, did you get both galeon related files? ones called common something and the other, i forget, but they both show up 1 under the other in the list of available items. i've installed galeon and epiphany on all 5 of my machines without an isssue. both browsers are better than firefox, imo. epiphany is just a baby as of now though. in it's infancy.

---

