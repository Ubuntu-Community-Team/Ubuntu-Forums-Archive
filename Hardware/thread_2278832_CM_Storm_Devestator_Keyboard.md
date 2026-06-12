---
title: "CM Storm Devestator Keyboard"
date: 2015-05-19
forum: Hardware
---

### Post by Kaabi on 2015-05-19
Hey all,

I have a CM Storm Devestator Keyboard, that has a blue backlight.  Unfortunately it uses the SCRN LCK key to turn on and off, and I have been unable to figure out how to get that working.  What I would ideally like is for the led to turn on automatically at boot/login, but it would also be great if I could just get the SCRN LCK to turn it on and off.

I'm currently on Lubuntu 15.04 and am using ```
xset led 3
``` after logging in to turn it on.

Any help would be great.

Cheers
Kaabi

---

### Post by v3.xx on 2015-05-19
Adding linux to a search will do wonders :)
Check it out

[https://answers.launchpad.net/ubuntu/+source/linux/+question/241299](https://answers.launchpad.net/ubuntu/+source/linux/+question/241299)

[https://www.google.com/search?client=ubuntu&channel=fs&q=CM+Storm+Devestator+Keyboard+linux&ie=utf-8&oe=utf-8#channel=fs&q=CM+Storm+Devastator+Keyboard+linux&spell=1](https://www.google.com/search?client=ubuntu&channel=fs&q=CM+Storm+Devestator+Keyboard+linux&ie=utf-8&oe=utf-8#channel=fs&q=CM+Storm+Devastator+Keyboard+linux&spell=1)

I do not have this keyboard, but hope it helps.

---

### Post by Kaabi on 2015-05-19
Thanks....had a real blonde moment it seems....I think these blonde foils in my hair were a bad idea....

Found a solution.  Added the following line to /usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf: 
```
greeter-setup-script=xset led 3
```

Blonde moment officially "foiled." :P

Thanks.

---

### Post by v3.xx on 2015-05-19
Just a little trick :)  Here is another ..

[http://www.googlubuntu.com/](http://www.googlubuntu.com/)

For the benefit of others

 [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

