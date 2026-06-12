---
title: "Rename folders from &quot;John Smith&quot; to &quot;Smith, John&quot;"
date: 2008-08-18
forum: General Help
---

### Post by DuplexEmotions on 2008-08-18
Just like the title says, I have a bunch of folders that are sorted by name (some of which have middle names) but I prefer them in the surname, first name format.

Example: "John T. Smith" becomes "Smith, John T." and so on and so forth.

I have a lot of these folders and, for the life of me, I don't have a clue as to how to chuck together a quick bash script to do a whole folder full of these folders.

Any suggestions?

---

### Post by AndyCee on 2008-08-19
Thought I could knock something together quickly, but no avail.

Try asking in the "Development & Programming" forum. You'll get a reply quick-smart.

---

### Post by DuplexEmotions on 2008-08-19
thanks, I'll do that!

---

### Post by DuplexEmotions on 2008-08-19
Just like the title says, I have a bunch of folders that are sorted by name (some of which have middle names) but I prefer them in the surname, first name format.

Example: "John T. Smith" becomes "Smith, John T." and so on and so forth.

I have a lot of these folders and, for the life of me, I don't have a clue as to how to chuck together a quick bash script to do a whole folder full of these folders.

Any suggestions?

---

### Post by WW on 2008-08-19
This can probably be done as a "one-liner" with the **rename** command, but it would be good to make clear exactly what you want to have happen.  My understanding is this: take the longest sequence of non-whitespace characters from the end, move it to the beginning followed by a comma and a space, and remove the leftover final space.  Does that sound right?

Double check: do all the filenames have a space in them, or are there any names like "Cher" or "Madonna"?  What about something like "Balthasar van der Pol", which should probably become "van der Pol, Balthasar"?

---

### Post by DuplexEmotions on 2008-08-19
that sounds exactly right. Move the last word of the string to the front, followed by a comma. None of the folders I have are one name, and any with special rules (like your latter example) I can do by hand later. I just have a couple hundred of these folders so I'd rather not do them all by hand.

Thanks for your help thus far!

---

### Post by WW on 2008-08-19
Create a temporary directory with some dummy files and test this before using with your actual files:
```

rename 's/(.*) ([^ ]+)/$2, $1/' *

```

---

### Post by Keith Hedger on 2008-08-19
this is crudely what u want```
#!/bin/bash

find ./ -name "* *"  | while read line
do
	filename=${line:2}
	array=( $filename )
	newname="${array[2]} ${array[1]} ${array[0]}"
	mv "$line" "$newname"
done

```

u can alter "newname" to any format u like

---

### Post by DuplexEmotions on 2008-08-19
Thanks, WW. That works perfectly!

---

