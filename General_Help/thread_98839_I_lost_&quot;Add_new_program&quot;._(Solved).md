---
title: "I lost &quot;Add new program&quot;. (Solved)"
date: 2005-12-04
forum: General Help
---

### Post by cydec on 2005-12-04
Hi all,

I was wondering if somebody can help me out here, i searched the forum but could not find a solution.

The problem is the following:

I lost the icon 'add new program' in my Menu Bar 
(i'm not sure of the name since its gone ;)). 
With that icon, that is normaly under "system tools", It was easy to install and remove programs...
It just disapeared.

Can somebody help me to get it back, or tell me the shell command ?

Yeah, i'm a pure newb, but i'm always testing stuff out... don't know what i did wrong here (i was installing FF 1.5 - what worked)

---

### Post by Cheule on 2005-12-04
[QUOTE=cydec]Hi all,

I was wondering if somebody can help me out here, i searched the forum but could not find a solution.

The problem is the following:

I lost the icon 'add new program' in my Menu Bar 
(i'm not sure of the name since its gone ;)). 
With that icon, that is normaly under "system tools", It was easy to install and remove programs...
It just disapeared.

Can somebody help me to get it back, or tell me the shell command ?

Yeah, i'm a pure newb, but i'm always testing stuff out... don't know what i did wrong here (i was installing FF 1.5 - what worked)[/QUOTE]

All is not lost, there is actually a second icon, in System --> Administration --> Add Applications

:)

---

### Post by ad noiseam on 2005-12-04
It might actually be gone, this had happened to me (see 
[this thread](http://www.ubuntuforums.org/showthread.php?t=84509)).

Try to enter the following in a terminal:
```

sudo apt-get install gnome-app-install

```

It did the trick for me.

---

### Post by cydec on 2005-12-04
[QUOTE=Cheule]All is not lost, there is actually a second icon, in System --> Administration --> Add Applications[/QUOTE]

I searched every menu before your tip because i thought it would be elsewhere. 
But could not find anything, but a big THANKS for the info anyway!

[QUOTE=ad noiseam]sudo apt-get install gnome-app-install[/QUOTE]

Tried it and worked: Thanks dude, i read your other thread also. I was realy desperate :rolleyes:. It's something to remember...

---

### Post by ad noiseam on 2005-12-04
I submitted a bug ([number 20462](https://bugzilla.ubuntu.com/show_bug.cgi?id=20462)) about this.

---

### Post by Cheule on 2005-12-04
[QUOTE=cydec]I searched every menu before your tip because i thought it would be elsewhere. 
But could not find anything, but a big THANKS for the info anyway![/QUOTE]

Hmm, sorry about that, for some reason my install of Ubuntu has two of them, one where you lost yours and one where I said the other one was.

Maybe I accidentally stole yours? :D

---

### Post by cydec on 2005-12-04
[QUOTE=Cheule]Hmm, sorry about that, for some reason my install of Ubuntu has two of them, one where you lost yours and one where I said the other one was.

Maybe I accidentally stole yours? :D[/QUOTE]

LoL no problem, you theaf hehehe.
Wel indeed now i have 2 of them like you said .
So my conclusion: the program was realy GONE...

---

### Post by aysiu on 2005-12-04
Have you tried Applications > System Tools > Application Menu Editor?

---

### Post by cydec on 2005-12-04
Like i said, problem solved in the mean time.
but thanks for the effort !

---

### Post by Zerocool10482 on 2005-12-07
you can go to the package manager and reinstall it. Look for gnome-app-install. It should come up. Mines up and running.

---

### Post by Zerocool10482 on 2005-12-07
you can go to the package manager and reinstall it. Look for gnome-app-install. It should come up. Mines up and running.

---

