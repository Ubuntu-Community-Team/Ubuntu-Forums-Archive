---
title: "How do i (re-) assign the Buttons of my TabletPC"
date: 2007-04-27
forum: Hardware &amp; Laptops
---

### Post by schmolch on 2007-04-27
Hello everybody,

i have a Tablet-PC (Thinkpad X60T) that has some additional buttons on the screen which would be very usefull when the device is in tablet-mode where you have no keyboard available.

What i already know about this topic is that u use the command setkeycodes to assign keycodes to those buttons/keys that do not have a keycode already.
Then you use xmodmap to assign a "real" command or function to that new keycode.

Is this correct?

The first question that remains though is what to do if my Buttons already have a keycode assigned that i do not want, like some do Page-Up / Page-Down out-of-the (Ubuntu) box but i would like it do something else.

Second question is what do i do if a button does not get recognized at all and there is nothing showing up in dmesg when i press them?


Thanks in advance
schmolch

---

### Post by raja on 2007-04-27
Use ```
xev
``` to check if a key is recognised and what its keycode is. Then use ```
xmodmap -pk
``` to look at the keymap table. If nothing important is assigned to it, you can remap it.

---

### Post by schmolch on 2007-04-27
Well, as i said the buttons are either NOT recognized at all or are already assigned a keycode of a key on the keyboard, if i would reassign this the key on the keyboard would be re-assigned too.

So how do i solve that?

---

### Post by raja on 2007-04-27
Sorry - I cant understand what you are trying to say. 
If you use 'xev' and then press the key, you can see in the terminal if the key is recognised. You can find the keycode which is a number. This number is mapped to a function in the keymap and you can remap it. 
For example, my X40 has the 'forward' and 'reverse' buttons. They were recognised (had a keycode), but were not mapped to anything useful. So i mapped them as F13 and F14 and assign those as keyboard shortcuts for something useful.

---

### Post by schmolch on 2007-04-27
There are 2 different issues:

Some keys are not recognised, meaning xev does not report anything if i press them.

Those 2 Keys that are recognized have the keycode 99 and 105. Now this is the same keycode of Page-Up and Page-Down on the keyboard.
If i assign a new function to 99 and 105 with xmodmap i lose the Page-Up/Page-Down Keys on my keyboard as well.

---

### Post by raja on 2007-04-27
OK. So the keys on the screen share the keycode with the pgup/pgdown keys on the keyboard and so you cannot map them? In that case, maybe there is nothing else you can do. For the other keys, I dont know if 'tpb' may help.

---

### Post by schmolch on 2007-04-27
No, it worked fine in Gentoo-Linux, all keys were recognized and none had shared keycodes with the keyboard. I also did not require tpb which when i run it now just kills the recognition of all keys.

The whole situation how to configure buttons in linux is a big pile of sh*t, and i am not blaming anyone or anything but thats how it is, i dont think anybody who ever had to waste his time with this crap would disagree.

---

### Post by schmolch on 2007-04-27
I have no idea why, but suddenly after a reboot all the keycodes of those buttons changed, none shared and all buttons included.

...

---

### Post by raja on 2007-04-27
So, is the problem solved?

I was just going to suggest trying 'showkey' and 'setkeycode'.

About your frustration, my viewpoint is that in linux atleast there is always a way to do things. Nothing is impossible, if you are willing to spend time and learn.. and you do end up learning a lot when you solve a problem.
On the other hand with windows, apart from rebooting, there is very little you can do if something doesnt work. And you never learn anything. 
Just my opinion.

---

### Post by schmolch on 2007-04-27
Yes its solved, thx for your help.

About my frustration, im not a Windows to Linux convert that is frustrated by the use of command line, but im tired of "learning" things i dont want to learn because they dont have any use except that you are forced to learn them to get your Hardware working.
Learning some bash scripting would be completely different and very usefull, learning which tools i have to use and how their syntax works to get buttons working on my Latptop is not usefull at all IMHO, it just wastes our time and i hope there will be a nice GUI in 2 years (you see im not naive by saying 2 months ;-)).
I have not used Windows in 10 years and even on my Tablet-PC i use Linux while Vista offers excellent Handwriting recognition, evewn speech recognition (but sucks on everything else, especially a fast UI, and i have a CoreDuo with 2GB RAM).

Well, on to the next issue, for some reason acpi is not listening to my events in ubuntu...

---

### Post by DagMan on 2007-04-27
Which events?  If it's using your extra keys then it's finding those events.  If it knows when you battery cable is plugged in or not then it's finding that event.

[http://www.gentoo.org/doc/en/power-management-guide.xml](http://www.gentoo.org/doc/en/power-management-guide.xml) may be helpful... if you knew bash scripting, but I think it may still walk you through enough.

start with seeing if there's any output from the events you mention using this and doing stuff
tail -f /var/log/acpid | grep "received event"

If you get output from an event then it can be tied to an action that you specify.

Edit: I'm looking at that guide again and it may be a little daunting for someone who doesn't know bash.  It really isn't as hard as you might think to set things up if you indeed get any output from things when doing the above.  I'm a bit confused though, what exactly is it that you don't have?

---

### Post by schmolch on 2007-04-28
No i was saying it wrong, acpid gets all events fine, i just have that issue where my scripts in /etc/acpid/events are not getting executed.

[http://ubuntuforums.org/showthread.php?t=418436](http://ubuntuforums.org/showthread.php?t=418436)

---

