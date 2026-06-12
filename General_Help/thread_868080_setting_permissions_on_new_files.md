---
title: "setting permissions on new files"
date: 2008-07-23
forum: General Help
---

### Post by dexter.deepak on 2008-07-23
is it possible to pre-set the permissions of the newly created file in a folder ?
what i want is to have a ~/bin directory in which , whatever file i create would have an execute permission...i need this thing coz i am fed up of changing the permission of the shell scripts i make , every time.

---

### Post by apswartz on 2008-07-23
Good question. I don't know. See if...
```
man acl
```
provides the information you are looking for -- or maybe a starting point.

---

### Post by dexter.deepak on 2008-07-24
i did have a look at some of the guides on ACLs... and it seems to be just a substitute of 'chmod' , although more powerful and flexible than that. so i can only use ACLs to secure my stuff .
but what i need is permissions over the new files..in short i am looking for a substitute of 'umask'.

---

### Post by GreenN00b on 2008-07-24
There is a command that can do this, the umask command.
You can see more details here:
[http://en.wikipedia.org/wiki/Umask](http://en.wikipedia.org/wiki/Umask)

---

### Post by estyles on 2008-07-24
I think umask affects *all* files created in the file system - I didn't see a way to do it to individual directories, though I might have missed it, sort of skimmed...

Here's a different idea...  what if you set up a nautilus action called "Make Executable" that ran "sudo chmod a+x".  It should then show up in your right-click menu.  I know this is easy enough to do in Mint.  In Ubuntu, I think it requires installing a package, which I think is called nautilus-actions, or something like that.  You could omit the sudo if you only want to do it to files in your own userspace.

---

### Post by dexter.deepak on 2008-07-25
yes..umask affects "all" the newly created files in the system..thats why i was asking for a "substitute" of umask in my earlier post.
i already have nautilus-actions on my system..i think i cant use it properly. i am attaching the screenshots of what i did for `chmod a+x` on the selected file...but this didnt work.please tell me where am i wrong.

---

### Post by estyles on 2008-07-25
I'm no expert, but I think you want %d/%f as the parameters.  

If that doesn't work, I would try "/bin/chmod" as the path to the command and "a+x %d/%f" as parameters.  But I don't think that's necessary.

---

### Post by dexter.deepak on 2008-07-25
@ ^^
didnt work:(

---

### Post by estyles on 2008-07-25
ugh... been trying to figure this out for like a half-hour... and then suddenly it worked.  At one point, it seemed like nautilus was passing single-quotes before and after each parameter, but that might have been the way I was using to check it (gnome-terminal --title="chmod a+x %d/%f" ...  couldn't figure out any other way to send the command to a terminal and have it kept open - like I said, not an expert here by any means...).  

But then I changed the command back to "chmod a+x" and paramaters to "%d/%f" (make sure that slash is in there) and it worked.  If you have it perfect and it's not working, it might require you to restart nautilus (either logout and back in or "killall nautilus") in order to work.

I attached screenshots.  The third one is after right-clicking the file and running "Make Executable" from the context-menu.

---

