---
title: "[SOLVED] Thunderbird not opening!"
date: 2008-09-18
forum: General Help
---

### Post by Delta458 on 2008-09-18
Hello,

I have installed Mozilla Thunderbird via the synaptic package manager.
[B]
My sources list: [/B] 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb [http://ubuntu.iuculano.it](http://ubuntu.iuculano.it) feisty thunderbir
deb-src [http://ubuntu.iuculano.it](http://ubuntu.iuculano.it) feisty thunderbir

**What I did: **

First I downloaded thunderbird and then i used this **[guide]("http://wiki.ubuntuusers.de/Thunderbird/Installation")**
But then I canceled this guide. I thought its gonna be easier with this **[guide]("http://ubuntuswitch.blogspot.com/2007/09/ubuntu-how-to-get-yahoohotmail-emails.html")**

After I finished the last guide, I had the problem that Thunderbird wont open! I click on Applications -> Internet -> Thunderbird ... but nothing happens... only on the taskbar "Starting mozilla Thunderbird" is displayed and then happens nothing.


Can anyone help me?

(I am using Ubuntu 8.04 LTS Version)

---

### Post by whizbaby on 2008-09-18
Let me ask a question first:
are you running hardy or feisty? Because you have all mixed up in your sources.list and its likely to cause problems. If you are unsure which distro is running please post the output of
```
cat /etc/issue
```

and
```
uname -r
```

---

### Post by LowSky on 2008-09-18
Dude, Thunderbird is available from the Ubuntu repos, you didn't need to add any new ones.
First uninstall thunderbird
get rid of these you dont need them
deb [http://ubuntu.iuculano.it](http://ubuntu.iuculano.it) feisty thunderbir
deb-src [http://ubuntu.iuculano.it](http://ubuntu.iuculano.it) feisty thunderbir

then install it normally from terminal.
sudo apt-get install mozilla-thunderbird

---

### Post by whizbaby on 2008-09-18
Sorry I apparently overread your comment in brackets-.-
Lowsky is right, thunderbird is in the repos and the secong guide you mention is probably more than a year old. Good luck!

---

### Post by Delta458 on 2008-09-18
**Version: **
Ubuntu 8.04.1 
and:
2.6.24-19-generic

I did remove: 
deb [http://ubuntu.iuculano.it](http://ubuntu.iuculano.it) feisty thunderbir
deb-src [http://ubuntu.iuculano.it](http://ubuntu.iuculano.it) feisty thunderbir

and installed Thunderbird from the terminal. But still not working.

May be a registry problem? 
I remember when I did the first guide, that I entered the **following command:**
sudo ln -s /opt/thunderbird/thunderbird /usr/local/bin

---

### Post by LowSky on 2008-09-18
did you uninstall T-bird and its directories before reinstalling it?

does it give any errors if you run thunderbird from a terminal

just type **thunderbird **or **mozilla-thunderbird**, im not sure what the command is, I'm on a windows machine right now

---

### Post by Xgen on 2008-09-18
Start thunderbird from the terminal and see what (if any) error pops up. If it is a missing libstdc++5  file then install it from Synaptic.

---

### Post by Delta458 on 2008-09-18
Yes. I tried to start** TBird** from the terminal but I get a **libstdc++5 error.**

So I used **Synaptic** to install TBird, but it didnt help.

---

### Post by whizbaby on 2008-09-18
Sorry delta, there seems to be a little misunderstanding. What the two people above want from you is to start thunderbird in the terminal, not to install it with apt in the terminal. That way thunderbird will give error messages in the console that would give a hint about what is missing.
Or are we all misunderstanding you, and you don't have any executable on your machine?

---

### Post by buntunub on 2008-09-18
I think he is suffering from the same thing that just happened to me. Good ol TBird was working swimingly for me up until about a week ago, and then it just stopped working. It would load up about half way and then just freeze up so I would be forced to kill it every time. Launching it from Terminal as $thunderbird %t resulted in the same thing, with zero error messages. On a hunch, I tried to launch it as follows: $/usr/bin/thunderbird and it worked. When it finally loaded up, a popup came up for an overdue calender event warning, which I cleared. Now it launches from default settings again with no issues.

---

### Post by Xgen on 2008-09-19
Yes, Delta458, there was a misunderstanding. If starting from Terminal gives an error (missing libstdc++5) then install libstdc++5 with Synaptic and thunderbird will start with the launcher.

---

### Post by Delta458 on 2008-09-19
Ah THANK YOU!
I installed libstdc++5 with Synaptic and my problem is solved now! TBird is opening :) 

regards,
delta

---

