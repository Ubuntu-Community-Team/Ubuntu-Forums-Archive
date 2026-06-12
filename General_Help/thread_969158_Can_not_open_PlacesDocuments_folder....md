---
title: "Can not open Places/Documents folder...?"
date: 2008-11-03
forum: General Help
---

### Post by jwkungfu on 2008-11-03
Hi all,
I recently upgraded and when I tried to access a spreadsheet saved in Places/Documents I get an error message stating...
 
Could not open location 'file:///home/john/Documents'
Failed to execute child process "wxvlc" (No such file or directory)

Does anybody have any idea what has happened here?

:(

---

### Post by jcanfield on 2008-11-03
I am recieving the same error from clicking on either Places --> Home Folder, Places --> Desktop or any item in my Recent Documents. Except the error reads:'Failed to execute child process "prism" (No such file or directory)'.

I did a quick run though gconf-editor and did not find any launchers that would be doing that. This is odd.

---

### Post by jcanfield on 2008-11-03
Just an weird setting change that somehow happened when I upgraded to Intrepid.

[http://ubuntuforums.org/showthread.php?t=964392](http://ubuntuforums.org/showthread.php?t=964392)

---

### Post by jwkungfu on 2008-11-03
> **jcanfield said:**
> Just an weird setting change that somehow happened when I upgraded to Intrepid.

[http://ubuntuforums.org/showthread.php?t=964392](http://ubuntuforums.org/showthread.php?t=964392)

Hmmmmm....?
Looks like we may have stumbled on to a bug with the new upgrade?
Will have to report it...

---

### Post by raucous on 2008-11-04
For me:

Places - Home Folder

or:

Places - Documents


opens all of my music in audacious.

---

### Post by Gizmo69 on 2009-01-11
>> Could not open location 'file:///home/<user>' <<

Hello, 
Since 8.1 I do a similar problem in "places\<user>". The 'home' folder link,as well as the other personel links, do not work. I can remove them and place new onces though it does not matter. They do not work... What has changed ? Where can in change these ?

I read something in another thread ([http://ubuntuforums.org/showthread.php?t=964392](http://ubuntuforums.org/showthread.php?t=964392)). I could not do this directly, but with a litle playing there is was:

Using Nautilus (file manager), in "tree view". This is important! Then use "right mouse click"/properties, "open with" tab, add/ select the browser. And this solved my problem.

I hope it helps or gives a clue on how to solve your Ubuntu problems.

---

### Post by fooman on 2009-01-11
go to places > computer

this opens the nautilus file browser.  on the left side,  click on your user name...then on the right side, *right*-click on "Desktop".

choose "properties" from the drop-down menu. click the "open with" tab and put a check next to "open folder".

hope that helps.

---

### Post by Clueles on 2009-04-06
i have the same problem but i installed 8.10 and i got an error saying no nautalis found where can i get it??? or start it??????

---

### Post by drs305 on 2009-04-06
> **Clueles said:**
> i have the same problem but i installed 8.10 and i got an error saying no nautalis found where can i get it??? or start it??????
Are you sure you are spelling it correctly: nautilus

To see if it's installed, this should return the run path/command (/usr/bin/nautilus):
```

which nautilus

```

In the unlikely event it isn't installed, install it:
```

sudo apt-get install nautilus

```

---

### Post by Clueles on 2009-04-06
> **drs305 said:**
> Are you sure you are spelling it correctly: nautilus

To see if it's installed, this should return the run path/command (/usr/bin/nautilus):
```

which nautilus

```

In the unlikely event it isn't installed, install it:
```

sudo apt-get install nautilus

```

after some heavy thought i checked  the synaptic manager and i needed to install the nautilus software. now everything is working fine for now i guess.

next is to tackle the card readers....

---

### Post by Clueles on 2009-04-09
hey all i just wantedto say that everyone here has been so helpful. i got everything i needed on my own after searching the net. gotta love google...but anyway thanks again.):P

---

### Post by jluxenberg on 2009-07-11
I had the same problem after upgrading from 8.10 to 9.04.  There's no "open with" tab in 9.04 for folders, so I did this:

mv ~/.local ~/.local-old

Then log out and log back in.  When my .local directory was regenerated, the problem was solved.

---

### Post by testazio on 2010-06-17
Hi, same problem.
I solved removing these two files from folder .local/ inside my home directory.
.local/applications/vlc-usercustom-usercustom.desktop
.local/applications/vlc-usercustom.desktop

Regards.

Ignazio :-)

---

### Post by papacosta on 2011-01-28
> **fooman said:**
> go to places > computer

this opens the nautilus file browser.  on the left side,  click on your user name...then on the right side, *right*-click on "Desktop".

choose "properties" from the drop-down menu. click the "open with" tab and put a check next to "open folder".

hope that helps.
Thanks a million for this hint. I've been going nuts for the past hour. That was a simple, but totally effective solution.

---

