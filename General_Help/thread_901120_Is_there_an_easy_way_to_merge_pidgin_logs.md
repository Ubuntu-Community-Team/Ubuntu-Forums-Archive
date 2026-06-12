---
title: "Is there an easy way to merge pidgin logs?"
date: 2008-08-26
forum: General Help
---

### Post by fraktalek on 2008-08-26
Is there an easy way to merge pidgin logs? Or do I have to write it myself?

---

### Post by Joe of loath on 2008-08-26
theres a way to do it in the command line, but I can't remember it. it's quite simple though. let me go get my unix system V book... no, sorry. If it's there I can't find it. all I can say is open them both in gedit and cut all the info from one and paste it on the bottom of the other.

---

### Post by monkeyking on 2008-08-26
want do you want to merge?

give a small snippet of what you want to merge.

Is it the conversation you want to paste together?

if you just want to put one file at the bottem of the first one do something like

cat log1 log2 > outfile

---

### Post by trwww on 2008-08-26
find logs/ -type f | xargs cat > all_logs.txt

---

### Post by Dutch70 on 2008-08-26
> **trwww said:**
> find logs/ -type f | xargs cat > all_logs.txt 
 
what is it about people that know their stuff, giving these answers that make no sense at all?
 
You are better off getting an answer from someone that barely knows their stuff...

there is nothing funny about it either...no one is impressed with that ****
just looks like a foreign language.

and yes, I know that most codes look like a foreign language, but I just dont get why you can't give a little more info. If you are going to help someone, help them for crying out loud.

---

### Post by fraktalek on 2008-08-26
> **Dutch70 said:**
> what is it about people that know their stuff, giving these answers that make no sense at all.
 
You are better off getting an answer from someone that barely knows their stuff...

there is nothing funny about it either...no one is impressed with that ****
just looks like a foreign language.

and yes, I know that most codes look like a foreign language, but I just dont get why you can't give a little more info. If you are going to help someone, help them for crying out loud.

it is comprehensible for me but unfortunately not what I need :) (I should have made myself more clear).

I indeed want to merge conversations - from pidgin logs I have on my home computer and logs that I have on work and other computers. Pidgin keeps each conversation with each buddy in a different file. So there's lots of conversation, quite a few buddies and all of these from couple of computers (I've been lazy for quite a long time now to do anything about it). So there's no way I'd do that manually.

So I guess I'll have to put together some script myself.

---

### Post by trwww on 2008-08-26
> **Dutch70 said:**
> what is it about people that know their stuff, giving these answers that make no sense at all.


The question made no sense at all. In a basic sense, the command fulfills the OPs request. For us to provide better advice, a better question is needed.

To answer your question (or as it reads, your demand), The string of commands I posted finds all files recursively in the logs directory, echos them to the standard output device, and redirects the output to a file called all_logs.txt.

---

### Post by fraktalek on 2008-08-26
> **trwww said:**
> The question made no sense at all. 
Then you should have asked for more information.

> **trwww said:**
> 
In a basic sense, the command fulfills the OPs request. 

Well, given a problem, you can always think of a completely different problem and give a solution for that although it helps noone.

> **trwww said:**
> 
To answer your question (or as it reads, your demand)

That's your interpretation, it was a normal question, others took it well (and I am glad for their reactions).

> **trwww said:**
> 
, The string of commands I posted finds all files recursively in the logs directory, echos them to the standard output device, and redirects the output to a file called all_logs.txt.

I know precisely what it does, as I've said already above, and it is not what I need as I've also said. I clarified what I was asking for/about in my previous reply and also said that I should have been more precise. So this post of yours is really plain useless.

---

### Post by fraktalek on 2008-08-26
Well, after reading my original question again, I admit that it may seem arogant. But it certainly wasn't the intention I was just too quick to send it. Sorry.

---

### Post by trwww on 2008-08-26
> **fraktalek said:**
> Well, after reading my original question again, I admit that it may seem arogant. But it certainly wasn't the intention I was just too quick to send it. Sorry.

I was replying to the person that had complained abut me not doing a bash -> english translation :-)

---

### Post by fraktalek on 2008-08-26
> **trwww said:**
> I was replying to the person that had complained abut me not doing a bash -> english translation :-)

oops...I'm really too quick today, sorry again :(

And moreover...I found out that my problem is probably no problem at all. I've checked that pidgin really keeps each conversation in separate file so all is needed is simply to copy the backups of log directories from the other computers to my home computer.

---

### Post by trwww on 2008-08-26
> **fraktalek said:**
> I indeed want to merge conversations - from pidgin logs I have on my home computer and logs that I have on work and other computers.

An easy way to set this up without having to write an application to do it for you is to use subversion.

Make a subversion repository on a machine that all the machines you do IM from can access. Then make the logs folder on each pidgin instance a working copy. When you start work on a machine, 'svn up' in the working copy, and when you finish on a machine, 'svn add' and 'svn commit' the new log files/folders.

Then your logs will always have all conversations.

---

### Post by trwww on 2008-08-26
> **fraktalek said:**
> I've checked that pidgin really keeps each conversation in separate file so all is needed is simply to copy the backups of log directories from the other computers to my home computer.

Yep copying the 'logs' folder from machine to machine will work fine, too :-)

---

### Post by fraktalek on 2008-08-26
> **trwww said:**
> An easy way to set this up without having to write an application to do it for you is to use subversion.

Make a subversion repository on a machine that all the machines you do IM from can access. Then make the logs folder on each pidgin instance a working copy. When you start work on a machine, 'svn up' in the working copy, and when you finish on a machine, 'svn add' and 'svn commit' the new log files/folders.

Then your logs will always have all conversations.

yeah, that's a good idea, I didn't think of that. 
or maybe some synchronization tool?

---

### Post by trwww on 2008-08-26
> **fraktalek said:**
> yeah, that's a good idea, I didn't think of that. or maybe some synchronization tool?

Sure. Something like rsync would be a good median of subversion and hand copying the folder.

---

### Post by Dutch70 on 2008-08-26
> **trwww said:**
> The question made no sense at all. In a basic sense, the command fulfills the OPs request. For us to provide better advice, a better question is needed.

To answer your question (or as it reads, your demand), The string of commands I posted finds all files recursively in the logs directory, echos them to the standard output device, and redirects the output to a file called all_logs.txt.

Thank you for coming back and explaining it a little better. 

 I went back and put a "?" after the question. Certainly didn't intend to make any demands...:)  
I apologize if it came off that way.

 There are quite a few people searching for answers instead of posting questions, which is what I was doing. It just seems to be very difficult to find the answers that actually relate to my situation, whatever it is, and then the guru's complain about people not searching before they post, yet at the same time, they post answers that answer **only** the OP's direct question most of the time.

on a side note...this is really a funny thread.

---

### Post by Dutch70 on 2008-08-26
trwww,
 I bet you'll never forget the first post you were thanked in...:lolflag:
Actually it is really nice to have people like you here, and maybe I should just keep my big mouth shut. :popcorn:

---

