---
title: "command to get to drive on another computer"
date: 2008-07-27
forum: General Help
---

### Post by wgato on 2008-07-27
Hello-

I am able to see my mp3s that are on another computer through the file browser on the desktop.  The file browser location bar shows: smb://chup/elements%20(e)/Music

now i'd like to access the files through the bash command line but dont have the knowledge.  i've tried to move into the directory by
cd smb://chup/elements%20(e)/Music
and
cd //chup/elements%20(e)/Music

but it doesnt work.  i'm not sure if it is because i am escaping the ( wrong or if the drive is not correctly mounted (i'm not completely clear on what 'mounted' means.  but it seems like if i can access it through the gui, it would be right??)

can anyone point me in the right direction?

thanks!

---

### Post by Dr Small on 2008-07-27
It is a little bit more complicated to use smb through the terminal, though if you posses the knowledge, it can be done in a breeze.

One must learn to use smbclient, and the search engines seem to have the best documentation avaliable on how to use it. Unfortuantly for me, I use it so rarely that I have to look up how to use it, each time I try to use it.

Dr Small

---

### Post by wgato on 2008-07-27
thanks, that gives me something to google at least.  ideally i'd liek to make a sym link to the music directory but thats a step or 2 away at the moment.

---

