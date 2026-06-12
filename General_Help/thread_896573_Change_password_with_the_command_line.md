---
title: "Change password with the command line ?"
date: 2008-08-21
forum: General Help
---

### Post by stoneage on 2008-08-21
Recently, due to a keyboard glitch I was unable to correctly enter my password. I have a spare user account, and was able to get in that way and resolve the issue, but I was left wondering....   

....how can I change my password using the command line?

---

### Post by iaculallad on 2008-08-21
> **stoneage said:**
> Recently, due to a keyboard glitch I was unable to correctly enter my password. I have a spare user account, and was able to get in that way and resolve the issue, but I was left wondering....   

....how can I change my password using the command line?

If you're login as the user yourself:

```
passwd your_username
```

Or, if you're login as someone else and want to change other's password:

```
sudo passwd username_of_others
```

---

### Post by stoneage on 2008-08-21
That's lovely and simple but if I don't have access to my current password can I do it as root? 

Sorry, I wasn't paying attention. So for example:-
su -
passwd my_username



EDIT - Yeah, that all works fine. Thanks very much - I won't get caught like that again.


2,560 posts in six months - don't you ever go home ?

---

### Post by cojon on 2010-05-04
```
passwd your_username
```

I have the same problem as the other person, but I can't seem to understand what you are saying or make anything work. I'm new to Ubuntu, but I like the concept. Please help me. 

I'm using my fathers computer to ask because my boyfriend has been promising to fix mine for a year now and only comes up with excuses. Like so many "average" people he can't man-up to anything. My father set the stage high. He's honest and real. If he says he will do something, get  ready for action. I wish I could find a man like that. A "real" man. 

Please Sir, could you tell me how to fix it? I haven't been able to use it for a year waiting on this 24 year old child to run out of dumb excuses .

---

### Post by darolu on 2010-05-04
Most of the time, when you see something in the "code" box, it means you have to run it on a Terminal (command line), go to **Applications -> Accessories -> Terminal** and run the command there. I hope this is the part you didn't understand. Otherwise please post more details about your problem (the computer one only), why can't you use your computer exactly?

---

### Post by sportsdude81 on 2010-10-23
Thanks for the Post:P

---

### Post by Samayas on 2011-09-10
Kubuntu 10.04 Lucid

THAT was easy. Thanks!:)

---

### Post by oldos2er on 2011-09-10
May angels sing thee to thy rest. Closed for necromancing.

---

