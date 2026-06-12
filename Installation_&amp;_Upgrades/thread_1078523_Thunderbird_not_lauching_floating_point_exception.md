---
title: "Thunderbird not lauching: floating point exception?"
date: 2009-02-23
forum: Installation &amp; Upgrades
---

### Post by maxinquaye on 2009-02-23
Thunderbird crashed while I was adjusting my font preferences. Since then I haven't been able to launch it again. When I try through Applications -> Internet -> Mozilla Thunderbird I get the spinning hourglass icon for a while, then nothing. When I try through the terminal I get the following message:

```
Floating point exception
```

Any ideas?

---

### Post by maxinquaye on 2009-02-23
bump! ;)

---

### Post by maxinquaye on 2009-03-03
OK folks,

Latest developments include an attempt to reinstall the program (unsuccessful) followed by a full uninstall & reinstall. Still the floating point (t)error persists. Looks like Thunderbird is rooted deep into the system and I can't dig it out any more!
It might also be relevant to note the issue arose when I was trying to change the font type & size under Preferences after having installed new system wide fonts.
I would greatly appreciate any feedback!
Thank you for your time! ;)

---

### Post by maxinquaye on 2009-03-08
*bump*

Anyone please? . . .

---

### Post by cubeist on 2009-03-08
Perhaps start by removing the fonts you installed, and see if that fixes it.

If not, go into your home folder and backup your .mozilla folder, as a precaution.

Then completely uninstall thunderbird
```
sudo apt-get purge mozilla-thunderbird
```

then reinstall
```
sudo apt-get install mozilla-thunderbird
```

If all that doesn't work, post back with any new error messages

---

### Post by maxinquaye on 2009-03-10
Thank you much for your help!
I did exactly as you suggested: I removed the troublesome fonts, then ran the two pieces of code you suggested in a terminal. Still I get the same error message when I try to launch Thunderbird from the terminal:

```
gil@gil-laptop:~$ thunderbird 
Floating point exception
```

I still cannot figure out what is going on here . . . Even when I fully purge the program out of the system & reinstall it, I am shown the Floating point exception whenever I try to launch it from the terminal! When I try it by clicking its icon, I get a spinning wheel for a few moments, then nothing.

Any further ideas most welcome!

---

### Post by cubeist on 2009-03-10
Despite my previous comments, I think I am running a version of thunderbird I installed directly from the mozilla site... this might work for you to

first, again, purge your existing thunderbird package,
then go here
[http://www.mozillamessaging.com/en-US/thunderbird/system-requirements/](http://www.mozillamessaging.com/en-US/thunderbird/system-requirements/)
and make sure you have all the libraries listed for linux (install them via synaptic if you don't)

then download a fresh copy and install (or try again the version from synaptic)
[http://www.mozillamessaging.com/en-US/thunderbird/all.html](http://www.mozillamessaging.com/en-US/thunderbird/all.html)

---

### Post by maxinquaye on 2009-03-19
Sadly, not even that helped. I went even further and searched in nautilus for all instances of thunderbird on the filesystem, sudo rm them all, and then reinstalled Thunderbird. Result: when I try to launch the application through the terminal, all I get is the floating point exception error.
I ran out of options here, and all I can think of is a system bug. Maybe I'll try again when Jaunty is out?

Anyhow thank you very much for your help! :(

---

### Post by maxinquaye on 2009-04-05
I finally managed to solve the issue! All I had to do was to delete the hidden .mozilla-thunderbird profile file on my home directory, reinstall, et voila! Thunderbird was back!

---

### Post by theeo on 2009-12-04
Floating point exception realy maybee due to **font** problems!!!

My problems was propably due to deleted all confs at /etc/fonts/conf.d so I reinstalled package fontconfig-config and Thunderbird works again!

---

