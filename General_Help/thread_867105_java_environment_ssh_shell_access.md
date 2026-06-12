---
title: "java environment/ ssh shell access?"
date: 2008-07-22
forum: General Help
---

### Post by oohwewubi on 2008-07-22
Hi, I just installed wubi. I installed it because I'm building a website using amazon ec2.  In the getting started guide it said I would need a java environment and ssh access.  it says this is usually a part of linux installations...do these item come standard with wubi or do I have to down load it from somewhere?  Thank you in advance.](*,)

---

### Post by ago on 2008-07-22
You get the ssh client with wubi. just type "ssh servername" in a terminal. As for java is not pre-installed, but you can install it as any other application. there are several guides on the subject

---

### Post by oohwewubi on 2008-07-22
> **ago said:**
> You get the ssh client with wubi. just type "ssh servername" in a terminal. As for java is not pre-installed, but you can install it as any other application. there are several guides on the subject

thank you.  What do you mean by a terminal?  Like your avi,btw.

---

### Post by ago on 2008-07-22
Something like the windows dos box... But much much better... ;)

---

### Post by oohwewubi on 2008-07-22
yeah I found it \\:D/ Applications > Accessories > Terminal

Now to figure out how to install java :-k

---

### Post by oohwewubi on 2008-07-22
> **ago said:**
> You get the ssh client with wubi. just type "ssh servername" in a terminal. As for java is not pre-installed, but you can install it as any other application. there are several guides on the subject
it says server unknown ](*,)

---

### Post by ago on 2008-07-23
you obviously need an internet connection and be sure the ssh server URL is correct. replace "servername" with whatever URL is appropriate.

---

### Post by oohwewubi on 2008-07-23
> **ago said:**
> you obviously need an internet connection and be sure the ssh server URL is correct. replace "servername" with whatever URL is appropriate.
:confused: How do I know the URL?  Was it given to me at install?

---

### Post by ago on 2008-07-23
> **oohwewubi said:**
> :confused: How do I know the URL?  Was it given to me at install?

That is the URL of the remote machine you want to connect to...

---

### Post by fred.warren on 2008-07-24
To get an ssh server running on your system, from a terminal type

sudo apt-get install openssh-server

The quick an painless way to get java depends on if you are running ubnutu or kubuntu or xubuntu or ubuntu server edition. the -restricted-extras will get you java, and adobe flash player, mp3 playback and ms core fonts. 

For ubuntu
   sudo apt-get install ubuntu-restricted-extras

For kubuntu
   sudo apt-get install kubuntu-restricted-extras

For xubuntu
   sudo apt-get install xubuntu-restricted-extras

For server
   sudo apt-get install sun-java6-bin sun-java6-jre

---

### Post by oohwewubi on 2008-07-29
fred.warren thank you so much for your reply.  I accidently found this thread while searching for ec2 on ubuntu and was surprised to see your post on the end.  It seems to have worked.  
You wouldn't happen to have experience with elasticfox would you?

---

