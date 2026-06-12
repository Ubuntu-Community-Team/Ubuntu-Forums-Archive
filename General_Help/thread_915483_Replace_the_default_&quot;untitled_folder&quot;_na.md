---
title: "Replace the default &quot;untitled folder&quot; name."
date: 2008-09-09
forum: General Help
---

### Post by iaculallad on 2008-09-09
Is there a way for me to automatically replace the name "untitled folder" whenever I right-click and select "Create Folder"? Could it be possible to replace the name to the current date of the day?

> Say: 
Instead of the default name "untitled folder", it will automatically be named to "2008-09-10". If it has the same name on the parent folder, it would be automatically named as "2008-09-10 1".

---

### Post by kerry_s on 2008-09-09
i think it would be easier to make a nautilus script.

```
mkdir `date '+%m%d%y'`
```

opp's, sorry forgot the dash's

```
mkdir `date '+%m-%d-%y'`
```

---

### Post by iaculallad on 2008-09-09
Thanks for the reply. I did try using a script but what I want is to directly change the default from using "untitled folder". Or is there a way to integrate the script with the "Create Folder" option on the right-click?

---

### Post by Ripfox on 2008-09-09
This is a really interesting idea...if you accomplish it please share the nautilus script!

---

### Post by kerry_s on 2008-09-09
> **Ripfox said:**
> This is a really interesting idea...if you accomplish it please share the nautilus script!

huh, it's simple. see pic

---

### Post by mc4man on 2008-09-09
I don't know how to edit XML but maybe in here is where it's controlled?

file:///usr/share/nautilus/ui/nautilus-directory-view-ui.xml

---

### Post by iaculallad on 2008-09-10
> **mc4man said:**
> I don't know how to edit XML but maybe in here is where it's controlled?

file:///usr/share/nautilus/ui/nautilus-directory-view-ui.xml

Thanks for the suggestion but it's not there, tried searching the other *xml files for the option on "Create Folder" but can't find one. Any other ideas?

---

### Post by kerry_s on 2008-09-10
> **iaculallad said:**
> Thanks for the suggestion but it's not there, tried searching the other *xml files for the option on "Create Folder" but can't find one. Any other ideas?

did you try the script? 
a little looking around tells me the option your wanting to change is hard coded.

perhaps you just need more detailed instructions?

press alt+f2
type> gedit ~/gnome2/nautilus-scripts/dated-folder
(you can change the name by the way, it doesn't have to be dated-folder)

put:

```
#!/bin/sh
mkdir `date '+%m-%d-%y'`

```

press alt+f2 again or in a terminal
type> chmod +x ~/gnome2/nautilus-scripts/dated-folder

---

### Post by iaculallad on 2008-09-10
> **kerry_s said:**
> did you try the script? 
a little looking around tells me the option your wanting to change is hard coded.

perhaps you just need more detailed instructions?

press alt+f2
type> gedit ~/gnome2/nautilus-scripts/dated-folder
(you can change the name by the way, it doesn't have to be dated-folder)

put:

```
#!/bin/sh
mkdir `date '+%m-%d-%y'`

```

press alt+f2 again or in a terminal
type> chmod +x ~/gnome2/nautilus-scripts/dated-folder

Actually I already did that before (that was what I'm using until I taught of this idea), the use of a script to handle the task I wanted (Of naming the folder to the current date). What I want to know is: If there's a way of either integrating the script I am using to the "Create Folder" option or a way in w/c to edit it's default value of "new folder". Or a (nautilus) tweak maybe that instead of using the script to change the way on which it names a new folder created.

---

### Post by mc4man on 2008-09-10
I'd think you'd need to create a nautilus extension solely for that. The script would be good if it appended to end in case of existing same name (though once a day per dir. seems sufficient 

as far as the "untitled folder" name

from a past changelog

> * src/file-manager/dfos-xfer.c: 
	(fs_new_folder):
	Changed to use "untitled folder".



and the source

> . localizers: the initial name of a new folder
#: ../libnautilus-private/nautilus-file-operations.c:2422
msgid "untitled folder"
msgstr "untitled folder"


---

