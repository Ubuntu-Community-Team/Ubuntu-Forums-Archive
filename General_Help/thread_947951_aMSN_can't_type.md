---
title: "aMSN can't type?"
date: 2008-10-14
forum: General Help
---

### Post by Tryfon on 2008-10-14
Hello everyone. I've been using aMSN for a while and suddenly, I am not sure after what exactly, something weird started to happen. Every time I type in a window and something new happens in aMSN I can't type anymore! I have to minimize the window and bring it to focus again and **hope** to be able to type again. Sometimes I have to restart aMSN to make it typeable again. Any clue?

---

### Post by Claus7 on 2008-11-24
Hello - &#935;&#945;&#943;&#961;&#949;&#964;&#945;&#953;!

I really won't be any great help to you. I haven't faced any similar problem before. What I can advice you if your are still using it, is to unistall it and install it back again. 

Undoubtedly as you describe the problem it seems that it has to do with amsn. 
Do you still have the same problem? In some versions of amsn there were problems with memory leaks, so an update to a newer version wouldn't be bad.

If you are confident enough you can check this out also:
[http://ubuntuforums.org/showpost.php?p=4851276&postcount=3](http://ubuntuforums.org/showpost.php?p=4851276&postcount=3)

Regards, &#935;&#945;&#953;&#961;&#949;&#964;&#953;&#963;&#956;&#959;&#973;&#962;!

---

### Post by macabro22 on 2008-11-26
This happens to me as well.

---

### Post by osviweb on 2008-11-27
I'm having the same same problem.
What we can do?

---

### Post by osviweb on 2008-11-28
no one knows a solution for this?
amsn is important for me. is this happening to all amsn users and anyone  cares? :confused:

---

### Post by Zer0d on 2008-11-28
What kind of output do you get if you run amsn from the terminal? Maybe it would give you some output like erros inside the terminal window.

---

### Post by macabro22 on 2008-12-01
Ok. aMSN has a problem with SCIM.

Create a bash script (just edit a text file) with the following:

```
#!/bin/bash
XMODIFIERS='' amsn &
```

then 

```
sudo chmod +x *filename*
```

Double click the file in nautilus to launch or create a menu entry pointing to it.

Cheers.

---

### Post by TWO on 2008-12-01
Funny I should come across this thread as I was about to post about this issue.

This happened to me long ago on amsn and it seems to come and go. I also have SCIM input installed. 

Surely this is a bug.

macabro22, what is your bash script designed to do?

Thanks

TWO

---

### Post by macabro22 on 2008-12-01
> **TWO said:**
> Funny I should come across this thread as I was about to post about this issue.

This happened to me long ago on amsn and it seems to come and go. I also have SCIM input installed. 

Surely this is a bug.

macabro22, what is your bash script designed to do?

Thanks

TWO

I built it based on a long aMSN forum discussion. Supposedly this should make aMSN ignore SCIM input, but I can type with accents nonetheless.

Try it out and post back, its harmless. XMODIFIERS is an [environment variable]("http://en.wikipedia.org/wiki/Environment_variable"), thats all I know, sorry.

---

### Post by TWO on 2008-12-04
Ah OK.

I sometimes need to use SCIM input so that might not be a good idea for me. 
I'm using emesene in the meantime, and whilst it's missing some of the features of aMSN, it's enough for me to use and be happy, and then there's no problem with SCIM on it.

---

