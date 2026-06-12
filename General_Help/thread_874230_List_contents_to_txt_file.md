---
title: "List contents to txt file"
date: 2008-07-29
forum: General Help
---

### Post by underground on 2008-07-29
Hello..
I know already how to list folder contents to a txt file...but i want to know to know if there is any nautilus script or i can someway integrate an option to right click menu??

Actually i want to right click a folder and choose the option to list contents to a file...how can i do that??

Please help me..

---

### Post by Diabolis on 2008-07-29
Create a script in this location: **.gnome2/nautilus-scripts/*ls script***

Make it executable:
```
chomd +x .gnome2/nautilus-scripts/*ls script*
```

The content of the scrip would look similar to this:
[PHP]
#!/bin/sh

file='~/Desktop/folder'
for path in NAUTILUS_SCRIPT_SELECTED_FILE_PATHS; do
	ls $path>>$file
done
[/PHP]

I'm not very good at scripting yet. So that is not fully working.

You can find some already written here: [http://g-scripts.sourceforge.net/](http://g-scripts.sourceforge.net/)

---

### Post by DagMan on 2008-07-29
```
#!/bin/bash

cd "$1"
x=`ls`
echo $x > ~/contents.txt
```
this would change directory to the folder, then spit the contents of the command ls to the file contents.txt in your home folder.

this one is prettier
```
#!/bin/bash
echo '' >  ~/contents.txt
cd "$1"
for i in * ; do
echo $i >> ~/contents.txt
done
```

Edit:  I'm a slow typer

---

### Post by Diabolis on 2008-07-29
Oh, yeah!

This works wonderful

[PHP]
#!/bin/bash
echo '' >  ~/Desktop/contents.txt
cd "$1"
for i in * ; do
echo $i >> ~/Desktop/contents.txt
done[/PHP]

---

### Post by mosty friedman on 2008-07-29
hmm i dont really know about the right click thing..but if you open the terminal and type
```

ls -"name of folder"

```
the contents of the folder will be listed..make sure that you are in the directory where the folder is located

---

### Post by Diabolis on 2008-07-29
> I know already how to list folder contents to a txt file

cough cough

---

### Post by ibuclaw on 2008-07-29
> **Diabolis said:**
> Oh, yeah!

This works wonderful

[PHP]
#!/bin/bash
echo '' >  ~/Desktop/contents.txt
cd "$1"
for i in * ; do
echo $i >> ~/Desktop/contents.txt
done[/PHP]

```

#!/bin/sh
cd "$1" && cat > ~/Desktop/contents.txt << EOF
`ls`
EOF

```
:D

---

### Post by Diabolis on 2008-07-29
> **tinivole said:**
> ```

#!/bin/sh
cd "$1" && cat > ~/Desktop/contents.txt << EOF
`ls`
EOF

```
:D

oh! nice, same thing with less text. :guitar:

---

### Post by braddcadd on 2008-07-29
Looks like the best way to do this is to use the script functionality of nautilus.

From a terminal:
```

sudo aptitude install nautilus-script-manager
touch ~/.gnome2/nautilus-scripts/listem.sh
chmod 755 ~/.gnome2/nautilus-scripts/listem.sh

```

Inside this file:
```

#!/bin/bash -x
ls -lt $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS >> /home/brad/test.txt

```

Now right click on a folder in nautilus ans notice your script.  Try it out!  Good luck.

---

### Post by Diabolis on 2008-07-29
Seems like we got a scripting competition in here.

Thanks for posting this script examples.

---

### Post by ibuclaw on 2008-07-29
Seems that we are missing a decent one-liner though...
```
find $PWD -maxdepth 1 -print | sort > ~/Desktop/contents.list
```
Or if you don't want the "/home/username" part in the list...
```
find $PWD -maxdepth 1 -print | sort | rev | cut -f 1 -d '/' | rev > ~/Desktop/contents.txt
```

[EDIT]
May need to replace "$PWD" with "$1", as I've noticed in some examples here...
I've never used nautilus scripts before, so I wouldn't know...

Regards
Iain

---

### Post by Diabolis on 2008-07-29
haha great! It looks very hackish for such a simple task. :lolflag:

---

### Post by kaibob on 2008-07-29
> **underground said:**
> Hello..
I know already how to list folder contents to a txt file...but i want to know to know if there is any nautilus script or i can someway integrate an option to right click menu??...
You can assign any of the numerous scripts in this thread to the right-click menu by way of the Nautilus Actions extension:

[http://www.grumz.net/index.php?q=taxonomy/term/5/9](http://www.grumz.net/index.php?q=taxonomy/term/5/9)

You apparently know about Nautilus scripts, and that is an alternative way to get the script on the right-click menu.

---

### Post by 3rods on 2008-07-29
I like it. 

Would be better if it wrote to a temp directory to be flushed out later and opened it self in gedit or similar... :P

---

### Post by underground on 2008-07-30
> **tinivole said:**
> ```

#!/bin/sh
cd "$1" && cat > ~/Desktop/contents.txt << EOF
`ls`
EOF

```
:D
> **Diabolis said:**
> Oh, yeah!

This works wonderful

[PHP]
#!/bin/bash
echo '' >  ~/Desktop/contents.txt
cd "$1"
for i in * ; do
echo $i >> ~/Desktop/contents.txt
done[/PHP]

I tried them but when i right click a folder in Desktop the contents of Desktop is being listed in the file..not the contents of the folder...i have to navigate inside the folder to do what i want...also..if i choose another folder to list contents the txt file is rewritten...it doesn't keep the old list...

> **braddcadd said:**
> Looks like the best way to do this is to use the script functionality of nautilus.

From a terminal:
```

sudo aptitude install nautilus-script-manager
touch ~/.gnome2/nautilus-scripts/listem.sh
chmod 755 ~/.gnome2/nautilus-scripts/listem.sh

```

Inside this file:
```

#!/bin/bash -x
ls -lt $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS >> /home/brad/test.txt

```

Now right click on a folder in nautilus ans notice your script.  Try it out!  Good luck.
This one works perfect...all the folders i choosed to list where all listed in the file...one after another...

Anyway thank you all very much for your work...i am happy that you helped me...
By the way where can i learn shell scripting??Is there any book??

---

### Post by Diabolis on 2008-07-30
Google is your friend:

[http://www.google.com/search?hl=en&q=shell+scripting+tutorial&btnG=Google+Search](http://www.google.com/search?hl=en&q=shell+scripting+tutorial&btnG=Google+Search)

---

