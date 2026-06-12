---
title: "Is it possible to configure dead key behaviour?"
date: 2008-08-15
forum: General Help
---

### Post by InspiredIndividual on 2008-08-15
For my newly acquired computer, I decided to install Ubuntu Linux. Now, I'm trying to tailor my keyboard configuration to my needs. As mentioned in the Ubuntu community docs ( [https://help.ubuntu.com/community/ComposeKey](https://help.ubuntu.com/community/ComposeKey) ), it is possible to manually edit key sequences by using the Xwindow Input Method (XIM) instead of the Gnome hard coding. Then, you can create your own set of compose keys by editing the Compose table for your locale and saving it as ~/.XCompose. The Compose table lists all key sequences that are designed to produce a certain character. For example, you can set <dead_acute><a> to return á.

However, I haven't been able to find a way to change the automatic behaviour for key sequences not listed in the Compose table. By default, pressing unlisted key sequences involving the Compose key of dead keys will return nothing.  Does anyone know how to edit this behaviour? Specifically, I would like any sequence <dead_keyA><keyB> not listed in the table to return the same as <keyA><keyB>. For example, if ' + a is listed in the table, it should return á, if it is not listed in the table, it should return 'a. 

So far, I like Ubuntu much better than the Windows XP installed on my laptop! This dead key behaviour is one of the few things left which I like better in Windows, as this is default within Windows. While being less logical, it is more efficient. It means I do not have to hit space every time I want a dead key to behave like it's not dead. I hope someone can enable me to eliminate one of the only two things I still like better in Windows... :-D

---

### Post by ellgor on 2008-08-16
Hi,

You can but try this, open a terminal and type in:

sudo dpkg-reconfigure xserver-xorg

accept the defaults when presented until you arrive at the keyboard section, there are options here to change the way the keys respond so I think this might be what you are looking for, hope this helps.

Regards, Ellgor.

---

### Post by InspiredIndividual on 2008-08-16
Thanks for your reply, however, the available options are quite limited and do not seem to include anything remotely like 'semi-dead' keys. There are two avenues I've walked so far in my search for a solution, yet without result so far. I went through the various xkb files hoping to find some clue. If I understand correctly (please correct me if I'm wrong), when a key is pressed, this returns scancode. The scancodes are mapped to keycodes, which basically means toggling between e.g. <grave> and <dead_grave> depending on the next pressed key is not possible. Thus, I see two possible solutions in theory. First possibility is modifying the way <dead_grave> behaves in general, but I haven't been able to locate the file that handles those keycodes. Second possibility is manually editing the compose sequences to return the appropriate string for all combinations <dead_key><key_without_assignment for dead key>. For clarity's sake: I mean manually editing ' + g to return the string 'r . However, I haven't been able so far to assign strings, just characters. Could there be a solution here, albeit with far too much work? Assigning strings should be possible, isn't it?

---

### Post by InspiredIndividual on 2008-08-19
After much trying and searching I feel that I'm simple not capable of solving this. From what I tried, this issue seems to be too low level for my beginning linux mind to be able to find a solution myself. I actually get the feeling the current behaviour seems to be preferred, although I have no idea why. Anyway, I'll stop directly searching for a solution and invest my time in understanding more about linux in general. Hopefully, I'll be able to return later and solve it. Still, I'll keep checking this thread in case somebody might be able to help me.

Helpful replies (I would be very pleased if someone could help me with this, to understand more, although I'll understand if nothing pops up) would include:
[LIST]
[*]Explanation why OSX behaves in the current way regarding shortcuts
[*]What files to experiment with in a search for a solution
[*]How to get the manual compose sequences in xkb to return strings instead of ASCII characters
[/LIST]

Naturally, it was folly to believe all things would be better in Linux ;-) With such capital, Microsoft should be expected to score at least a few points, although I cannot see myself switching back to Windows anymore.

---

