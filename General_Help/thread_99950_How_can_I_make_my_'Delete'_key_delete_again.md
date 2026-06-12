---
title: "How can I make my 'Delete' key delete again?"
date: 2005-12-06
forum: General Help
---

### Post by Stickymonk on 2005-12-06
Hi all, my first post on these forums, and its a plea for help I'm afraid.

I'm very new to this Linux lark, and am learning by messing around with things that I dont understand. I found a short tutorial to enable ctrl+alt+del functionality, but I've discovered that all that it does is open System Monitor when I press delete. I'm finding this to be very frustrating since I actually like to use my delete key for deleting things. The code I used to enable this was...

gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "Delete"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"

Any ideas how I can make delete work as it should again?

Thanks in advance!

---

### Post by canadianwriterman on 2005-12-06
Actually, I've suddenly lost the functionality of my delete key, too. It happened after installing Automatix. Originally, I installed almost everything available in Automatix (including the CTL-ALT-DEL function), but I had some serious system freeze issues after installing. I ended up reinstalling Ubuntu completely. After that, I reinstalled Automatix, but only used it to install a few things that I was more familiar with. I don't believe I installed the CTL-ALT-DEL program on the second round. It was then that I discovered that my delete key now does nothing.

---

### Post by bunty on 2005-12-06
man gconftool ??

---

### Post by Stickymonk on 2005-12-07
Say what? Does anyone have a solution to this that can be understood by a linux idiot like myself? I just want delete to delete again! :(

---

### Post by hentaidan on 2005-12-07
This should work:

1) Open up the configuration editor, (its under Applications | System Tools)
2) Click your way through the trees ("apps", then "metacity", then "global_keybindings"
3) In the right hand pane you should now have a long list of names & values. Further down you should see "run_command_1", "run_command_2" etc. (to 12 on my machine) Mine are all set to (there value that is) disabled (I have no keybindings set up).
4) Find "run_command_9" and double click on it. Change the value to disabled.
5) Then click on "keybinding_commands" in the left hand pane and double click on command_9 and delete the value (should be gnome-system-monitor) and leave it blank.

Basically what you did was told linux to run the gnome-system-monitor every time you press the delete key. What we do here is remove the variable that you set.

gconftool (the configuration editor is the GUI for gconftool) is similar (IMHO) to the windows registry; it stores settings etc.

bunty was suggesting that you read the manual page for gconftool (by typing man **gconftool-2** into a terminal window). I would recommend this if you dont know what the command that your typing does ;-)

---

### Post by Stickymonk on 2005-12-08
This worked a treat... thank you!!

---

