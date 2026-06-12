---
title: "Firefox 3.0"
date: 2008-07-10
forum: General Help
---

### Post by Animus Stealth on 2008-07-10
Hello,

First off, the problem I have at the moment would be my firefox. The problem is whenever I'm browsing websites I lose complete control of my mouse. Then right after my firefox starts to scroll at random which then freezes the browser. I've just installed WUBI ubuntu onto my computer, and I'm a little confuse at why this is happening.

---

### Post by pluckypigeon on 2008-07-10
Remove firefox and install opera


```
[CODE]gksudo gedit /etc/apt/sources.list
``` Add: deb [http://deb.opera.com/opera-beta/](http://deb.opera.com/opera-beta/) ```
sudo apt-get update
``````
sudo apt-get install opera
``````
sudo apt-get remove firefox
```[/CODE]

---

### Post by Animus Stealth on 2008-07-10
This is the first time I'm using Ubuntu, can you teach me how to use those codes?

---

### Post by cwii on 2008-07-10
Is it a specific page that you are viewing that causes it to crash?

> **pluckypigeon said:**
> Remove firefox and install opera


That isn't helpful.

---

### Post by Animus Stealth on 2008-07-10
Happens randomly. I lose contorl of my mouse and then my trash bin keeps opening like 100 times. And im on windows XP as well and that never happens.. But how do I install opera? Or view what programs are installed?

---

### Post by pluckypigeon on 2008-07-10
> **cwii said:**
> Is it a specific page that you are viewing that causes it to crash?



That isn't helpful.

It is helpful if he can't fix it. 

I wouldn't use a browser if I couldn't fix it. Maybe you would. Maybe that's why it is un-helpful to you.

---

### Post by dj3hac on 2008-07-10
I agree with Pidgeon, Opera is just as good as firefox in every way in MY opinion. Its worth a try, to put the code in do it in the terminal. I'm not sure but you may have to sudo it. Type in "sudo su" in the terminal before pidgeons code it should ask you for the root password. Correct me if I'm wrong, it's been a while since I linux'd

Scratch all the sudo stuff I didn't know Pidgeon included it. XD

---

### Post by aysiu on 2008-07-11
Does this happen with your mouse in any other application or just in Firefox?

Are you using a laptop touchpad or an external mouse?

Whether you choose to use Opera long term or not, you should try installing and using it to at least see if it's a web browser-related or Firefox-specific problem.

Just go to the Opera website and download the appropriate Ubuntu package and double-click the .deb file that downloads. If Firefox prompts you to open it with gDebi, you can do that too (and save the step of double-clicking the download).

---

### Post by Animus Stealth on 2008-07-11
I'm on Opera at the moment, and yes my mouse just goes crazy opening random things every now and then that im on Ubuntu. No, regular home computer not laptop.

---

### Post by falcon61102 on 2008-07-11
Does this just happen when you're using the browser or at any other time you're on the computer.  Also, is your mouse a wired usb or is bluetooth or some other wireless?

---

### Post by Animus Stealth on 2008-07-11
It's an USB mouse, and I know its acting up on Ubuntu because at the moment im on Windows XP and it never happens.

---

### Post by MyBrainReallyHurts on 2008-07-11
Do you have a special gaming mouse or a mouse that has drivers that are specific for that mouse? 

It sounds like it is confused. Does the mouse vendor have drivers for Ubuntu?

---

### Post by Animus Stealth on 2008-07-11
To be honest my video driver and most other drives won't load on ubuntu and i dont no what drivers i have or even why it dont work.

---

### Post by pluckypigeon on 2008-07-11
> **dj3hac said:**
> I agree with Pidgeon, Opera is just as good as firefox in every way in MY opinion. Its worth a try, to put the code in do it in the terminal. I'm not sure but you may have to sudo it. Type in "sudo su" in the terminal before pidgeons code it should ask you for the root password. Correct me if I'm wrong, it's been a while since I linux'd

Scratch all the sudo stuff I didn't know Pidgeon included it. XD

I do prefer Opera but for some reason I use Firefox though I must admit.

My sudo codes will work correctly

---

### Post by falcon61102 on 2008-07-11
Yeah, I have to agree with MyBrainReallyHurts and say that some drivers didn't load for your mouse.  Are any of your other USB devices acting strangely in Ubuntu or is it just the mouse.  If it is just the mouse then the problem is with the way Ubuntu is handling the mouse but if some of your other devices are acting up, then it could be that your drivers for your USB Controllers need to be looked at.

---

