---
title: "How to install sound drivers via cli"
date: 2009-01-29
forum: Installation &amp; Upgrades
---

### Post by himagain on 2009-01-29
Greetings all!
Certain ASUS M/boards require drivers to be installed via CLI.
Downloaded files and I finally learned sort of how to, and get the following: 

 me@Rigby-Thing:~/Desktop/ASUS/Audio/Audio$ 
me@Rigby-Thing:~/Desktop/ASUS/Audio/Audio$ ./install
bash: ./install: Permission denied
me@Rigby-Thing:~/Desktop/ASUS/Audio/Audio$ su me
Password: 
me@Rigby-Thing:~/Desktop/ASUS/Audio/Audio$ ./install
bash: ./install: Permission denied
me@Rigby-Thing:~/Desktop/ASUS/Audio/Audio$ 
---------------------

I have copied the directory info directly and manually - same result.
Any clues welcome.... Newby warning applies.....:(

---

### Post by jms1989 on 2009-01-29
Well, to install anything in ubuntu, you must install it as root.

Try (sudo ./install) and if that fails try:

sudo -i
cd /home/me/Desktop/ASUS/Audio/Audio
./install

Keep in mind, the file or executable in this case must be marked as an executable so chmod it to 755.

chmod 755 install

Hope this works, cheers mate.

---

### Post by himagain on 2009-02-04
> **jms1989 said:**
> 

Keep in mind, the file or executable in this case must be marked as an executable so chmod it to 755.

chmod 755 install

Hope this works, cheers mate.

Hi there!
Thanks for your reply.
Nobody ever said that before! 
(Wouldn't occur to me to have to do something like that separately to install a manufacturer supplied fix! 
(Also nobody else thought of it either, till you! :-)
I did it and it tried to work........ but
About 100 plus lines on screen but didn't work at the end... :-(

I see you have an ASUS system - did you have to download drivers to get sound?
I also see you seem to be on a very early version of Ubuntu .....
I've had many problems since upgrading to 8.10 esp. display.
Maybe I should go back!!!  

Cheers!
Would you mind taking a look at the very long output?

---

