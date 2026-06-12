---
title: "Downgrad Firefox"
date: 2008-08-21
forum: General Help
---

### Post by Chronix33 on 2008-08-21
Hey folks,
I imagine that this has been answered, but could not locate the proper search words to find the answer. 
I want to know how to get rid of Firefox 3 and replace it with a previous version so I can bring back all the extensions that I used before. 
I'm using Ubuntu 8.04 Hardy. I would appreciate your patience as I am new to the world of Linux, so any explanations will have to be thorough. Thanks again, Chronix.

---

### Post by forger on 2008-08-21
You can try to enable old extensions for firefox 3, install mr tech toolkit
[https://addons.mozilla.org/en-US/firefox/addon/421](https://addons.mozilla.org/en-US/firefox/addon/421)

It adds a checkbox when installing new addons, when you check it, it allows you to bypass the max version check, so you can install firefox 2 addons on firefox 3.

Sometimes they work, sometimes they don't.

Which addons did you use? Give me a list and we could try finding some testing versions that are supported by firefox 3

---

### Post by forger on 2008-08-21
You say you use 8.04. Are you sure you're not using 8.04**[COLOR="Red"].1[/COLOR]**? Firefox 3 has been updated to a stable release since the 8.04 :)

Type in terminal:
```
lsb_release -a
```
It will show you your current release

---

### Post by Chronix33 on 2008-08-21
Well, my favorite add on is Firesomething. Completely useless, but I have come to love seeing random animals as my browser. I think if I could just get this one to work, I could come to love Firefox 3 and embrace it as I have done the previous versions.
Chronix

Edit:
Yes, it is 8.04.1

---

### Post by starcannon on 2008-08-21
All of my firefox 2 add-ons work in firefox 3; that said, if you really want to go back to ff2, you can find it in System->Administration->Synaptic Package Manager: Search: firefox-2

After Install is complete you can find it available in Applications->Internet->Firefox-2

I have not uninstalled 3, but I am assuming that could be done in the Synaptic Package Manager, you will likely need to set your preferred applications in system->preferences, you will also need to update your desktop icon to open up ff2.

I recommend following forger's advice though, downgrading to 2 is an extreme measure when all else fails I think.

GL and have fun

---

### Post by forger on 2008-08-21
Ok, after installing mr tech toolkit, restart and head to:
[https://addons.mozilla.org/en-US/firefox/addons/policy/0/31/15753](https://addons.mozilla.org/en-US/firefox/addons/policy/0/31/15753)
Click "Accept and Install"
Check the "override maxversion compatibility checking"
Click "Install now"

---

### Post by Chronix33 on 2008-08-21
Perfect. Thanks for that, forger. Simpsons rule, problem solved, have a great day.
Chronix

---

### Post by forger on 2008-08-21
no problem, Mozilla Hypnocoyote to the rescue! :)
If you can't make an addon work this way and have any trouble finding testing versions for firefox 3, post back here or make a new thread, someone will be able to help you probably

---

