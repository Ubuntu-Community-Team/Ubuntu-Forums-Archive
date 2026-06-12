---
title: "underscore in nautilus file list"
date: 2008-10-06
forum: General Help
---

### Post by LoneWolfJack on 2008-10-06
in nautilus, the underscore is ignored in the context of sorting the file names alphabetically... which is kinda odd, because I have always used the underscore to mark files for various reasons so they would be shown as a block of marked files. now I always have to visually scan through the entire file list to check for underscores, which is pretty annoying.

is there any way to turn that feature off? I think this is a great example of intended usability killing practicability.

---

### Post by johandicap on 2011-03-27
Bump... I have the same problem!

Is there a setting to change somewhere so that it doesn't ignore my leading underscores when sorting by file name?

/ Johan

---

### Post by asmoore82 on 2011-03-28
This is an old and hotly contested issue.
This is regarded by some as a "bug" but it is not as it is functioning as the developers intended.

This is a bad habit on the part of the user and is a symptom of the larger problem of bad or lazy file management.
However, you can get the desired effect by prepending filenames with an underscore **and** a dot (*_.filename*).

---

### Post by johandicap on 2011-03-28
I can see that it is not a bug since it is working the way the developers intend it to. (But I don't really see the benefits of having it that way?) So I was looking for a setting or an extension or similar to change this behavior (without recompiling nautilus myself).

In my household I have a mixed environment with Mac/Windows/Linux and both Mac and Windows respect my underscores when sorting. I use it as a simple way to mark certain folders on my linux box. For instance, I have a folder called _Incoming_ in my Video folder where I temporarily put movies until I later come back and move them to their correct folder (so my media center can see them).

One might argue that it's a bad habit but I see it as an easy and robust way of organizing my files across platforms. Introducing a dot as well might be a workaround but not a very pretty one :S And I would have to go through all my data folders and rename where applicable.

If no hidden nautilus setting exist, one might be able to write a nautilus plugin that does it but this is most likely a time-consuming process.

---

