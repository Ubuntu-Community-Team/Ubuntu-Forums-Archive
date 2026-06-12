---
title: "Ubuntu cannot download a thing"
date: 2009-07-29
forum: Installation &amp; Upgrades
---

### Post by curtis_murray on 2009-07-29
My god, I am surprised Ubuntu is even considered a platform. It has been nothing but endless problems for me and I am getting tired of it. Can anyone help me? I can't seem to download a thing because it continuously thinks I have 2 update managers open up even though i shut down like a billion times, killed every damn process running.

I do not mean to sound angry but Ubuntu is an utter disgrace right now, and I would love some help. Maybe I am using this "operating system" wrong?

---

### Post by curtis_murray on 2009-07-29
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


I tried using ps -e and looking for any applications that might possibly be open that would be preventing it but Nothing!

---

### Post by lisati on 2009-07-29
> **curtis_murray said:**
> **[COLOR="Red"]E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.[/COLOR]** 
E: _cache->open() failed, please report.


I tried using ps -e and looking for any applications that might possibly be open that would be preventing it but Nothing!

*sigh*
Open up a terminal, and type in the following:
```
sudo dpkg --configure -a
```

---

### Post by pastalavista on 2009-07-29
Reboot into recovery mode and select 'repair broken pakages'. Then open a root terminal with networking and run ```
sudo apt-get update | sudo apt-get dist-upgrade
```. Reboot normally.

edit: I didn't see your second post. Do what **lisati** said.

---

### Post by curtis_murray on 2009-07-29
Beautiful! That worked but after that, it told me I had a broken package. But I managed to get around it thank you again! 

Also somewhat really off topic, what programs would you use to stream music for an internet radio. A friend of mine was wondering but he doesn't have an account on these forums. 

He want's to start an internet radio but he doesn't have a clue to what programs to use

---

### Post by pastalavista on 2009-07-29
I've heard good things about [Flumotion]("http://www.flumotion.net"). I think it's in the repositories but don't know if it's the latest version.

---

### Post by curtis_murray on 2009-07-29
What program is this? Also how would I go about downloading it? Through terminal or Add/Remove?

Got a tutorial on using it?

Thanks for the help everyone! xD

---

### Post by rlj1965 on 2009-07-29
> **curtis_murray said:**
> What program is this? Also how would I go about downloading it? Through terminal or Add/Remove?

Got a tutorial on using it?

Thanks for the help everyone! xD

Curtis,

You may have noticed that the poster (pastalavista) provided you a link to Flumotion ([http://www.flumotion.net/](http://www.flumotion.net/)). Even had he/she not given you the link, a quick Google search turned up a link immediately. I don't want to sound mean, but one must sometimes help oneself.

---

### Post by curtis_murray on 2009-07-29
Very very true, only thing is I have been trying to do that for all those stupid problems that Ubuntu has thrown at me and I have just lost all faith in it. Google has not been a friend of mine for awhile now, and just recently has Ubuntu Forums actually started to help.

---

### Post by lisati on 2009-07-29
> **curtis_murray said:**
> Very very true, only thing is I have been trying to do that for all those stupid problems that Ubuntu has thrown at me and I have just lost all faith in it. Google has not been a friend of mine for awhile now, and just recently has Ubuntu Forums actually started to help.

Sometimes going to [www.google.com](www.google.com), typing in a few keywords AND putting in site:ubuntuforums.org in the search box turns up results quicker than just using the search terms or using the forums search feature.

---

