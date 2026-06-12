---
title: "Synaptics Touchpad Problems"
date: 2009-09-30
forum: Hardware
---

### Post by Saku'sTroubles on 2009-09-30
So, yes I am new, hello and all of that. But I have a serious problem that may prevent me from doing my work...

I have an older Toshiba laptop with a Synaptics touchpad. I had gotten this computer from my mom who spilled coffee on it and ruined the buttons on the touchpad. So I plugged in a HP mouse. The USB ports soon gave out. Now I am tapping and maneuvering strictly on the touchpad.

It double taps, single taps, ect. But I cannot double tap and drag. Thus preventing me from doing my graphical work and my file editing. I have determined the problem. It does not register the tap until I let go where it clicks and un-clicks. But I have **no **fix!

I admit that I am not an extreme geek. So if you post an answer, please give me detailed instructions. ((Click here, download this, put it here))

Thank you! I have been beating my head against the wall for about 3 hours.

---

### Post by rubenverweij on 2009-09-30
Welcome to the forums.:)
Could you tell us first precisely what kind of laptop you have? (version number)
Then I might be able to help...

---

### Post by Saku'sTroubles on 2009-09-30
Yes... Here we go... This is what it says on the bottom of the laptop...

**Toshiba **PM760 1024 100 15WCH 1915 g 1Y QP

Model No.

PSM42U-017006

Serial No.

Y5044600Q


Is that what you wanted?

---

### Post by Saku'sTroubles on 2009-10-01
-bump-

I **need **help with this! I can't even copy/paste.

---

### Post by rubenverweij on 2009-10-01
As far as I can see, it is a Toshiba Satellite M45-S359.
Have you already filed a bug report? If not, please do the following: use Alt+F2 to fire up a launch dialog.
In the box type:
```
ubuntu-bug xserver-xorg-input-synaptics
```
And hit enter. This will send a bug report to the Ubuntu developers. Could you post the link to the report if it has succeeded? It sends additional information, that makes it easier to fix.

---

### Post by Saku'sTroubles on 2009-10-01
Hmm, the Alt + F2 seems to not work.. It isn't bringing anything up....

---

### Post by rubenverweij on 2009-10-01
Now that is strange. Well, instead just open a Terminal via Applications->Accessories->Terminal and type the command I provided above.

---

### Post by Saku'sTroubles on 2009-10-02
The command line correct? I also did I quick search through my computer and found a hyper-terminal, but it wanted to dial a number in my area. oter than that, I have no terminal on my computer under 'Accessories'. I am so sorry about being difficult.:(

---

### Post by SkyNet2029 on 2009-10-02
Your reply of alt+f2 not working and the finding of hyperterminal suggest that you are using a windows based computer. Is this the case or did I miss something. At any rate, you can file a bug report through the website.

---

### Post by Saku'sTroubles on 2009-10-03
Oh. I am using Windows XP. Excuse my retardness -headwall-

I guess I will find out how to file a report of some sort.

---

### Post by MarkDingwall on 2010-11-18
Bug report?!!! Whoa! What the hell?  This person just wants to know how to take the Toshiba apart and clean out the spilled coffee from the touchpad!  Does anyone ever read?

---

### Post by SkyNet2029 on 2010-11-21
Thanks. I read just fine. Please note date of OP. 
Also, this looked like an issue I had come across on my Toshiba laptop wherin the drivers did not allocate proper resources and device settings.
Thank You, but try not to be a troll next time.

---

