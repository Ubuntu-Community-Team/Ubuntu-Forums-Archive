---
title: "[SOLVED] Help with my new Ubuntu Hardy 8.0"
date: 2008-10-06
forum: General Help
---

### Post by BSG Fan on 2008-10-06
Hello

I am trying to delete a folder from my pc but I can not.  The message is:
"The file cannot be moved to the trash.
Unable to trash file: Permission denied"

Okay, How can I delete that (and future) folders if I am the owner of the computer, of course?

Something else:
I am new in Ubuntu
where is the "TEMP" folder(its equivalent) for Ubuntu?

---
In another Topics:

I can not watch online videos from Youtube, etc although I can download them and watch in "Movie Player"
so, what I do to watch them online?
----

My pc freezes from time to time obliging me to restart the pc,
any idea?  What to do?  A new memory?  My memory is 2 GB!

---

Other question:
I heard that Ubuntu is virus-free but what about hackers-free?

Thanks for read

=)
Note:
I do not know if this is the corresponding forum, sorry

BSG Fanhttp://ubuntuforums.org/images/smilies/new_popcornsmiley.gif

ps:
How to "thanks" here the repliers?  I am confused ;)

---

### Post by kpkeerthi on 2008-10-06
1. Post of the output of the below command:
```
ls -ld ~/.local/share/Trash
```

2. For Youtube, [install flash]("http://www.psychocats.net/ubuntu/flashubuntu")

3. Not sure about your freezes

4. Temp folder is /tmp. Select Places -> Home. Press Ctrl + L and type /tmp in the location bar to view this folder. 

5. To say thanks, click on the blue ribbon with a star you see on the bottom right corner of this post. :)

6. Ubuntu Security:
[http://ubuntuforums.org/showthread.php?t=919472](http://ubuntuforums.org/showthread.php?t=919472)
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Also spend some time reading [https://help.ubuntu.com](https://help.ubuntu.com)

---

### Post by geirha on 2008-10-06
> **BSG Fan said:**
> Hello

I am trying to delete a folder from my pc but I can not.  The message is:
"The file cannot be moved to the trash.
Unable to trash file: Permission denied"

Okay, How can I delete that (and future) folders if I am the owner of the computer, of course?


Where is the file located? You need to have write access to the directory it's contained in in order to delete it.

> **BSG Fan said:**
> 
Something else:
I am new in Ubuntu
where is the "TEMP" folder(its equivalent) for Ubuntu?


/tmp is the temporary folder. It is wiped everytime you boot. To get to it using nautilus (the "explorer"), you go to "Filesystem" -> "tmp"

> **BSG Fan said:**
> 
---
In another Topics:

I can not watch online videos from Youtube, etc although I can download them and watch in "Movie Player"
so, what I do to watch them online?
----

In firefox, when there's a flash video on the page you have loaded, a new bar should appear at the top of the page, which you can click in order to install flash. Have you tried that?

> **BSG Fan said:**
> 
My pc freezes from time to time obliging me to restart the pc,
any idea?  What to do?  A new memory?  My memory is 2 GB!


Could you explain more on how it freezes? Is the mouse pointer still active? Does it happen randomly or when you run a certain program?

> **BSG Fan said:**
> 

Other question:
I heard that Ubuntu is virus-free but what about hackers-free?

Thanks for read


A fresh install should be very secure as it does not have any services listening on the network, so there should be no way in. It depends on what services you install and how securly you set them up, and whether you install packages from outside ubuntu's package repositories.

> **BSG Fan said:**
> 
=)
Note:
I do not know if this is the corresponding forum, sorry

BSG Fanhttp://ubuntuforums.org/images/smilies/new_popcornsmiley.gif

ps:
How to "thanks" here the repliers?  I am confused ;)

This is a good place to ask these questions :) To thank someone for a useful post, you click the medal icon at the bottom right corner of that post.

---

### Post by Sef on 2008-10-06
It is best to post one problem in one thread.  That way it increases the chance that your questions will all be answered.

---

### Post by BSG Fan on 2008-10-07
Hello everybody

I will answer to each one of you here.

First, I thanked to all you this time.  The first time I used this forum I did not know how to do it.  My bad!

second:
I finally deleted the folder in my desktop.  thanks you

Third:
Now I can see Youtube videos.  thanks you.

Fourth:
My pc continues freezing: well, my cursor freezes and I am obliged to restart the pc.  That happens mostly when the Internet is on.
Where I detect the processes?  and how I know which one to stop without harm the pc?

Fifth:
I tried to get where the Folder /TMP is but I couldn't find its location.

----

I have a new problem:

My Mozilla Firefox 3.0 pop outs (disappears) after be opened!
Why happen that??

Once again thanks to:

Sef
Geirha
kpkeerthi

and let me thanks that people that helped me in August but I did not thanks them:
VitaLiNux
Jualin
jamesrfla

---

### Post by kpkeerthi on 2008-10-08
File & folder names in linux are case sensitive. /tmp is not same as /TMP.

Press ALT+F2 while on your desktop and type ```
nautilus /tmp
```. You may also type this command at the command prompt in a terminal.

---

