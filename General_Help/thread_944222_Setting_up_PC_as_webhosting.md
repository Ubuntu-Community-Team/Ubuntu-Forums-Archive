---
title: "Setting up PC as webhosting"
date: 2008-10-11
forum: General Help
---

### Post by Spartanis on 2008-10-11
To all it may concern,

I wish to learn about creating one of my PC as a webhosting space for my website. I know windoze have some program called IIS or something, but i was wondering if anyone can direct me to a "..for dummies" like site that would teach me the basic of finding the desired program for Linux (ubuntu), installing, and setting it up and all that jazz.

I have searched the net, but its confusing me with apache and stuff, for their site is mumble jumble and not really saying what its purpose is for..

Thanking you guys in advance.
Sparty

---

### Post by sokopok on 2008-10-11
Try this one: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by Spartanis on 2008-10-11
Thank you Sokopok,

That site is very useful to me. I have read slowly and carefully, and gotten as far as MySQL bit. And all is working well so far.

However, Im at lost to perform the recommended command of:- 

[COLOR="Purple"]*mysql -u root*
[/COLOR]
in the Terminal, for it spits back to me :-

[COLOR="Purple"]*ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)*[/COLOR]

I know i have to go into ROOT or something. The only thing i know is someone else taught me to use the "**alt + F2**" and type in "*gksudo Nautilus*" which is a nifty feature to use!

Thank you anyone who has time to read my thread,
Sparty

---

### Post by sokopok on 2008-10-12
When you installed the mysql server, you were asked for a root password. You need to log in to mysql using this password using the command: ```
mysql -u root **-p**
```The "-p" thingie instructs mysql to ask you for this password.
Whenever you're at a loss with just about any command in linux type: ```
**man** command
``` or ```
**info **command
``` this will give you a summary of available options for the "command"

---

### Post by Spartanis on 2008-10-12
Thanks, worked all the way.. now.. how do i tell the world what addy they should type in teh address bar to view my index.html on my home pc?

---

### Post by sokopok on 2008-10-12
get a domain name from your preferred registrar
or
give them your ip address
or 
use a dynamic dns service (eg. dyndns)

and
configure your router to forward traffic on port 80 to your machine

---

### Post by Calmatory on 2008-10-12
Why everyone prefers apache? [Lighttpd](http://www.lighttpd.net) is faster, lighter and simplier. It lacks all that fancy stuff which no regular home server needs.

Configure your apache for an hour with how-to, with Lighttpd I am done in bare 10 minutes on my own. :)

Then again, I would use Apahche for corporation stuff, or commercial or just anyuthing which needs it's fancy features which lighttpd lacks. For everyone their own.

---

### Post by sokopok on 2008-10-12
I never realy configured apache. It runs perfectly out of the box.

---

### Post by koenn on 2008-10-12
> **Calmatory said:**
> Why everyone prefers apache? [Lighttpd](http://www.lighttpd.net) is faster, lighter and simplier. It lacks all that fancy stuff which no regular home server needs.

Configure your apache for an hour with how-to, with Lighttpd I am done in bare 10 minutes on my own. :)

Then again, I would use Apahche for corporation stuff, or commercial or just anyuthing which needs it's fancy features which lighttpd lacks. For everyone their own.
true.
if you just need straightforward serving of some web pages, a distribution point for deb packages or other software, and other 'no thrills' stuff, lighttpd is an excellent choice.

(and it offers excellent protection against php, apache, or mysql oriented exploits  :) )

---

