---
title: "metacity keybinding commands"
date: 2008-08-02
forum: General Help
---

### Post by hurinth on 2008-08-02
Hello. I would like to understand how to use my special keys (Natural Ergonomic KB 4000) by configuring keybindings instead of installing more software like xbindkeys.

I did alt+f2 and typed gconf_editor
Then applications>metacity>keybinding_command and global_keybindings [[COLOR="Green"](check this howto for more info)[/COLOR]](http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/)
So far I configured command_1 with this value > /usr/sbin/nautilus and assigned <Alt>a as the keybinding, but nothing happens.

I have 3 problems here:
-nautilus is not launching
-I want to provide a specific folder to be opened
-I want to replace <Alt>a with a [COLOR="DarkOrange"]special key[/COLOR] on my keyboard.

If I use System>Preferences>Keyboard shortcuts then I can see what is the hex ID of my [COLOR="DarkOrange"]special key[/COLOR], something like: 0xb7

Thanks

---

### Post by hurinth on 2008-08-02
Ok I solved 2/3 problems now

-to launch nautilus I went to keybinding_command>command_1 and gave it a value of nautilus /myfolder. This folder is now opened with keybinding <Alt>a.

Now the remaining problem is how to assign the special key. Typing the ID 0xb7 in global_keybinding>run_command_1 as the value doesn't work.

How do I get the correct value for my special keys?

---

### Post by hurinth on 2008-08-04
Answer taken from my [[COLOR="DarkGreen"]launchpad question[/COLOR]](https://answers.edge.launchpad.net/ubuntu/+question/41154):

> Last night I was able to understand the output and usage of "xev" command.

You can use your method (I wrote how I used it to verify key recognition) but you will be resctricted to the commands in that list. If you wish to open a very specific folder, not just home folder, you won't be able to do it with your method, neither run a script you wrote.

So the trick is, to understand the name of your special keys, actually the KEYSYM, that is the word we are looking for.

Run xev in a x terminal. Type a special key like button 1. A portion of the output is as follows:

KeyRelease event, serial 28, synthetic NO, window 0x3200001,
root 0xb7, subw 0x0, time 137010761, (693,138 ), root: (705,256),
state 0x10, keycode 136 (keysym 0x1008ff27, XF86Forward), same_screen YES,
XLookupString gives 0 bytes:

The third line reads "keycode 136 (keysym 0x1008ff27". This is what matters, this way we know that keycode 136, and keysym 0x1008ff27 were assigned by X to that Key.

Now, in order to use it in #gconf-editor>apps>metacity>keybinding_command / global_keybindings which was part of my original question, we have to search a nice file.

#gnome-search-tool >XKeysymDB >choose File System. The file might be under /usr/share/X11, depending in Ubuntu version. That file contains a nice list of KEYSYMS that the system recognizes. Do a search of the hex number we got bfore: :1008ff27, instead of 0x, just a colon : and once you find the line that matches the keysym we find with xev for the special key, we can then go to #gconf-editor>apps>metacity>global_keybindings and give a keybinding_command key the launcher we want.

In my case, the Ergonomic Keyboard has at least 6 buttons I didn't know their name, or keysym to enter in the global_keybinding. The xev output gave me this: keycode 131 (keysym 0x0, NoSymbol). That means keycode 131 has no name! Then we need to make the system understand something else by keycode 131 so we can tell metacity something it understands.

Type xmodmap -pke > xmodmap.conf and a file named xmodmap.conf will be created in the home folder. Open it. Locate keycode 131. It should be empty. Then take a look at XKeysymDB file and pick a name with meaning for that key. In my case I picked XF86Launch3. Type that name in xmodmap.conf at line 131. Save the file. In a terminal run xmodmap xmodmap.conf. Assign that keysym to metacity for your personalized command. Press the special key and see how your command is executed. In case it doesn't work right away, in metacity global_keybindings section, try entering a different value, like <alt>a, hit enter, erase it and then type the name XF86Launch3.

Great links to understand this answer: [http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/)

[http://ubuntuforums.org/showthread.php?t=27039&highlight=metacity+key+codes](http://ubuntuforums.org/showthread.php?t=27039&highlight=metacity+key+codes) (In Hardy Heron I didn't even have to relocate the xmodmap.conf file for linux to load it each time. Leaving it where it was created works everytime)

---

