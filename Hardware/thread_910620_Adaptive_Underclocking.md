---
title: "Adaptive Underclocking?"
date: 2008-09-04
forum: Hardware
---

### Post by Oliver Acevedo on 2008-09-04
I have an M1330 with the famous nvidia 8400M GS. I'm not too happy with my battery life (about 2.5 hours) so I wanted to underclock my video card. I have the nvidia settings installed and can do it that way but every time you restart, it wipes out the settings. I also looked at the powermizer with the adaptive overclocking option and had 2 questions about it. 
#1 Is this only for 2D overclocking or does it effect the 3D clock speeds as well? Reason why I ask is because it just shows you the 2D clock speeds. 

#2 Is there a way to keep the clock speed under clock to like 100mhz when it's not needed and have it kick up to 300 or 400mhz when you play games or whatever? 

Thanks!

---

### Post by Oliver Acevedo on 2008-09-06
Bump

---

### Post by qazwsx on 2008-09-18
I was just experimenting with this.

You could create script for more demanding programs.

So nvclock (CLI) might be the answer to your problems.

We should set up new $PATH for your convenience.

run  
```
mkdir $HOME/.bin
```
open .bashrc in your home directory. Look for line that contains something like this:
```
export PATH=/usr/local/bin:/usr/bin:/bin:/usr/games
```
add before /usr/local/bin this
$HOME/.bin:

So the line should now look like this:
```
export PATH=$HOME/.bin:/usr/local/bin:/usr/bin:/bin:/usr/games
```
Restart terminal
Simple script example:

Lets do it for neverball which dosen't need really that much power.
create file:
$HOME/.bin/neverball

```
#!/bin/bash
nvclock -r
/usr/games/neverball
nvclock -m 200 -n 200
```
NOTE: You should set up your own settings depending on your own GPU! -r restores original settings, -m corresponds to memory clock and -n GPU clock.  In case of underclocking make sure you are really undercloking

Make it executable

```
chmod +x $HOME/.bin/neverball
```

and run it ```
neverball 
```

Hope this helps.

---

### Post by Oliver Acevedo on 2008-09-18
That sounds really good. Thanks I'm going to try it out and see. By the way, how the heck do you linux people know all these codes? I mean do you just come up with them by memory or do you have to look them up? Whenever I want to do anything in the terminal, I have to look it up or turn to google. But it seems like some of you know everything there is to know, almost by heart.

---

### Post by remu on 2008-09-19
Please let me know how that turns out for you, I'm quite interested in this as well!

---

### Post by qazwsx on 2008-09-20
> **Oliver Acevedo said:**
> By the way, how the heck do you linux people know all these codes? I mean do you just come up with them by memory or do you have to look them up? Whenever I want to do anything in the terminal, I have to look it up or turn to google.
Answer: Bash scripts are easy and fast to create once you memorize most of the commands. It takes some time. 
If you want to become one of us:
[http://tldp.org/LDP/Bash-Beginners-Guide/html/](http://tldp.org/LDP/Bash-Beginners-Guide/html/)
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

Never bothered to learn program languages. Bash pretty much does everything I need in that field (case is different for example  if you need more performance or access to lower level stuff esac ):)

---

