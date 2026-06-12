---
title: "Nvidia Driver - Too Many Options!?!?!"
date: 2008-01-22
forum: Hardware &amp; Laptops
---

### Post by Rwild on 2008-01-22
OK.  I have a Nvidia GeForce 6600 GT and can not figure out which one to use.  Directly after install, I chose to use the propriety drivers.  However, I get lag on my screen when scrolling pages so I know it is not the ideal driver.  

I have had the right driver on a different Linux OS so I am wondering what the best one would be.  Thanks.:popcorn:

---

### Post by Mikecore on 2008-01-24
Here is a guide 

```


https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29


```

---

### Post by AsoSako on 2008-01-24
I recomend this little tool for you. 

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

I consider it the best thing that ever happened to graphics drivers. :D

---

### Post by Mikecore on 2008-01-25
> **agsimeonov said:**
> I recomend this little tool for you. 

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

I consider it the best thing that ever happened to graphics drivers. :D

sudo "apt-get" nvidia-glx* 

or just using the nice "restricted driver manager" works just fine.


Your tool is really not needed and could confuse "windows turds" that are trying out Ubuntu/Linux for the first time. IMHO. But whatever!

---

### Post by AsoSako on 2008-01-25
> **Mikecore said:**
> sudo "apt-get" nvidia-glx* 

or just using the nice "restricted driver manager" works just fine.


Your tool is really not needed and could confuse "windows turds" that are trying out Ubuntu/Linux for the first time. IMHO. But whatever!

I agree that the restricted driver manager works as well.  Nevertheless I do not agree that this is confusing.  All you do is click install the Nvidia driver, and it automatically downloads the Latest Nvidia driver from the Nvidia website and installs it.  I find it better because it does the configurations for you and it actually does use the latest driver which is very helpfull.  If you do it from the repositories on the other hand you don't get the latest drivers, and if you download the latest Nvidia driver yourself you would probably have to do some configurations that are too hard for first time Ubuntu users.  The Envy tool I suggested on the other hand does all of this in just one click of the mouse button.

These are just the facts, but I am not about to argue.  I simply like to have the latest and this thus suits me well.  You should do whatever suits you best too.

---

### Post by Mikecore on 2008-01-25
> **agsimeonov said:**
> I agree that the restricted driver manager works as well.  Nevertheless I do not agree that this is confusing.  All you do is click install the Nvidia driver, and it automatically downloads the Latest Nvidia driver from the Nvidia website and installs it.  I find it better because it does the configurations for you and it actually does use the latest driver which is very helpfull.  If you do it from the repositories on the other hand you don't get the latest drivers, and if you download the latest Nvidia driver yourself you would probably have to do some configurations that are too hard for first time Ubuntu users.  The Envy tool I suggested on the other hand does all of this in just one click of the mouse button.

These are just the facts, but I am not about to argue.  I simply like to have the latest and this thus suits me well.  You should do whatever suits you best too.

I understand what your saying, However you are going to find out the more you use linux that the "latest" drivers are not always the best drivers and sometimes they may even break your system. Does this tool provide for down grading if there is a problem?

---

### Post by AsoSako on 2008-01-25
I know about the problems that could occur, but I certainly have never had any with this tool since one of the things it does is help fix such problems during installation.  I do admit that the latest drivers could mess up something though.  As I said it is all a matter of choice.  In any case even if something does get messed up you could easily go in the xorg.conf and edit the errors youself.

---

### Post by Mikecore on 2008-01-26
> **agsimeonov said:**
> I know about the problems that could occur, but I certainly have never had any with this tool since one of the things it does is help fix such problems during installation.  I do admit that the latest drivers could mess up something though.  As I said it is all a matter of choice.  In any case even if something does get messed up you could easily go in the xorg.conf and edit the errors youself.

your correct I could and have edited xorg many times. however a new user may not even  know what xorg.conf is or how to go about editing it. If they happen to be GUI dependent like most 'new linux' users are once X server failed to start they wouldn't know what to do next besides booting back into windows. 

I want you to know I'm really not trying to be argumentative I just think its a bad idea to suggest new users or even younger users to use this tool. They don't understand what they are doing other then installing the latest drivers. And if or when they run into trouble 
this could possibly push them back to windows. or at lest cause them a lot of frustration.
I'm only suggesting they uses Ubuntu tools this way they learn one way that works that is also documented and that a majority of other users have used.

---

