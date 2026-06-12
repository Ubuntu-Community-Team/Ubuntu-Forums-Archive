---
title: "[SOLVED] Enable sudo insults"
date: 2008-10-17
forum: General Help
---

### Post by TheLions on 2008-10-17
I heard that you can enable insults when you mismatch password in sudo, how to enable it????

---

### Post by sisco311 on 2008-10-17
edit the sudoers file:
```
export EDITOR=nano && sudo -E visudo
```

find the line that begins with *Defaults*

and append insults to the end:
> Defaults        env_reset,**insults**
save the file and exit(Ctrl+o, Enter, Ctrl+x)

clear your sudo session:
```
sudo -K
```

> Sorry about this, I know it's a bit silly.

You can't come in. Our tiger has got flu

Have a gorilla...

 :)

---

### Post by ruipalmeira on 2008-10-17
aahahahah didn't knew about this one :D...

my next screenshots will have this fo shure :popcorn:

---

### Post by HornedOne on 2008-10-21
Thanks for posting this.  I was bored over the weekend and ended up seeing some amusing responses...

"Are you trying to match wits with a rutabaga"

:lolflag:

---

### Post by MaxIBoy on 2008-10-21
```
maxtothemax@maxtothemax-laptop:~$ sudo apt-get install random-crap
[sudo] password for maxtothemax: 
My pet ferret can type better than you!
[sudo] password for maxtothemax: 
Your mind just hasn't been the same since the electro-shock, has it?
[sudo] password for maxtothemax: 
I can't hear you -- I'm using the scrambler.
sudo: 3 incorrect password attempts
maxtothemax@maxtothemax-laptop:~$ sudo apt-get install random-crap
[sudo] password for maxtothemax: 
I feel much better now.
[sudo] password for maxtothemax: 
I don't wish to know that.
[sudo] password for maxtothemax: 
You'll starve!
sudo: 3 incorrect password attempts
maxtothemax@maxtothemax-laptop:~$ sudo apt-get install random-crap
[sudo] password for maxtothemax: 
There must be cure for it!
[sudo] password for maxtothemax: 
Ying Tong Iddle I Po
[sudo] password for maxtothemax: 
Speak English you fool --- there are no subtitles in this scene.
sudo: 3 incorrect password attempts
maxtothemax@maxtothemax-laptop:~$ 

``` Whee!

---

### Post by macabro22 on 2008-10-21
:lolflag: This is awesome!!!

---

### Post by Phkillah on 2009-06-12
[sudo] password for phk: 
I've seen penguins that can type better than that.

---

