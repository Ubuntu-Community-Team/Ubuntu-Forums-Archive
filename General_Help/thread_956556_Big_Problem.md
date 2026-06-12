---
title: "Big Problem"
date: 2008-10-23
forum: General Help
---

### Post by Robert John Kelly on 2008-10-23
I recently switched over to ubuntu for many reasons. I do really like it but it is so hard to use. the problem i'm having now is that after days of confusion as to how to install any software. once i figured it out, something has gone wrong with it and i can no longer install anything. whether it be with the synaptic package manager or self installing deb files. this is the error message i keep getting:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
i'm sure to most of you that is so simple it's not even funny, but for me it is so infuriating it's driving me insane..... literally! so if anyone can help i would greatly appreciate it. and please keep in mind my understanding of this all is non existant. try to explain it like your talking to a 3 year old. very slowly, step by step and in great detail. any help would be greatly appreciated. i'll check back on here but if it's easier to just e-mail me, my e-mail is [email]robertjohnkellyjr@hotmail.com[/email] . again thanks in advance

---

### Post by hyper_ch on 2008-10-23
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by melojo on 2008-10-23
dpkg --configure -a

open a termianl under accessories and type
sudo dpkg --configure -a if you get any error messages post them.

---

### Post by DGortze380 on 2008-10-23
> **Robert John Kelly said:**
> I recently switched over to ubuntu for many reasons. I do really like it but it is so hard to use. the problem i'm having now is that after days of confusion as to how to install any software. once i figured it out, something has gone wrong with it and i can no longer install anything. whether it be with the synaptic package manager or self installing deb files. this is the error message i keep getting:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
i'm sure to most of you that is so simple it's not even funny, but for me it is so infuriating it's driving me insane..... literally! so if anyone can help i would greatly appreciate it. and please keep in mind my understanding of this all is non existant. try to explain it like your talking to a 3 year old. very slowly, step by step and in great detail. any help would be greatly appreciated. i'll check back on here but if it's easier to just e-mail me, my e-mail is [email]robertjohnkellyjr@hotmail.com[/email] . again thanks in advance

open a terminal from the accessories menu. type

```

sudo dpkg --configure -a

```

press enter.

wait.

post the output here.

This generally happens when an installation does not finish correctly.

---

### Post by drs305 on 2008-10-23
To correct:
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. " 
normally all you need to do is run the following. You will be asked for your password. You won't see it as you type but it will be registered. Just hit Enter once you have typed it.

```
sudo dpkg --configure -a
```

If that doesn't solve it please post the resulting error message.

---

### Post by rbee on 2008-10-23
watch the spaces in the command line.

---

### Post by Robert John Kelly on 2008-10-23
ok i don't think anyone is understanding how much i don't understand any of this. i have no idea what any of you are talking about. this may seem very simple to you, but it's not to me. i made it quite clear how over simplified i need this to be. this terminal stuff makes no sense to me at all. i do appreciate the help, but it's not helping if i don't understand it

---

### Post by melojo on 2008-10-23
> **Robert John Kelly said:**
> ok i don't think anyone is understanding how much i don't understand any of this. i have no idea what any of you are talking about. this may seem very simple to you, but it's not to me. i made it quite clear how over simplified i need this to be. this terminal stuff makes no sense to me at all. i do appreciate the help, but it's not helping if i don't understand it


Just goto a terminal
Click
Applications>Accessories>Terminal
At the terminal 
```
sudo dpkg --configure -a
```

Thats it!!

---

### Post by Robert John Kelly on 2008-10-23
ok, i think i got it now, it just threw me off when you guys had this box sayin code. i was lost for a min but i re-read all of your replies, and i think i got it now. thank you all so much. so if i ever see something like that again and it tells me i have to manually do it can i just open another terminal like that and put in what ever it says? again thank you all so much. if there is anyway i could help any of you with anything don't hesitate to let me know. thanks

---

### Post by melojo on 2008-10-23
> **Robert John Kelly said:**
> ok, i think i got it now, it just threw me off when you guys had this box sayin code. i was lost for a min but i re-read all of your replies, and i think i got it now. thank you all so much. so if i ever see something like that again and it tells me i have to manually do it can i just open another terminal like that and put in what ever it says? again thank you all so much. if there is anyway i could help any of you with anything don't hesitate to let me know. thanks

Yes try that first and if it doesn't work come back and post a question.

---

### Post by rbee on 2008-10-23
you may get a second pop-up, if so look upper top of screen, there should be a icon just after your name, right click it as it states, this fixed my downloading problem

---

### Post by ajgreeny on 2008-10-23
1.  In your menu go to Programs->Accesories->Terminal
2.  In the terminal window that appears type sudo dpkg --configure -a
3.  Type in your user password (nothing will appear on screen but it will be entered, don't worry) and press enter.
4.  If any error messages appear, copy them and come back again.  If the terminal simply ends up back at your user prompt, all is probably OK, so try installing something again.

As a general point, always start by looking in synaptic for any software you want to install, either by name or by a description of what you are trying to use it for, eg for mp3 players just search "mp3"

EDIT:  Sorry too slow, I had a phone call after I started.

---

