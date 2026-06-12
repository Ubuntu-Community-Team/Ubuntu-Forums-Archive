---
title: "[SOLVED] Where is the root's trash?"
date: 2008-08-26
forum: General Help
---

### Post by befana on 2008-08-26
As my root partition is getting full I want to empty the root's trash. When running "gksudo nautilus" and trying to open the root's trash, I get this error:
"The folder contents could not be displayed. Sorry, couldn't display all the contents of "trash": Operation not supported."

Why I do not have access to this trash?

I am with Ubuntu 8.04.

---

### Post by ad_267 on 2008-08-26
It's in /root/.local/share/Trash/files

---

### Post by iaculallad on 2008-08-26
Root's Trash is located at (Hardy):

```
~/.local/share/Trash/files/
```

---

### Post by iaculallad on 2008-08-26
> **ad_267 said:**
> It's in /root/.local/share/Trash/files

Where is that? Is there a directory like that in the filesystem?

---

### Post by befana on 2008-08-26
I do not have /root/.local. "Show Hidden Files" is ON.

---

### Post by ad_267 on 2008-08-26
You probably don't have anything in the root's trash then otherwise there would be a .local directory if you're using 8.04.

> Where is that? Is there a directory like that in the filesystem?

Yes, /root is roots home directory. It's the same place you posted. ~ is /root for root.

---

### Post by iaculallad on 2008-08-26
> **ad_267 said:**
> You probably don't have anything in the root's trash then otherwise there would be a .local directory if you're using 8.04.



Yes, /root is roots home directory. It's the same place you posted. ~ is /root for root.

/root is not the same as ~. As ~ depicts/symbolizes your HOME directory. And there is no /root folder in the Filesystem hierarchy.
Posting a path like that could not help the OP either as it would only create ambiguous answer. Be direct instead.

---

### Post by befana on 2008-08-26
[QUOTE=ad_267;5666351]You probably don't have anything in the root's trash then otherwise there would be a .local directory if you're using 8.04.


And I will have that directory only when root will delete something?

---

### Post by Tom--d on 2008-08-26
What version of Ubuntu are you on as the Where the Trash is held is different.

Root has its own Trash and so do you.
Roots trash (in 8.04) is located in
```
/root/.local/share/Trash
```
Are you sure there are things in there?

---

### Post by befana on 2008-08-26
> **Tom--d said:**
> What version of Ubuntu are you on as the Where the Trash is held is different.

Root has its own Trash and so do you.
Roots trash (in 8.04) is located in
```
/root/.local/share/Trash
```
Are you sure there are things in there?

Few days ago my root partition suddenly was 100% full and I could not do anything and because of that I had to reinstall Ubuntu 8.04. Reading here posts about full root directories I'm trying to learn how to prevent root directory getting full. So I am looking now for root's trash, to know where it is and to empty it if necessary. But I can not find it nor /root/.local. And how to know if there is something in root's trash, if I can not find it?

---

### Post by ad_267 on 2008-08-26
> **iaculallad said:**
> /root is not the same as ~. As ~ depicts/symbolizes your HOME directory. And there is no /root folder in the Filesystem hierarchy.
Posting a path like that could not help the OP either as it would only create ambiguous answer. Be direct instead.

He is asking where root's trash is, not his own trash. ~ depends on which user you are and so ~/.local/share/Trash/files/ is only root's trash if you're logged in as root using sudo. No matter what user you are logged in as /root/.local/share/Trash/files/ is always the roots trash.

> And there is no /root folder in the Filesystem hierarchy.
From [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)
> 
/root/ 	Home directory for the root user.


To the OP, if you haven't deleted something as root in nautilus (using rm from the terminal will delete it, not move it to trash) then that directory won't be there. 

Some commands to free up some space:
```
sudo apt-get autoremove
sudo apt-get clean
```
apt-get clean removes all of your downloaded packages so usually you would just use "sudo apt-get autoclean"

---

### Post by Tom--d on 2008-08-26
> **befana said:**
> Few days ago my root partition suddenly was 100% full and I could not do anything and because of that I had to reinstall Ubuntu 8.04. Reading here posts about full root directories I'm trying to learn how to prevent root directory getting full. So I am looking now for root's trash, to know where it is and to empty it if necessary. But I can not find it nor /root/.local. And how to know if there is something in root's trash, if I can not find it?

Use Applications > Accessories > Disk Usage Analyzer.
It shows whats using what. Make sure you scan your whole drive, not your home directory.

---

### Post by ilrudie on 2008-08-26
Perhaps you are confusing the root filesystem (e.g. /) with root's home directory (e.g. /root).  The OP could be saying / is full.  To me this makes more sense because root really shouldn't have anything in trash.

To OP:  Post the output from ```
df -kh
```
What is telling you that your root partition is filling up?

---

### Post by befana on 2008-08-26
I am really sorry about my ignorance, but I do not know what is OP.
Please, explain!

---

### Post by drs305 on 2008-08-26
befana, 

It appears I wrote a tutorial this week that applies to your situation. I think it should answer your questions. Here is the link:
[Disk Full? - Check Your Trash Bin(s)]("http://ubuntuforums.org/showthread.php?t=898573")

It covers system/root trash, how to find it, how to get rid of it, and what tools/commands are available to do these things.

---

### Post by Irony on 2008-08-26
Type in terminal;

```
gksudo nautilus
```

Type your password and hit enter, then paste into the address bar;

```
/root/.local/share/Trash
```

And delete anything in it.

---

### Post by thierrybo on 2008-11-09
As far as I remember, I never could open Places->Trash when Nautilus was opened as root. Don't remember if this also occured before Gnome use FreeDesktop specification or not. This issue is not only about Trash. We can't open Places->Computer too.

---

### Post by thierrybo on 2008-11-09
Oh,

also a simple workaround. In Intrepid Ibex install trash-cli package (Universe) and type ```
sudo empty-trash
``` to remove all files from **your** trash including thoses with permission problems and 
```
sudo su
empty-trash
exit
```
to empty root trash

---

### Post by glotz on 2008-11-09
> **befana said:**
> I am really sorry about my ignorance, but I do not know what is OP.
Please, explain!

OP stands for Original Poster, ie. you in this thread.

---

### Post by bronner on 2008-11-15
where is the root trash in 8.10???? please help :(

---

### Post by drs305 on 2008-11-16
> **bronner said:**
> where is the root trash in 8.10???? please help :(

It's located in /root/.local/share/Trash.

Check the link in my signature line for more about finding and deleting *trash* from your system.

---

