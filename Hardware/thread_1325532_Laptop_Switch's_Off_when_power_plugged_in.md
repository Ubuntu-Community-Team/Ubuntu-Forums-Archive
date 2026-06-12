---
title: "Laptop Switch's Off when power plugged in"
date: 2009-11-13
forum: Hardware
---

### Post by th081 on 2009-11-13
Hello

I upgraded to the latest version of Ubuntu since when my Fujisu Amilo laptop shuts down if i am using it on battery and plug in the charger or am using it on charger and unplug the charger.

I say shuts down but it goes to a black screen the power still seems to stay on, this only started happening since the upgrade.

Any idea's

Thanks in advance

---

### Post by jjayr41 on 2009-11-13
I get the same thing with 9.10 karmic. My netbook doesn't shut off but does go into a hibernate mode when I plug in the charger. I just have to wake it up and it's fine. A tad annoying though...

---

### Post by th081 on 2009-11-13
With mine i can't seem to get it back without holding down the power button, it was ok in the previous version

---

### Post by Fizzasist on 2011-03-24
Mine too!

Annoying because I have to turn it back on....seems to do it whenever there is a change in the "power state"....if it is already plugged in and I unplug the power, it hibernates and if it is not plugged in and I plug in the power it goes to hibernate too....

any ideas on this??

---

### Post by na5h on 2011-10-31
Don't know if this thread is active anymore...but I'm gonna reply anyway. Does the computer say something about low battery just before it hibernates? In that case, this might do the trick: Press Alt+F2 and run "gconf-editor". Go to apps->gnome-power-manager->general and uncheck "use_time_for_policy".

---

### Post by Fizzasist on 2011-10-31
For me, the battery can be fully charged and it will still do it. It even does it when I REMOVE the power cord after charging all day.....so it seems to be unrelated to the amount of battery life and more related to a change in the "power state".

It hibernates when power is plugged in or unplugged regardless of the battery life....weird huh?

---

### Post by na5h on 2011-10-31
Try the fix I mentioned above (it's easy to undo if it doesn't work...you just check the "use_time_for_policy" box again). I used to have the same problem on my Fujitsu Siemens Amilo laptop. The computer would hibernate regardless of battery state as soon as I unplugged the power cable. For some reason the computer thought that I had like 1 minute of battery power left even though the battery was fully charged (and even though the indicator showed that it was fully charged). Unchecking the "use_time_for_policy" box solved my problem.

---

### Post by Fizzasist on 2011-10-31
Bummer.....it was already unchecked.

:(

---

### Post by na5h on 2011-11-01
Try opening the gconf-editor again and go to apps->gnome-power-manager->actions. Set all the keys to "nothing" (right click->Edit Key, then write the word "nothing" without quotes in the text area...don't leave it blank). After this, the computer should not be able to suspend nor hibernate regardless of any changes in battery state or actions such as closing the lid. Remember to write down the previous values so that you can change it back to the way it was.

---

### Post by Fizzasist on 2011-11-01
No change.....still does the same thing :(

---

### Post by na5h on 2011-11-02
Check out this page [http://linuxexpresso.wordpress.com/2010/05/09/disable-suspend-and-hibernate-ubuntu/](http://linuxexpresso.wordpress.com/2010/05/09/disable-suspend-and-hibernate-ubuntu/) to get instructions on how to disable suspend/hibernate. It's the same method as marshalium's solution in [this]("http://ubuntuforums.org/showthread.php?t=1305081") thread. I hope it solves the problem!

---

