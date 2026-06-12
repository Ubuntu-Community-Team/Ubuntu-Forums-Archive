---
title: "Logitech MK300 wireless keyboard layout"
date: 2014-03-26
forum: Hardware
---

### Post by Keith_Beef on 2014-03-26
It's been a long time since I last wondered about this, but recent interest in being able to type the whole range of IPA characters has prompted me to look into the keyboard layout selector, again.

I have a Logitech MK300 wireless keyboard, I had a little bit of a problem with it back in 2010, but it's been working flawlessly since then for my work in English, French, German, Russian, Greek, even Armenian&#8230; I don't do any of the South or East Asian languages yet (other than very brief experiments with Korean for food labelling), nor do I do any right-to-left scripts yet.

But my question for now is this: where is the physical keyboard layout selector? I remember at some point, possibly during installation, having the option between PC84, PC101, PC105, Japanese, etc., the numbers 84, 101, 105 referring to the number of physical keys on the keyboard and their standard locations.

Right now, my installation of Ubuntu is set up to use PC105; I've set the left WIN key to be the compose key and added non-breaking spaces to the space bar at levels three and four.

[IMG]http://i71.photobucket.com/albums/i121/Keith_Beef/screenshots/keyboard_layout_01_zpsaf8c70e6.png[/IMG]

The slight problem is that my MK300 keyboard does not quite match the layout shown above.
The differences are that the MK300:
[LIST]
[*]does not have the key between the Shift L and the Z keys,
[*]has a single-line Enter key,
[*]has the \ key on the right-hand end of the top line of letter keys,
[*]has, to the right-hand side of the space bar, three keys marked Alt, FN and Ctrl, Alt is mapped to Level, Ctrl is mapped to Control R, but FN is not mapped to anything as far as I can tell, and the Super R and Menu shown in the layout are not physically present.
[/LIST]

[IMG]http://i71.photobucket.com/albums/i121/Keith_Beef/screenshots/logitech_mk300_wireless_desktop_zps5ff09920.jpg[/IMG]

So what I would like to do is:
[LIST=1]
[*]make the representation of the keyboard layout on the screen match the physical layout of the MK300,
[*]find a way of mapping the FN key to something useful,
[*]find a way to type all the IPA characters (or at least the most useful ones) that are currently inaccessible.
[/LIST]

Any ideas where to start?

---

### Post by gifford on 2014-03-26
Using system settings you have Keyboard under hardware and keyboard layout under personal. I think it is a good place to start as there are a number of options you can set.

---

### Post by Keith_Beef on 2014-03-26
> **gifford said:**
> Using system settings you have Keyboard under hardware and keyboard layout under personal. I think it is a good place to start as there are a number of options you can set.

Thanks, Gifford, but I know that already. I can't find any settings there to set the physical keyboard layout.

---

### Post by gifford on 2014-03-27
Here are some threads that might help:[http://ubuntuforums.org/showthread.php?t=1968980](http://ubuntuforums.org/showthread.php?t=1968980) and [http://askubuntu.com/questions/153115/how-do-i-change-the-system-default-keyboard](http://askubuntu.com/questions/153115/how-do-i-change-the-system-default-keyboard)

---

### Post by Keith_Beef on 2014-03-27
Thanks, this bit may well be of some help.


from [http://askubuntu.com/questions/153115/how-do-i-change-the-system-default-keyboard](http://askubuntu.com/questions/153115/how-do-i-change-the-system-default-keyboard)
> 
Firstly, see that they all fall under us. Now edit /etc/default/keyboard and change this

XKBMODEL="pc105"
XKBLAYOUT="us"
XKBVARIANT="intl"
XKBOPTIONS=""


It doesn't fix my question of showing a specific physical layout for the MK300, but it's a start.

The rest is just a rehash of the regional setup that I've already known forwards, backwards and sideways for about the past five years.

---

