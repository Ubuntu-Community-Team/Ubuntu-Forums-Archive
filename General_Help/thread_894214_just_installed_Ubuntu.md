---
title: "just installed Ubuntu"
date: 2008-08-19
forum: General Help
---

### Post by devinloretz on 2008-08-19
I had my Windows Xp desktop crash so i bought a new HD and installed Inbutu. I just installed it and it was working great. I was surfing the internet a bit with my wireless card that worked right away. Then I went to the restricted drivers and showed my sound card and said i needed to install the drivers so i did. and then it said i need to restart so I did. 

Now when the system turns on it shows the Ubuntu name and the orange loading bar. It loads all the way up but then just goes to a complete black screen. Meanwhile my HD just continually seems to be spinning making more and more noise. Seems like it continuously builds up.

no clue what to do....

---

### Post by Ryadt on 2008-08-19
Try starting in recovery mode. Start x from there```
startx
```

---

### Post by devinloretz on 2008-08-19
When I go through recovery mode everything runs through and then I am left with the Recovery Menu. From here I have:

resume   resume normal boot
dpkg     repair broken packages
root     drop to root shell prompt
xfix     try to fix X server

which one of these should i choose?

---

### Post by Ryadt on 2008-08-19
> **devinloretz said:**
> When I go through recovery mode everything runs through and then I am left with the Recovery Menu. From here I have:

resume   resume normal boot
dpkg     repair broken packages
root     drop to root shell prompt
xfix     try to fix X server

which one of these should i choose?

Go in the prompt

---

### Post by devinloretz on 2008-08-19
this session is running as a priviledged user

Running a session as a priviledged user should be avoided for secutiy reasons, if possible, you should log in as a normal user.


should i continue or quit?

---

### Post by devinloretz on 2008-08-19
> **devinloretz said:**
> this session is running as a priviledged user

Running a session as a priviledged user should be avoided for secutiy reasons, if possible, you should log in as a normal user.


should i continue or quit?

that is what it says when i put in "startx"

---

### Post by Ryadt on 2008-08-19
> **devinloretz said:**
> this session is running as a priviledged user

Running a session as a priviledged user should be avoided for secutiy reasons, if possible, you should log in as a normal user.


should i continue or quit?

Did you get the gui working? If yes restart and log in as normal user.

---

### Post by devinloretz on 2008-08-19
Since I am not too familiar with this yet I am not sure what the answer is to your question =]

First i hit quit and it brought me back to the prompt. So I entered startx again and this time hit continue. Now my screen is bright white with nothing there.

---

### Post by devinloretz on 2008-08-19
I guess problem solved I am able to log in now. After the bright white screen I just turned it off and turned it back on.

---

