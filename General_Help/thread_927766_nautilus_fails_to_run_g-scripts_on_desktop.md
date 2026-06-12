---
title: "nautilus fails to run g-scripts on desktop"
date: 2008-09-23
forum: General Help
---

### Post by lgoster on 2008-09-23
Hi everybody,

I have a nautilus G-script that allows me to compare two files using meld. This is the script:

#!/bin/bash

if [ $# -ne 2 ]; then
  zenity --error --title "Compare with Meld" --text "You have to select only two files"
else
  meld $*
fi

And the script is located in the next folder  

/home/lgoster/.gnome2/nautilus-scripts

with the name "Compare with Meld..." (execution flags are activated).

So, if I open nautilus and select two folders or files from the window nautilus opened the script works fine. However, if I select directly two files (or two folders) from the Desktop the error message indicated ("You have to select only two files") appears. 

It seems that in the latter case the string "$*" is empty, as well as "$NAUTILUS_SCRIPTS_SELECTED_FILE_PATHS". This is not the case the files/folders are selected from the nautilus window.

I just write this message since I have not found a solution to the problem I post here, even if it seems that other people had similar problems. On some webpages I saw that this was filed as a nautilus bug (a long time ago), but the problem still remains.
 
Anyone has any ideas of what the problem is ? 

Best,

Luis

---

