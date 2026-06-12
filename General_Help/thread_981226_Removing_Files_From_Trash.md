---
title: "Removing Files From Trash"
date: 2008-11-13
forum: General Help
---

### Post by Bahb on 2008-11-13
So I just made a really dumb mistake and moved the contents of my home folder to Trash... I attempted to simply move them back to my home folder, but It turns out my music is in there, and since I have not yet emptied the trash, I do not have space to copy it back over, What do I do Ubuntu Forums?
Please Ubuntu Forums, you are my only hope.

---

### Post by Bahb on 2008-11-13
Danger Ubuntu Forums, Danger! Danger!

---

### Post by AllanPoe on 2008-11-13
Can't you copy them to a USB flash drive?

---

### Post by bodhi.zazen on 2008-11-13
Free up disk space, use the command line ...

rm == delete

Or , in the trash, delete / restore individual files.

Or, use an external media such as flash drive or CD/DVD.

---

### Post by Bahb on 2008-11-13
i cant free up disk space, the things that are taking up disk space are in the trash already...

i have a 100gb partition for a home folder, my music collection alone is 53 gb and is sitting in my trash... i cant restore it because i do not have 53 gb in my home folder, because it is already taken up by my music, even though my music is in the trash.

---

### Post by snova on 2008-11-13
Can you sort the items in the Trash by deletion date? This would help to find the older files in the Trash that *are* safe to delete. Then remove them to free up some space.

---

### Post by Bahb on 2008-11-13
Yes I could, but my music folder alone is still more than half of the space in the folder, I cant restore it without deleting it. 

100gb - 53gb = 47gb

47gb < 53 gb

therefore my music is stuck in the trash, how do i fix this.

---

### Post by bodhi.zazen on 2008-11-13
You will have to manually delete what you do not want, and then restore what you wish to keep.

47 Gb is a huge amount of space, Ubuntu probably takes up no more then 7 Gb = 40 Gb of space.

You will have to do this one step at a time ;)

---

### Post by Bahb on 2008-11-13
Why can't i just un trash them? why is there no functionality for this?

---

### Post by fballem on 2008-11-13
I'm not sure this will work, but ...

1/ Open Nautilus to your home folder
2/ Unhide the hidden folders (Ctrl-H)
3/ Locate the .local folder and click on it.
4/ Within the .local folder, locate the share folder and click on it.
5/ Within the .local\share folder locate the Trash folder and click on it.
6/ Within the .local\share\Trash folder locate the files folder and click on it.
7/ If all goes well, then these should be the folders and files that you deleted. You should be able to drag the files and folders back to their proper location. For example, if you have a Music folder in trash, then drag it to your home (on the left part of the panel).
8/ In my tests, this was instantaneous and worked very reliably. The fact that it was instantaneous suggests that it is not making a copy - but only moving a directory entry (to use old windows terminology).

I have attached two screenshots - one showing my Music folder in Trash (yes, I did delete it) and the second showing the effect after I dragged it to the folder named 'fballem', which is my home directory on my machine.

Sorry if the instructions are basic, but I find step by step easier to follow myself and I hope that you do to.

Hope that this helps,

---

### Post by Bahb on 2008-11-13
> **fballem said:**
> I'm not sure this will work, but ...

1/ Open Nautilus to your home folder
2/ Unhide the hidden folders (Ctrl-H)
3/ Locate the .local folder and click on it.
4/ Within the .local folder, locate the share folder and click on it.
5/ Within the .local\share folder locate the Trash folder and click on it.
6/ Within the .local\share\Trash folder locate the files folder and click on it.
7/ If all goes well, then these should be the folders and files that you deleted. You should be able to drag the files and folders back to their proper location. For example, if you have a Music folder in trash, then drag it to your home (on the left part of the panel).
8/ In my tests, this was instantaneous and worked very reliably. The fact that it was instantaneous suggests that it is not making a copy - but only moving a directory entry (to use old windows terminology).

I have attached two screenshots - one showing my Music folder in Trash (yes, I did delete it) and the second showing the effect after I dragged it to the folder named 'fballem', which is my home directory on my machine.

Sorry if the instructions are basic, but I find step by step easier to follow myself and I hope that you do to.

Hope that this helps,

/hug 
tnx very much

---

### Post by fballem on 2008-11-13
If that fixed your problem, then please don't forget to mark the thread as solved. This can be done using the Thread Tools at the top of the page.

And you're welcome!

---

