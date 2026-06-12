---
title: "My root password???"
date: 2005-11-07
forum: General Help
---

### Post by relativity on 2005-11-07
I just installed ubuntu but i don't recall being asked to enter a root password. I remember for normal user but no root. How am I going to get it?

---

### Post by adwait on 2005-11-07
For god sake, atleast google it ONCE before posting here.
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by relativity on 2005-11-07
Next time don't bother reply if you're going to have that attitude.

---

### Post by iluminate on 2005-11-07
It's good to search and read before you post any questions :)
Root is disabled by default in Ubuntu. However it can be enabled though.
Read through [http://ubuntuguide.org/](http://ubuntuguide.org/) and many of your questions will be answered.
Hope it helped!
Cheers

---

### Post by afonic on 2005-11-07
[QUOTE=relativity]Next time don't bother reply if you're going to have that attitude.[/QUOTE]

Well his attitude was not right but I kind of understand him. :cool: 

You see there are 10 posts / day about root pass here and nobody bothers to read the wiki, its the first article on the first page.

The right order is:

1) Search the documentation
2) Seach the forum
3) Search Google
4) Post and ask

and not the other way around! :)

---

### Post by Zwack on 2005-11-07
While I don't condone adwaits attitude, I am an irregular visitor to this forum and I see that question way more than you would think...

Simple answer for anyone using the search feature at the top of the page is that root is "disabled" by default and you use sudo to get root privileges when needed.

Sudo allows you to become root by providing your password, assuming you have been configured to do so.  The first user created in Ubuntu is set up to use sudo.

I hope that this helps, but next time consider using the search feature in the menu.  It's quick, painless and usually gets you useful answers.

Z.

---

### Post by nSTKo on 2005-11-07
Need to change root password?
```
sudo passwd
```
:)

---

### Post by adwait on 2005-11-07
[QUOTE=relativity]Next time don't bother reply if you're going to have that attitude.[/QUOTE]
Well look, I know nobody forced me to reply and I could have easily just ignored the thread, but when you look at that question SO many times, you kinda get irritated....and it just came out here. I didn't quite mean to sound so "RTFM" type......but you certainly should have searched before posting.
I'm sorry :)

---

### Post by r4ik on 2005-11-07
[QUOTE=iluminate]It's good to search and read before you post any questions :)
Root is disabled by default in Ubuntu. However it can be enabled though.
Read through [http://ubuntuguide.org/](http://ubuntuguide.org/) and many of your questions will be answered.
Hope it helped!
Cheers[/QUOTE]

Good link bookmarked it thanx.

---

### Post by relativity on 2005-11-07
Yes I know I should have searched first. I actually did after I posted and found threads that explained the problem. I panicked when I realised that I didn't have a root password, kinda like not having the keys to your house. I thought I was going to get a reply about a trick or something to get the password, it didn't cross my mind that it was a feature of the OS. Lol still haven't made up my mind about ubuntu as yet though. I like that its fast, didn't have to configure anything and it very easy to install apps but I feel like I am in a cage when I can't find kde control center or the terminal lol. I understand that it aims to make linux very easy to use which from what I see it does a great job but does anyone think that maybe they go a little too far at times?

---

### Post by madjo on 2005-11-07
actually it suits my need most perfectly.. I don't need root access that often only when I install software, and for that sudo fits the bill most perfectly... 
$ sudo apt-get install <whatever package you need>

I myself have used quite a few versions of Linux, but never really got the hang of it, until I stumbled upon Ubuntu... and now I have only booted into Windows 3 times over a periode of almost 2 months.. and all of three times was to check whether some piece of exotic hardware was acting up, or if it was Linux.. (in all cases it was the hardware) :)

But yeah, I have seen this question raised also on more than one occasion, even in a few reviews. 
A lot of people give Windows critic because by default its users are 'god' on their machine. And those same people try to do the same on Linux (become the root user). That is something I don't get.
Now I don't say that you are one of them, don't get me wrong.. and I too have enabled the root account, but I haven't used it yet. It's just an observation.

---

