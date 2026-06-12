---
title: "How to make a script"
date: 2008-08-02
forum: General Help
---

### Post by t4ggs on 2008-08-02
Hi ubunteros!

I want to make this script:
#!/bin/bash
gconftool-2 -s /desktop/gnome/peripherals/keyboard/kbd/options -t list --list-type=string "[]"
gconftool-2 -s /desktop/gnome/peripherals/keyboard/kbd/options -t list --list-type=string "`echo -e "[grp\tgrp:alt_shift_toggle]"`"

How do a make it, and also how do a make it to run at startup??

thanks in advantage!

---

### Post by Claus7 on 2008-08-02
Hello!

in order to create the script, open with your favourite text editor a file, and then copy - paste the commands you have in your post. Save and quit.

Example : For vi editor type
vi gconftool.sh
then hit the button insert and click paste (you have already copied your commands)
then type Esc -> :wq!

In order to make the gconftool.sh executable type :
chmod 755 gconftool.sh

In order to make it executed at startup go there :
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Forums_FAQ#How_can_I_make_Ubuntu_execute_a_script_or_program_at_startup.3F](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Forums_FAQ#How_can_I_make_Ubuntu_execute_a_script_or_program_at_startup.3F)

It is very comprehensive on how you will be able to achieve it. This page has also other helpful information.
EDIT:Sometimes it opens a little bit difficult, yet it opens! With this link I think that you should have no trouble.

Regards!

---

### Post by t4ggs on 2008-08-02
man i didnt understand a word of what u said///whay is a vi editor type??

i just have to open the text editor and save the text without any file type?
then what?

---

### Post by geirha on 2008-08-02
Make sure it has execute permissions. Either with a temrinal command: ```
chmod +x your-script
``` or by right-clicking it, selecting properties, and add execute permission in the permission tab.

Then add it as a startup-program with System -> Preferences -> Sessions

---

### Post by Claus7 on 2008-08-03
Hello,

in windows there is word, wordpad, notepad, e.t.c.. Just open a text editor. Something that you want to write text. Go to Applications -> Accessories -> Text Editor if it is easier for you.
There, write the commmands you want line by line. Save the file with the name of your choice.
The name of the script doesn't have any special meaning. As far as you make it executable it doesn't matter. It only helps you to distinguish it form other files. Also if you make it executable, its colour would be green. Usualy the scripts have the ending "sh".
If you want to test it, you just have to open a terminal to the location you have saved the file and type : ./name_of_the_executable 
(where the name of the executable is the one you have given yourself, when you saved the file).

I hope this is clear,
Regards!

---

### Post by t4ggs on 2008-08-03
yes thans i did it...and i try the script and it works.. i also added it to the startup items under sessions, but it doesnt execute automatically.

---

### Post by Claus7 on 2008-08-03
Hello,

in ubuntu gutsy for example in sessions there is a tab that says startup programs. There you have to give the path to where your script is and not only the name. So, in the command option, you have to give the full path. For example, if the script is in your Desktop you have to type : /home/"your_user_name"/Desktop/"name_of_the_script", substituting the inhalt of " " with yours (and removing the " "). Just in case you haven't checked that.

Regards!

---

### Post by t4ggs on 2008-08-04
Check this...still the script is not running at startup...and i have to open it manually each time i start the computer..

why?

maybe there is something happening at startup that make the script not to work?

maybe i shoul put a delay and if so how do i do it?

---

### Post by geirha on 2008-08-04
Based on that screenshot, it looks correct. One thing that struck me though, is that maybe whatever gnome application is setting the wrong value for you, is starting _after_ your script. Try adding the following line to the end of your script

```
echo "$(date) Script ran" >> ~/keyboard.log
```

The next time you boot, check if you have a new file in your homedirectory called keyboard.log.

Also, is the values you need to set not possible to set using System -> Preferences -> Keyboard ?

---

### Post by derrick81787 on 2008-08-04
> **t4ggs said:**
> Check this...still the script is not running at startup...and i have to open it manually each time i start the computer..

why?

maybe there is something happening at startup that make the script not to work?

maybe i shoul put a delay and if so how do i do it?

Are you sure you made it executable?  If you didn't make it executable, then it won't run. To make it executable, open a terminal and type:

```
chmod +x keyboard
```

That should make it work.  If, for some reason, you don't want to do that, you could change the command for the startup program from "/home/ytaggs/keyboard" to "sh /home/ytaggs/keyboard".  The "sh" command will run a shell script even if it isn't executable.

I hope this helps.

- Derrick

---

