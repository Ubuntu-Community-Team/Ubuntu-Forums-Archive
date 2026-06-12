---
title: "How can I zip files?"
date: 2008-11-11
forum: General Help
---

### Post by alexeix on 2008-11-11
Hi,

Is there a zip utility with a GUI?

I need to zip some mpg files and can't find how to do it.
Thanks.

---

### Post by ju2wheels on 2008-11-11
Right click on the file and click on the "create archive" option.

If you want to create or unzip a rar then you will need to install rar and unrar:
```

sudo apt-get install rar unrar

```

---

### Post by alexeix on 2008-11-11
I already tried right-clicking on the files, but 'create archive' isn't available as an option.

I'm actually running Mythbuntu, but will that make a difference?

---

### Post by bodhi.zazen on 2008-11-11
Install Archive manager or File roller :)

---

### Post by alexeix on 2008-11-11
I've added the thunar-archive-plugin, but no difference.

You know, I've come to love Ubuntu over the last few months, but at times like this, things do seem to be a lot more difficult...

(invites flaming)

---

### Post by ju2wheels on 2008-11-11
Honestly, thats part of Ubuntu by default so I would assume its because you are using Mythbuntu customized that its not in there (also not sure if its automatically part of KDE since I use Gnome).

```

sudo apt-get install file-roller

```

---

### Post by alexeix on 2008-11-11
Yep, I tried it on vanilla Ubuntu 8.10 and the option to create archive files was there.  

My mistake!  

So I'm past that problem, but it didn't help me reach my end goal. :(

I want to convert some .mpg files to .avi, so I can stream them to my Xbox.  WinFF doesn't seem to work on Intrepid, so I was trying to compress the files, put them on a USB stick and then convert them on my Vista box.
Long winded and unfortunately the software didn't like the files anyway...

But that's another post.

Thanks for the assistance - it's a great community. :)

---

### Post by ju2wheels on 2008-11-11
Give avidemux a try.

---

### Post by alexeix on 2008-11-12
Tried Avidemux, but when I try to convert from mpeg to avi, I get the following error (when saving as, e.g. Heroes.avi):

"incompatible output format".

---

### Post by tecknomage on 2009-07-03
> **alexeix said:**
> Hi,
 
Is there a zip utility with a GUI?
 
I need to zip some mpg files and can't find how to do it.
Thanks.
 
 
Looking at this thread, the answers, NO one answered Alexeix's question.
 
I would also like a **[COLOR=red]GUI[/COLOR] Compression Utility** (*ZIP, TAR, RAR, etc.*), **NOT Command Line**. (*compress/uncompress functions*)
 
It there one for **Ubuntu 9.04**?

---

### Post by credobyte on 2009-07-03
zip archive can be made trough Archive Manager ( edit top panels main menu and under accessories, add Archive Manager ( check it ) - by default it's invisible ).

---

### Post by Chronon on 2009-07-03
> **tecknomage said:**
> Looking at this thread, the answers, NO one answered Alexeix's question.
 
I would also like a **[COLOR=red]GUI[/COLOR] Compression Utility** (*ZIP, TAR, RAR, etc.*), **NOT Command Line**. (*compress/uncompress functions*)
 
It there one for **Ubuntu 9.04**?

I guess you ignored bodhi.zazen's post, then. Maybe make sure you read all posts before breaking out the bold text and caps. ;)

---

