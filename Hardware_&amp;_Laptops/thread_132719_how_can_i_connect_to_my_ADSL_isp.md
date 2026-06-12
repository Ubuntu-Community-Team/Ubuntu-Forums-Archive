---
title: "how can i connect to my ADSL isp?"
date: 2006-02-18
forum: Hardware &amp; Laptops
---

### Post by Matt Clark on 2006-02-18
i have just installed ubuntu on my compaq evo n400c laptop.

i cannot figure out how to get it to connect to my ISP (hinet- in Taiwan) 

can anyone send me a link or step by step instructions on setting up an ADSL connection inside ubuntu? with screenshots would be great! I am a simple man.

it uses old fashioned wires, but it isnt a dialup. I do have a CD-Rom they gave me, but unfortunately the stuff inside it is some programming language stuff for RedHat 6.0 and i am not sure where in Ubuntu or IF Ubuntu has a place for me to type in their command lines. 

yes i am a newbie. I just downloaded it after getting my new comp. right now I am switching my old comp over to Linux as an experiement to see if I can get a more stable system running (I am a bit sick of the buggyness of Xp- but right now at least I know how to get things running in Xp. sigh.)

ubuntu looks good btw, i hope someone can help me.

---

### Post by prizrak on 2006-02-18
Hmm,
Try going through this section 
[http://www.ubuntuforums.org/forumdisplay.php?f=100](http://www.ubuntuforums.org/forumdisplay.php?f=100) It has loads of How-To's
Also see if there is anything helpful here [http://doc.gwos.org/index.php/Main_Page](http://doc.gwos.org/index.php/Main_Page)
You could also call your ISP they might have a techie who'd be happy to walk you through the install.

---

### Post by newbie_jhay on 2006-02-19
ei matt, what kind of connection do u have? if it is using a pppoe connection like mine, where u still have to dial in and enter a user name and password, u cud try running 

#sudo pppoeconf

it will guide you through putting all the needed info (i.e. username, password). then, usually after that, it will try to connect everytime you boot up as long as your dsl modem is on....

hope this helps =)

---

### Post by newbie_jhay on 2006-02-19
by the way, you could also try to check out this thread for further info....

[http://www.ubuntuforums.org/showthread.php?t=126396](http://www.ubuntuforums.org/showthread.php?t=126396)

again, hope this helps....

---

