---
title: "error in Java ! anyhelp ?"
date: 2009-06-20
forum: Installation &amp; Upgrades
---

### Post by Bloody-Hell on 2009-06-20
[SIZE=3][COLOR=black]hi 
im new user in ubuntu 

the problem is that i install java many time but every time i try to enter a chat after i put my nick-name and Enter i got this error 

[/COLOR][/SIZE][ATTACH]118333[/ATTACH]
[SIZE=3][COLOR=black] 

please anyone kno wt this mean or wt should i do till me 

thanks '
[/COLOR][/SIZE]

---

### Post by starcraft.man on 2009-06-20
Full disclosure, I'm not a Java expert >.>. Can you provide the link to the java applet/site your using for chat. Then I can try it on my machine and see if I also get the error. 

How did you install java btw? It comes packaged with the ubuntu-restricted-extras package by that means? If not, please describe.

---

### Post by Bloody-Hell on 2009-06-20
AT first i install java from add-remove tool 
i have that error so
after that i removed it and install it again from terminal 
i used the next code 


[COLOR=Red]sudo apt-get install sun-java6-bin[/COLOR]

after that i do 

[COLOR=Red]sudo apt-get upgrade [/COLOR]

and 

[COLOR=Red]sudo apt-get install openjdk-6-jre[/COLOR]


-----------
the chat link is :
[http://chat.alshellah.com/](http://chat.alshellah.com/)

---

### Post by Bloody-Hell on 2009-06-20
juss want to till 

the java is install in my machine but i think the error is in  some file missing or need to config

---

### Post by starcraft.man on 2009-06-20
```
sudo aptitude install sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin

```

Run the above code in terminal, that will install any missing files that you need. Then restart browser.

I don't think you'll have a problem after that. I can't really take that site for a spin, I don't read arabic >.>.

---

### Post by Bloody-Hell on 2009-06-20
sorry but i tray the code and restart the firefox 
but the error still there 
----------
the web site i give you there a botton in the right next to Nick-Name 
juss enter a name and click connect 

<< for the record i tray other chat site also the same problem !

anyway thanks [starcraft.man]("http://ubuntuforums.org/member.php?u=250927") you awesome man ; :D

---

