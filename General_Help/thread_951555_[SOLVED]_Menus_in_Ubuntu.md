---
title: "[SOLVED] Menus in Ubuntu"
date: 2008-10-18
forum: General Help
---

### Post by Brandon81 on 2008-10-18
Okay I really need some help figuring out the menus in Ubuntu. (Meaning the application menu in the gnome panel)

In XP making a new menu item was beyond simple.

In Ubuntu it seems like the simplest things, like linking to a folder, or linking to a, for example, RDP file (remote desktop saved configuration file) that opens fine if I were to double click on it but no matter what I try to do it will not open out of a menu item. 

If I choose location and type in, for example, /menu/harddrive1/mp3, why wouldn't that work? I even tried making a link to the folder, put it in a custom folder I made specifically for links (Thinking this was the answer I was looking for), but nope, it goes to the link target with a double click or by choosing open. 

Any advice on the menus would be greatly appreciated. 

Thank you!

---

### Post by shawnrgr on 2008-10-18
[http://ubuntuguide.org/wiki/Ubuntu:Hardy#Add_a_program_to_the_Applications_menu](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Add_a_program_to_the_Applications_menu)

what is "/menu/harddrive1/mp3" ?

are you trying to plan an mp3 from your applications menu? first off /menu doesn't exist and shouldn't exist. 

please be more clear. tell us exactly what your doing and what your typing. a screenshot would be nice ;)

---

### Post by geirha on 2008-10-18
Not sure I understand what you want. Do you want to add a menu item that will open up a folder? If so, set the command to "nautilus /media/harddrive1/mp3" for instance. You need to specify that nautilus, the default file browser, should open the folder.

---

### Post by victor.zamanian on 2008-10-18
From what I understand, you want to be able to simply add general shortcuts to stuff, such as maybe a folder or a song or whatever. I just had a fiddle with the menu editor (aka 'alacarte') and it seems that no matter what I enter as "command", I'm not able to create a menu item when choosing "Location" from the drop-down menu. So don't use that.

Instead use "Application", then **enter the program with which you wish to open the location/file**, and then the location/file itself. For example:

[LIST]
[*]eog /path/to/pic/hello.png,
[*]totem /path/to/music/artist-song.ogg or
[*]nautilus /path/to/documents/
[/LIST]

Remember, use "Application". Otherwise, according to my version at least (0.11.5) things will not work well.

---

### Post by Brandon81 on 2008-10-18
I am sorry, I meant /media/ etc. 

Yes, I was looking to open a folder through a menu item. 

Additionally, I was looking to be able to open things from menus, such as an associated file. For example, even though I'm not going to be using it, how would I make a link to a file like an RDP file?

Thanks for the responses! This should help!

---

### Post by victor.zamanian on 2008-10-19
I haven't used RDP files but my guess is that you have to create a menu item of type "Application" that has the command 'rdesktop /path/to/RDP_file.rdp'. If rdesktop is the program you use to open the RDP file, of course. Otherwise replace it with whatever program you use. :-)

I apologise if I misunderstand what it is you wish to achieve.

PS. (I think) you (accidentally?) marked this thread as solved even though it seems like you hadn't gotten your answer yet. You shouldn't do that until you feel you do have a solution.

---

### Post by kingdon on 2008-12-05
I don't know if this has really been solved ...

I'm running into the same problem. I select "new item", then set the type to "location" and populate all the other fields. After doing this the item never appears in the sub menu.

Type: Location
Name: text file test
Location: file:///home/kingdon/hw-gfxcard.txt
Comment: why won't this work?

Note that I used the "browse" button to get the path to the .txt file.

I've done what victor.zamanian suggested (i.e. leaving type set to Application and pre-pending gedit), but I feel this is a work around. Otherwise, what is the point of having a location option?

I've also tried to point to a folder and have had no luck.

Any input is appreciated.

---

### Post by victor.zamanian on 2008-12-05
> **kingdon said:**
> I don't know if this has really been solved ...

I've done what victor.zamanian suggested (i.e. leaving type set to Application and pre-pending gedit), but I feel this is a work around. Otherwise, what is the point of having a location option?

I've also tried to point to a folder and have had no luck.

Any input is appreciated.

Yeah, I think the work-around is the best we've got for now. I don't know if it's a bug or if we're all doing it the wrong way (yeah right). I haven't looked for any bugs regarding this, but maybe it is filed already. I personally always go for Alt-F2 or start things from the terminal, so at least I'm alright (I'm sure that brings you some comfort ;).

---

