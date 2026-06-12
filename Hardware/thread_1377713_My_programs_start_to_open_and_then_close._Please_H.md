---
title: "My programs start to open and then close. Please Help"
date: 2010-01-10
forum: Hardware
---

### Post by dakman33 on 2010-01-10
Hi,
I've tried searching all over and cant seem to find the right way to find an answer. I have an Acer Aspire. My programs were working fine. Everything but when I went to go online yesterday, I found my programs starting up and then closing. 
I am VERY new to Linux and haven't been on it in months. This seemed to happen many months ago and the person who fixed it indicated it was a very simple fix. They're in another state and I have no way to contact them.
Can someone please help? I am desperate here. I have no idea how to figure this out. Is it a button on my keyboard?
The network connects and stays on, my desktop is there but again, when I try to run a program, they simply wont open. 

Thanks in advance for ANY suggestions for this extreme N00B.:(

---

### Post by dakman33 on 2010-01-11
wow. I know this was my first post but did I post it in the wrong place? Am I missing some info that might get a response? I'm seriously considering a new OS like a nice Windows XP or 7 just so I can get on the internet on that damn laptop (using a friends mac right now). Please at least tell me if I put this in the right place.

Thanks to anyone who can relate to a serious internet jones!

---

### Post by SecretCode on 2010-01-11
You posted in the right place (I think, anyway. This isn't really a hardware issue). It's just that there are thousands of posts here and nobody is responsible for making sure they are all answered within a few hours!

You didn't provide a lot of information, which could have helped people respond. 
- What version of Ubuntu (or other Linux OS) do you have installed? 
- And is it the only OS on the system, or are you dual booting?

I presume you can log on, since you get to the point of opening programs. 
- Does this problem happen with every program - including Places > Home Folder and Applications > Accessories > Terminal, or only some? If only some, it's very important to give examples.

- Are there any other problems or things that look wrong?

Now some things you would not have known to supply: 
If you can't open a terminal window things are going to be tough, but if you can, post the output of 
```
free -m
```
and
```
uname -a
```

---

### Post by Sylslay on 2010-01-11
one tip, run in consloe ctr+alt+f1, login and make sure is Your system up to date.

Upgrade software: To upgrade your complete operating system, 
use
sudo apt-get  update 
Then use 
sudo apt-get dist-upgrade.

---

