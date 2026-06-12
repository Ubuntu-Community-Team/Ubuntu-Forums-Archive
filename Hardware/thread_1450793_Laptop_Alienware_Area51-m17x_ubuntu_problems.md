---
title: "Laptop Alienware Area51-m17x ubuntu problems"
date: 2010-04-09
forum: Hardware
---

### Post by razmaxis on 2010-04-09
As of 4-8-10 I was using windows vista and gaming happily, then i got smashed by about 28 viruses some worms and was told to pay $60 for windows security updates, i got 
UBUNTU 9.10 FROM a japanime con in boston and was told at the display i can do all gaming with it.  My computer was so ****ed from the viruses that i installed ubuntu
today 4-9-10.. .. now i have tons of problems and questions!!!!!!
I will ask a few questions and i pray for the answers!!!!!


ANY UBUNTU ALIENWARE USERS OUT THEIR PLEASE HELP!!!!!

on my laptop my eject button does not work..therefore i cannot insert cd/dvd discs
anymore. i usually just HOLD DOWN FN key while pressing F8 key to eject.

How do i get ubuntu to recognize my laptop butons????

---

### Post by rbolio on 2010-04-15
Hi there!

Welcome to the club :) 

Now, lets get to business.... First of all we all hope you have had a great experience using ubuntu and heres to freedom..

Anyways..

Hit Alt+F2  , in the window that pops up type [B]gnome-terminal[/B and hit enter.

When the new window pops up, type

```
update-manager
``` 
press enter

and this screen will look for any necesary updates for your computer...in this update the eject key command should be included....

if that doesn't work, try this more straight forward method

Go to terminal  (menu --> accessories --> terminal)

and type ```
Sudo apt-get install eject
```

Hit enter after entering your password.
Hope that works!


Oh I found  this as a bonus for you...plenty of the reviews claim its pretty good!

[http://ubuntuforums.org/showthread.php?t=1403399&highlight=alienware](http://ubuntuforums.org/showthread.php?t=1403399&highlight=alienware)

---

