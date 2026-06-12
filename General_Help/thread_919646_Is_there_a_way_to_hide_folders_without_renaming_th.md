---
title: "Is there a way to hide folders without renaming them to .foldername?"
date: 2008-09-14
forum: General Help
---

### Post by S3loth on 2008-09-14
I have some things linked to a few folders, so renaming them would mess it up.

---

### Post by mb_webguy on 2008-09-14
Not really.  Naming files and folders with a leading dot is what makes them hidden.

---

### Post by lian1238 on 2008-09-14
You can rename it foldername~ but it still requires renaming.
Edit by Oldsoldier:** This is very bad advice, bordering almost on malicious- since there are many cleaning scripts that will remove files and directories that end with a tilde.**

---

### Post by lian1238 on 2008-09-14
Wait, I found this: [quote=ahawesome]
If you want to hide files and folders without renaming them:

 Create a file named ".hidden" (without the quotes, of course) in the directory containing the files/folders you want to hide
 If you can't see the file, press Control-H or go to View->Show Hidden Files
 Open up the file in the text editor (I had to do this as root for some reason, you may not need to)
 Add the name of a file or folder you want to hide
 Save the file, exit the text editor, and open or refresh Nautilus (F5)
 You should not be able to see the file or folder


Hope this helps![/quote]

---

### Post by drs305 on 2008-09-14
There is a way. 

In the same directory, make a text file called .hidden
Inside that file type the names of any files or folders you want hidden. If you have nautilus set up to hide hidden files and refreshed it, you will not see any of the files/folders listed in the .hidden text file.

---

### Post by CorvisRex on 2008-09-14
Wow! I did not know that... that is really handy, thanks!  I can think of LOTS of way THIS is useful, particularly on workstations on a network.... 

Cool!

---

### Post by lswb on 2008-09-14
> **lian1238 said:**
> Wait, I found this:

That will work for Nautilus and possibly certain other file browsers but the listed files will still show up in an ls listing or in browsers that don't check for a .hidden file list.

---

### Post by mb_webguy on 2008-09-14
> **lswb said:**
> That will work for Nautilus and possibly certain other file browsers but the listed files will still show up in an ls listing or in browsers that don't check for a .hidden file list.

Ah... I was wondering why I hadn't heard of this trick.  I'm not new to *nix operating systems, but most of my experience has involved logging in to a server via telnet or ssh.  I'm still learning when it comes to these new-fangled GUIs on Linux...

---

### Post by niteshifter on 2008-09-14
Hi,

> You can rename it foldername~ but it still requires renaming.

Aw man, that's mean. And when the OP asks to how to clean up the clutter in their home folder and receives instruction to rm -rf *~ or uses one of the handy scripts floating about to do said housekeeping....

Poof! It will be gone. There's a reason the convention is a dot prefix.

---

### Post by Oldsoldier2003 on 2008-09-14
> **niteshifter said:**
> Hi,



Aw man, that's mean. And when the OP asks to how to clean up the clutter in their home folder and receives instruction to rm -rf *~ or uses one of the handy scripts floating about to do said housekeeping....

Poof! It will be gone. There's a reason the convention is a dot prefix.

+1 

I have edited the post in question.

---

