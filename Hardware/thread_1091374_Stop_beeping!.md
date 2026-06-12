---
title: "Stop beeping!"
date: 2009-03-09
forum: Hardware
---

### Post by kilgore9 on 2009-03-09
Hey I'm using 8.04 on a new Acer Extensa 5630Z.  I generally have no sound problems, but one thing I can't seem to control.  There is a computer "beep" that sounds at certain events, like unplugging the power cord or plugging it back in.  Also when I get an email it beeps at me.  Its not a normal ubuntu sound, but one of those sine wave computer beeps that I remember from computers of my childhood, when that was then only sound they could make.  I can't figure out how to change that annoying sound to something more pleasant or turn it off altogether.  I can't find the setting. Any help?

---

### Post by toffifeemann on 2009-03-09
got the same problem, i tried turning it off over bios but i gotta check with systemsupervisor...whom i dont know since it's a used laptop, was wondering if there was a way to stop the beeps via ubuntu

---

### Post by kilgore9 on 2009-03-09
hmm.. what is bios?  Maybe I can try that... I am my own supervisor!!

---

### Post by Dougie187 on 2009-03-09
Did you guys try anything in
System->Preferences->Sound
?

Possibly on the Sounds Tab?

There are events for "New Email", "Battery Warning" and quite a few others. You could probably just disable sounds on each event you don't want a sound for.

---

### Post by Therion on 2009-03-09
You could try what is suggested here.  I've not tried this myself so I can't confirm, just something to try:

[http://www.arsgeek.com/2006/08/23/how-to-turn-off-the-annoying-system-beep-in-linux-debianubuntu/](http://www.arsgeek.com/2006/08/23/how-to-turn-off-the-annoying-system-beep-in-linux-debianubuntu/)

---

### Post by kilgore9 on 2009-03-09
Well of course the Sound Preferences is the first place I checked.  There it does not list these things as new events...new email, unplugging power cord....none of it is listed.

But the link fixed some of the problem!  Now it doesn't beep for some of the events...deleting when there is no text is now silent, for example.  But it still does it when I plug/unplug the cord.  Waiting to get an email to see if it still does it there...

any thoughts on the power cord beep?

---

### Post by Dougie187 on 2009-03-09
What version of ubuntu are you using?

I attached a screenshot of my sound preferences.

See the options I mentioned above.

---

### Post by kilgore9 on 2009-03-09
like said, 8.04.  My sound prefs look nothing like that......

---

### Post by Dougie187 on 2009-03-09
I missed that. 

You could try this.

Press Alt+F2 and type
```
gconf-editor
```

Then navigate to
Apps/Metacity/General

And uncheck the box next to audible bell.

---

### Post by kilgore9 on 2009-03-09
thanks!  that might be a better solution than the link above, but it still doesn't get the beep from plug/unplug power cord to stop...thats also a different beep, I might add, than the beep from other apps.  

Do you know how I can get to the sound preferences like you have?  So I can add a new sound for "new email" for example?  Thanks for the help!

---

### Post by Dougie187 on 2009-03-09
I think that might be only in 8.10.

---

### Post by mtbsoft on 2009-03-09
There is [another thread]("http://ubuntuforums.org/showthread.php?t=1051220") which has been discussing this and where one guy suggested removing and blacklisting the pc speaker device driver - I'm thinking of trying that myself.

Edit: just tried it and am delighted to report that the last of the annoying beeps has now been killed.

---

### Post by kilgore9 on 2009-03-10
Yes I also tried and it worked, for everything but the plug/unplug power cord.  Now I'm trying to get a different sound to play when I get a new email, for example.  Any thoughts?

---

### Post by Korwynz on 2009-03-11
I found this on a website and it worked great for me

in console type "    **sudo rmmod pcspkr**        "

if you decide you want it back on type: "          **sudo modprobe pcspkr **    "

here is the source i got it from:
[http://lifehacker.com/software/ubuntu/hack-attack-top-10-ubuntu-apps-and-tweaks-195437.php]("http://lifehacker.com/software/ubuntu/hack-attack-top-10-ubuntu-apps-and-tweaks-195437.php")

the page has some "must have" apps and stuff including some reviews that i found quite helpful as i am a beginner user at both linux and ubuntu :)

---

