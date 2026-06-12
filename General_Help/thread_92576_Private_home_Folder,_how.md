---
title: "Private home Folder, how"
date: 2005-11-19
forum: General Help
---

### Post by ubuntu27 on 2005-11-19
Hello all&#65281;&#65281;

I need another help from you guys.

In my Ubuntu, there are 4 users including me.
I creted users. 

I cannot access their Home FOlder, yet they can access mine.  [Their Home Folder has an Red "X"] 
Funny, in Windows, I was the one who could acces their files, and not them ><


How can I make my Home Folder private? 

My user account is the one that has the ability to do sudo. The first account creted by UBuntu Install. 

And also, is there a way that I coyld acces their home folder? I am tired of E-mail miself so, I could donwnload the file later in the other user account.

Thank you in advance guys/girls

---

### Post by soulestream on 2005-11-19
man chown

they shouldnt be able to access your folder without using root privlidges

as far as you accessing theirs

you have sudo access or you could use chmod 

soule

---

### Post by ubuntu27 on 2005-11-19
Man! ANd they don't have Root privileges, in fact, I haven't created a Root user.
But, they can access my Home Folder !! :???: 

Ohh! man. Didn't think about chmod  >< Now I can access theirs.

But, Still. 

haven't figured out a way to prevent them to have access to my Home Folder.

---

### Post by spartas on 2005-11-19
```

chmod 700 /home/`whoami`

```

---

### Post by ubuntu27 on 2005-11-19
thanks everybody. :)

---

### Post by ngnr on 2005-11-19
if you are using gnome then open nautilus, go to: /home

select your home folder,

right click -> Properties

then select the tab: "Permissions"

you will find three groups: "owner" , "group" , "others".

clear read, write and execute checkboxes in "group" and "others".

you can also try: 

```
$ cd /home
$ chmod 700 <your_home_dir> 
```

i hope this can help.

sorry for my english.

:)

---

### Post by ubuntu27 on 2005-11-19
Thank you ngnr. :) NO, your english is not bad at all. :)

---

### Post by patonw on 2005-11-19
You may or may not want to use the recursive option. They won't be able to list your ~/ directory but they can still access the files inside it and list it's subdirectories.

---

### Post by invalid on 2005-11-19
[QUOTE=patonw]You may or may not want to use the recursive option. They won't be able to list your ~/ directory but they can still access the files inside it and list it's subdirectories.[/QUOTE]
You can not access files inside a 700 folder, unless you are the owner.

Cb

---

### Post by doclivingston on 2005-11-19
[QUOTE=patonw]You may or may not want to use the recursive option. They won't be able to list your ~/ directory but they can still access the files inside it and list it's subdirectories.[/QUOTE]

Only if the directory has the execute permission set for other users.

---

### Post by reedlaw on 2006-05-15
When I set users' directories to 700 they can no longer login remotely over nfs. Is there anyway to make user directories private in this situation?

---

