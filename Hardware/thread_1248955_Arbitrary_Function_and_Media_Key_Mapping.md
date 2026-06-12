---
title: "Arbitrary Function and Media Key Mapping"
date: 2009-08-24
forum: Hardware
---

### Post by coolaj86 on 2009-08-24
How do I find out what device is sending a signal?
i.e. How do I know if it was a mouse button, or the keyboard, or a wacom stylus?

How do I find out what signal it is sending?

How do I remap these keys to function as other keys?

How do I remap these keys to execute a command?


I figure if I can learn the answers to the 4 questions above, I should be able to solve all of the current issues I'm listing here below on my own.


I have a button on my laptop which in windows brings up the task manager. I would like it to do the same in Ubuntu, but it brings up the shutdown menu.

Right next to that I have a D-Pad. The current mapping is:
Right: 4
Left: 3
Up: 2
Down: 1
Center (push): 5
I would like it to map to the arrow keys.

A button right next to it is supposed to rotate the screen. It prints the number 6.

I have a stylus. When I click it, it emulates a middle-click.
I'd rather it right-click.

There's an fn button on my keyboard. Some of the FN combinations work, some don't.
I'd like to remap them to specific tasks - and perhaps configure FN+A (which has no function even in windows) to bring up my calculator, or something like that.

---

### Post by Favux on 2009-08-24
Hi coolaj86,

Do you have a tablet pc?  If so which one?  Are you using Hardy?

To get the stylus buttons mapped wacomcpl is useful.  If, in Synaptic Package Manager wacom-tools is installed, in a terminal enter wacomcpl.

Generally to detect the key code you enter xev in a terminal.  The little detection box pops up.  You press the key, and somewhere in the ouput should be the key code.

For a little on binding a key for screen rotation see:  [http://ubuntuforums.org/showthread.php?p=6274392#post6274392](http://ubuntuforums.org/showthread.php?p=6274392#post6274392)

So you can find key settings in a few places like Preferences>CompizConfig Settings Manager>General>Key Bindings and Preferences>Keyboard Shortcuts come to mind.

---

