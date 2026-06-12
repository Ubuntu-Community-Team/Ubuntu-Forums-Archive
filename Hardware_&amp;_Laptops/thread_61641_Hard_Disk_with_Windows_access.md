---
title: "Hard Disk with Windows access"
date: 2005-09-01
forum: Hardware &amp; Laptops
---

### Post by deathseeker25 on 2005-09-01
Hi people,

Well here i am with another doubt. I have two hard-disks. The first one has 80 Gb of storage data and the second one has 160 Gb. 

The HD with 80 Gb is for Windows use, but i think i won't need it no more since i have Ubuntu. The HD with 160 of storage data is where Ubuntu is installed. 

I want to know, how can i access to HD of 80 Gb(where Windows is installed).

Can you help me?

Thank you

---

### Post by KingBahamut on 2005-09-01
Youll need to edit your fstab in /etc to reflect the settings of your harddrive , with windows installed on it. 

Lets look at this......

/dev/hdx     /media/windows  ntfs    nls=utf8,umask=0222 0       0

youll need to add the above line to your fstab file in /etc 

the first bit - /dev/hdx is the specification of what linux sees your windows drive as. 

Typically for partitions sake its a /dev/hda1 , where the number denominates which parition on that drive. 

The next bit /media/windows - this bit is the name of a directory you wish to use as the mount point for the windows partition. On my system when accessing such a drive for data recovery purposes ( I do this alot, can you tell ) , I have it set at /windows 

the ntfs is setting the data type, as you can see ntfs for windows. 

everyting after nls is designed for some other miscellaneous options, like access right and so forth. 

If you do this properly, you should be able to see your windows parition on boot up in the specified mounted folder.

---

### Post by domstyledesign on 2005-09-01
check this page.

[http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)

---

### Post by deathseeker25 on 2005-09-01
Thanks a lot **KingBahamut** and **domstyledesign**...

I have done it... :)

---

### Post by deathseeker25 on 2005-09-01
Hey people a related doubt has ressurected, Apparently the link that dmstyledesign gave to me just explains how to have read access to Windows files. Now i wnat to know how to modify them.

That's because i have lots of music in the other HD and i can't play them here in Ubuntu....

Thank you

---

### Post by KingBahamut on 2005-09-01
In what format is this music?

---

### Post by deathseeker25 on 2005-09-01
[QUOTE=KingBahamut]In what format is this music?[/QUOTE]

It's mp3 format...but the music player that comes with ubuntu can't read it...just don't know why... :-?

---

### Post by KingBahamut on 2005-09-01
You need to read the ubuntu guide 

[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

do that and hell play mp3s all day.

---

### Post by deathseeker25 on 2005-09-01
[QUOTE=KingBahamut]You need to read the ubuntu guide 

[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

do that and hell play mp3s all day.[/QUOTE]

Thank you I'll install all codecs...sorry for the incovenience....that's because i'm a newb at linux...

---

### Post by domstyledesign on 2005-09-02
no need to apologize.  if it were a serious inconvenience then you probably wouldn't have gotten a response.  Just remember that ubuntu has been around for a while and so have these forums.  most of my problems have so far been solved by reading old posts.  the search utility isn't great, but it usually works.

---

### Post by KingBahamut on 2005-09-02
DS, we love newbs here. 

There are no stupid quesitons, nor are those who ask such questions themselves stupid.

---

### Post by undeadsoldier on 2005-09-02
[QUOTE=KingBahamut]DS, we love newbs here. 

There are no stupid quesitons, nor are those who ask such questions themselves stupid.[/QUOTE]
 Oh really!!

Well I for one didn't ask for a stupid question, and so did many other people, and they didn't get responded to... Only those questions that are most easily answered, are the ones that get done !!

---

### Post by KingBahamut on 2005-09-02
> I'm sick of this sh&#1110;t...

Of all the Linux forums, this is the only one that just doesn't give a fu&#1089;k about most peoples postings, its not just my post that gets widely ignored, its others.

Most posts that get answered is by people who either don't bother searching, questions that have been answered before, or questions that are easy to answer...

There is hardly anything wrong with the question I posted, the only fact that I want somebody else to build the modules for me is because I am getting shitloads of errors !

Of course, nobody ever came on this thread and replied "can't you build them, do you get an error"... ohh no, no such thing. Not a single reply from another member of this forum!

If anybody reads this before more questions get posted and gets bumped down the list, don't bother fu&#1089;king answering my question, whats the fu&#1089;king point really... Welcome to the world of linux, where every man's for himself on a fu&#1089;king island...

And for fu&#1089;ks sake, try and answer the other peoples postings that have 0 replies, you know, some people might care about having to get something out of the ordinary done!!

SO HELP PEOPLE, TRY AND ANSWER THEIR THREAD, ITS NOT THAT HARD !!

Undead when you make posts like this one, It surely doesnt make me want to help you in anyway. Patience is a virtue my friend. If we can help you, ask Google and try to learn yourself a little. Thats what a Community is about. Not about instant gratification. If thats what your looking for, then your not going to get it without improving that brain of yours.

---

