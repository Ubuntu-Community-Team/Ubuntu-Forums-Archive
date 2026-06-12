---
title: "Changing icons of known mimetypes"
date: 2008-10-23
forum: General Help
---

### Post by 3dmatrix on 2008-10-23
I have a large number of 'swf' files that i have collected from the web. I wish to assign a png icon (to ANY swf file I have), that i have made for it, but am unable to do so. Can anyone help me with this ? I tried the following two methods but non worked.

In this file ~./local/share/mime/packages/flash-files.xml I wrote the following :
<?xml version="1.0" encoding="UTF-8"?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
<mime-type type="application/x-shockwave-flash">
<comment>Flash movie</comment>
<glob pattern="*.swf"/>
</mime-type>
</mime-info>

I also placed the png files with names like application-x-shockwave-flash.png in the icon folders of all sizes like : ~./icons/Gnome-Green/64x64/mimetypes

---

### Post by pirattrev on 2008-10-23
maybe try application-x-flash.png or application-x-shockwave.png? I don't know, that's just a total shot in the dark.

---

### Post by 3dmatrix on 2008-10-24
Rt click > properties shows **application/x-shockwave-flash**, so i think it should be the same for the icons !

---

### Post by oomingmak on 2008-10-24
I use Assogiate for stuff like this.

I've tried manually editing MIME XML files in order to assign user specified icons to file types, but no matter what I did it just wouldn't work. However, Assogiate worked for me straight away, and it took less than 10 seconds to do.

Details on how to use Assogiate can be found in an instruction guide that I created here:

[[COLOR=DarkOrange]**http://ubuntuforums.org/showthread.php?p=3276774&#post3276774**[/COLOR]]("http://ubuntuforums.org/showthread.php?p=3276774&#post3276774")

The bits that are of relevance to you are steps **5** and **6**. You may need to update your MIME database in order to see the icon change.

> sudo update-mime-database /usr/share/mime/Adjust the above path to  suit your needs.

---

### Post by 3dmatrix on 2008-10-24
Is it available through Synaptic ?

---

### Post by oomingmak on 2008-10-24
I don't know (I'm on Windows, so I can't check). Surely it's easy enough to find out whether it's in Synaptic or not just by using Synaptic's search.

It's definitely in Add/Remove though (as stated in my instructions in the linked thread).

---

### Post by 3dmatrix on 2008-10-24
I installed it, made the changes in the program but nothing happened. Restarted - still nothing happened.

---

### Post by oomingmak on 2008-10-24
Made what changes? Did you create a new file type from scratch, or edit an existing SWF file type?

Did you try manually updating the Mime database from the command line?

---

### Post by 3dmatrix on 2008-10-25
Edited the existing swf mimetype and then updated the mime database by the command sudo update-mime-database ./usr/share/mime/

But nothing happened.

---

### Post by oomingmak on 2008-10-25
You said: 
> I also placed the png files with names like application-x-shockwave-flash.png in the icon folders of all sizes like : ~./icons/Gnome-Green/64x64/mimetypesSo maybe you need to update you local cache rather than the system wide one.

Try updating **~/.local/share/mime/**   and   **/usr/local/share/mime**

A couple of people have reported issues with failed icon updates when using 8.04 / Hardy, but I hardly ever use Linux and so my install is still on 7.10 / Gutsy. 

A few months ago I did try testing Assogiate out on Ubuntu 8.04, but it worked fine for me and I could not replicate the problems that other people were seeing.

---

### Post by oomingmak on 2008-10-25
Also, did you run Assogiate as a regular user or as root? because you may have been applying the changes to the wrong user account. 

Assogiate has settings (in the menu) to apply changes to all accounts, just to the current  user account or to the root account.

---

### Post by 3dmatrix on 2008-10-25
Note that '.local/share' is not in the search path
set by the XDG_DATA_HOME and XDG_DATA_DIRS
environment variables, so applications may not
be able to find it until you set them. The
directories currently searched are:

- /root/.local/share
- /usr/local/share/
- /usr/share/

Got the above reply !

---

### Post by 3dmatrix on 2008-10-26
Now after a lot of 'playing around' I am able to see the new icon when I try to open a file (ctrl+O) but not in the file browser (see attachments). How can I change it every where ?

---

