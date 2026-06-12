---
title: "[SOLVED] How to force quit in XFCE"
date: 2008-11-23
forum: General Help
---

### Post by RandyNose on 2008-11-23
I posted this on my Blog, but I wanted to share it here also, in hopes someone else finds the information useful. The original entry / thread was old and closed, but here's a little XFCE tip anyhow.  I was looking for a quick and easy way to kill a program like I can in Gnome. 

I found this entry on the Ubuntu forums:

[I]Thomas Beckett Said:

I always find it easier when you have a gui program to just run the xkill" command - the pointer changes to the kill icon - you then click on your crashed program and its gone

Tom[/I]

Ok, that's cool. That works. But what about the next time? I want a darn icon on the panel so that I can click click kill and get.
To get this, I did thus.


Right Click on the panel > Add Launcher (Program Launcher with Optional Menu) > in the Command box enter in xkill Add a name to this function if you wish, I used X Kill add a description if you wish, and add a Icon if you wish. And Viola! :) Now you can click on that icon, a little **X** pops up that you then can click on the program that's locked up. 

[IMG]http://lh3.ggpht.com/_oiDliTYCQoc/SSnG2L3VrZI/AAAAAAAAADQ/J4exdXkll5A/Screenshot-20.png[/IMG]


You can now kill rascal programs with a click click and get on with your bad self to the next thing you forgot about to do since you were going to do the first thing that didn't work cuz you had to kill a program and get on with your day.. And also maybe try to figure out why the darned blabbeded thing crashed. File a Bug Report etc... :confused: 

Another neat thing to add with this file launcher the Terminal.. Just add " xfce4-terminal " in the command box of the launcher and you'll have a fresh terminal window to play with also. 

[There is a sligly more wordy version over here on my blog.. ]("http://randynoseworthy.blogspot.com/2008/11/how-to-force-quit-in-xfce-ubuntu-forums.html")

---

### Post by jimmy the saint on 2008-11-23
Great tip.  Make sure you mark it as solved so that people know there is a solution here.

---

### Post by sisco311 on 2008-11-23
> **RandyNose said:**
> 
Right Click on the panel > Add Launcher (Program Launcher with Optional Menu) > in the Command box enter in xkill Add a name to this function if you wish, I used X Kill add a description if you wish, and add a Icon if you wish. And Viola! :) Now you can click on that icon, a little **X** pops up that you then can click on the program that's locked up. 


you can press Ctrl+Alt+Esc to start xkill.

to set a different keyboard shortcut go to:

Menu -> Settings -> Settings Manager -> Keyboard -> Shortcuts

> 
Another neat thing to add with this file launcher the Terminal.. Just add " gnome-terminal " in the command box of the launcher and you'll have a fresh terminal window to play with also. 

in xfce the default terminal is xfce4-terminal

---

### Post by RandyNose on 2008-11-30
> **jimmy the saint said:**
> Great tip.  Make sure you mark it as solved so that people know there is a solution here.

Done.

---

### Post by RandyNose on 2008-11-30
> **sisco311 said:**
> you can press Ctrl+Alt+Esc to start xkill.

to set a different keyboard shortcut go to:

Menu -> Settings -> Settings Manager -> Keyboard -> Shortcuts



in xfce the default terminal is xfce4-terminal

Updated to reflect the correct terminal for the Desktop Enviroment. I figured there was, but didn't know what the XFCE terminal name was. 

As for Ctrl+Alt+Esc to start xkill, that's good to know. :)

---

### Post by OrangeCrate on 2008-11-30
> **RandyNose said:**
> I posted this on my Blog, but I wanted to share it here also, in hopes someone else finds the information useful...

<snip>



Cool, thanks.

:)

---

### Post by rob86 on 2009-10-13
I was missing this feature on XFCE for the last month and just thought to google a solution. Easy, thanks to this thread. Thanks.

---

### Post by Fffuuuu on 2011-03-17
For everyone that googles this up these days - as I did - and end up just as infuriated because this method doesn't actually close the process: I've finally come up with a real solution.

Do the same thing above, but use this as the command. Also I named mine Force Quit.
```
kill -9 `xprop _NET_WM_PID | sed -ne 's/[^0-9]*\([0-9]\+\)/\1/p'`
```

This will actually kill the window's process for sure instead of just cutting off its connection to X.

Props (no pun intended) to [this linux user]("http://www.linuxquestions.org/questions/linux-software-2/advanced-question-finding-pid-of-an-x-window-328983/") who answered his own question and thereby helped me make this solution. The linux community needs more users like this person instead of the smart asses that plague my Google search results for anything related to linux.

EDIT: Actually you'll need to put that in a script, and put the script name in the command box. Lame.. Anyway, I:
1) sudo nano /bin/click2kill
2) Pasted that in and saved
3) sudo chmod 755 /bin/click2kill
4) Then put _click2kill_ as the command to run in the properties.

EDIT 2: If anyone figures out away to allow the user to cancel the window selection, please post it. Preferably canceling by right-clicking like xkill offers. Currently, there's no turning back after running it. :(

---

### Post by greasegum on 2011-07-05
This method works great! Huge thanks.

-EG


___

[I]I see us hurtling through the dark.
I tell Viktor there is a curious connection between weapons and waste. He says maybe one is the mystical twin of the other. He likes this idea. He says waste is the devil twin. Because waste is the secret history, the underhistory, the way archaeologists dig out the history of early cultures, every sort of bone heap and broken tool, literally from under the ground.
“It is only obvious,” he says. [/I]
Don Delillo, Underworld (pp. 791)

---

### Post by masuch on 2012-01-20
Thanks, helped me as well.

---

### Post by oaxacamatt1 on 2012-02-24
Fffuuuu, I like this click2kill tip.
Works for me!!

---

### Post by LewisTM on 2012-02-24
My contributions:

1)You don't need to make a script. Just enter this in the command box:
```
sh -c "kill -9 `xprop _NET_WM_PID | sed -ne 's/[^0-9]*\([0-9]\+\)/\1/p'`"
```

2) To cancel
Bind Control-Shift-Esc (or whatever) to
```
killall xprop
```

3) Or all-in-one shortcut (toggle)
```
sh -c "killall xprop && exit;kill -9 `xprop _NET_WM_PID | sed -ne 's/[^0-9]*\([0-9]\+\)/\1/p'`"
```

Bingo!

---

