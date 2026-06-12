---
title: "custom key for ibm thinkpad t30"
date: 2007-03-11
forum: Hardware &amp; Laptops
---

### Post by xnszxdotnet on 2007-03-11
Anyone figure out how to customize the thinkpad button on this ibm thinkpad t30 laptop? I would like to attach a script to it, say to open the home folder or open an app. I've been looking at the keyboard prefs but not seeing anything that would let me do something like this. 


Also, The numlock key how do you toggle it?

---

### Post by matburton on 2007-03-11
Right,

Open up a terminal and type xev and place your mouse over it.

You'' notice that anything you do gets logged in the terminal, these are all the events arriving.

So press the key that does nothing and see what happens, hopefully a key press should arrive with a keycode number.

You can use that number to bind it to a key like so:
```
xmodmap -e "keycode x = key"
```
where x is the keycode number and key is a valid keystroke, something silly like Greek_OMEGA.

Then you can hopefully set that as a shortcut elsewhere. I used this to configure those rubbish buttons on my laptop to do cool things in beryl ;)

Hope that helps!

---

### Post by xnszxdotnet on 2007-03-11
OK so I found out that the keycode is 159 so do I edit the xorg.conf file?

if so how do I do this.

xmodmap -e "keycode 159 = /home/user/"

??

or do I point it to a script that opens that folder? ie.

xmodmap -e "keycode 159 = /home/user/openhomefolder.sh"

???

---

### Post by matburton on 2007-03-11
Not quite.

You have to assign it to a key. So for instance I'm not in the habit of using the greek symbol omega too often. So I assigned one of keys to that.

To do that consistently and easily go
System Menu -> Preferences -> Sessions -> Startup Programs
And in there add 'xmodmap -e "keycode 159 = Greek_OMEGA"'
(without the first and last ' but with the "s)

Now you have to assign omega as a shortcut to your home dir.
System Menu -> Preferences -> Keyboard shortcuts
In there expand Desktop and choose Home folder ;) and set it to omega.

Hmmm actually ubuntu will probably be clever and not let you because omega is a valid letter.

Try it anyway! If in doubt try to find a list of valid key symbol name for one that you don't use.

Hope that helps, thats the jist at least!

---

### Post by matburton on 2007-03-11
Hmmm actually I may have gone overkill there!

You could try this first without any of the stuff before
System Menu -> Preferences -> Keyboard shortcuts
In there expand Desktop and choose Home folder click the shortcut and wack the useless button

This before you did the xmodmap thing.

If you did, remove it from the session options and then logout and backin.

Other programs might require a key but I dont think something this simple does.

Sorry if I confused you!

---

### Post by xnszxdotnet on 2007-03-11
Thanks it worked just fine. Thanks alot

for every one else it ended up being
0x9f 
(the useless key)

Thanks again, now I'm off to play more

---

