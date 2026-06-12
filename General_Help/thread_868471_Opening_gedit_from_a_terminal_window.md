---
title: "Opening gedit from a terminal window"
date: 2008-07-23
forum: General Help
---

### Post by malth on 2008-07-23
In Ubuntu I want to start gedit from the terminal without having the terminal keep monitoring the process so I can continue to use that terminal for other commands. i.e., I want to launch gedit and have it detached from the tty. You can sort of do this with:

```

$ gedit&

```

...but then you can't feed gedit any paramaters, e.g.,

```

$ gedit& somefile.py

```
doesn't work, neither does
```

$ gedit somefile.py&

```
or
```

$ 'gedit somefile.py'&

```

You can always hit Ctrl-z to background the process which almost does what I want it to do, but the extra step for this shouldn't be necessary if you don't want it. How would you make this happen, could I make a shell function that forks it in some way?

---

### Post by ali999 on 2008-07-23
why not just open a new terminal window? thats what i always do and never ran into any problems.

---

### Post by evets25 on 2008-07-23
Here's 2 options: 

- open another tab in gnome-terminal
- run gedit using alt-f2

---

### Post by steveneddy on 2008-07-23
```
sudo gedit /path/to/file
```

**EXAMPLE**

to open your xorg.conf file you would copy and paste this in terminal

```
sudo gedit /etc/X11/xorg.conf
```

it will ask for your password. Input your password.

xorg.conf opens in gedit.

You would need to use sudo if it is a file that isn't in your /home folder and you wanted to edit that file.

---

### Post by Locutus_of_Borg on 2008-07-23
gedit /path/to/file &

works for me

---

### Post by bodhi.zazen on 2008-07-24
you might like nohup

nohup gedit file &

nohup allows you to then close the terminal without killing gedit.

---

### Post by malth on 2008-07-24
ah Locutus_of_Borg you're right, $gedit filename & does work. I swear it wasn't working on the terminal i had open the other day. I guess I'll make a shell function:
```

gedit()
{
gedit $1 &
}

```

wow some these other answers are sort of bad.

Ali999: because I want to continue at the same place where I was when I executed the command or maybe there are a bunch of terminals open and there's no reason to have another. Why don't you try to answer the question instead of disqualifying it.

steveneddy: I'm sorry, how does sudo help in this case? It does the same thing, but runs it with privileges. Did you read the question / is that the only thing you know about linux? "Try it with sudo. Maybe it'll work". That's retarded.

---

### Post by chickpea on 2008-07-24
> **malth said:**
> ah Locutus_of_Borg you're right, $gedit filename & does work. I swear it wasn't working on the terminal i had open the other day. I guess I'll make a shell function:
```

gedit()
{
gedit $1 &
}

```

wow some these other answers are sort of bad.

Ali999: because I want to continue at the same place where I was when I executed the command or maybe there are a bunch of terminals open and there's no reason to have another. Why don't you try to answer the question instead of disqualifying it.

steveneddy: I'm sorry, how does sudo help in this case? It does the same thing, but runs it with privileges. Did you read the question / is that the only thing you know about linux? "Try it with sudo. Maybe it'll work". That's retarded.

it is good you have your problem solved. and Locutus_of_Borg's post helped me too.
but come on! i was surprised when i read your comments on Ali999's post and steveneddy's. i don't think such an attitude is appropriate.

---

### Post by Potatoj316 on 2008-07-24
Am I reading this all wrong.  What with the gedit /path/to/file **&**. Whats with the &, just using gedit /path/to/file works for me.  

Also some times people ask specific questions because they dont realize it is possible to do something a different way.  The object of these forums are to help people, helping them could mean getting them to an answer that works, it dosent always mean get it to do exactly what they want.

---

### Post by bodhi.zazen on 2008-07-24
> **Potatoj316 said:**
> Am I reading this all wrong.  What with the gedit /path/to/file **&**. Whats with the &, just using gedit /path/to/file works for me.  

Also some times people ask specific questions because they dont realize it is possible to do something a different way.  The object of these forums are to help people, helping them could mean getting them to an answer that works, it dosent always mean get it to do exactly what they want.

The & puts gedit in the "background", meaning you can continue to enter additional commands in the terminal while running gedit (without having to manually put it in the background). Give it a try and see :

gedit ~/.bashrc

quit gedit

gedit ~/.bashrc &

---

### Post by steveneddy on 2008-07-25
> **malth said:**
> 

steveneddy: I'm sorry, how does sudo help in this case? It does the same thing, but runs it with privileges. Did you read the question / is that the only thing you know about linux? "Try it with sudo. Maybe it'll work". That's retarded.



You're correct. I'm retarted.

Thank you for noticing.

I've lost my helmet, could you help me find it?

---

### Post by steveneddy on 2008-07-25
EDIT:

nevermind - thanks

---

### Post by evsombody on 2008-11-19
malth - thanks, although you stated the truth harshly, I completely agree. this is the exact question I was looking for an answer for, and was asked. I was already aware of all the other responses, becuase of my own poor skill's. 

Each of has our own reasons for wanting or doing something our way, dont feed someone peas when they wanted green beans, then say well there both green and vegtables. I appricate everyones answers, but dont try to redifine the question, answer the question requested

---

### Post by dtzortzis on 2012-02-18
> **evets25 said:**
> Here's 2 options: 

- open another tab in gnome-terminal
- run gedit using alt-f2

This works for me and I think it's the best option.
Open a terminal. Open gedit using Alt+F2. Then, in the terminal type 
```
gedit whateverfile
```
and that just opens the file you want in gedit but leaves the terminal free do do anything else. Try it :)

---

### Post by philinux on 2012-02-18
Alt F2 in 11.10 opens the run command in the Dash with unity anyway.

This thread is from 2008 so closed. Please dont resurrect old threads.

---

