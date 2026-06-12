---
title: "How to install my drivers?"
date: 2008-11-15
forum: General Help
---

### Post by k00ks on 2008-11-15
Im a total noob when it comes to linux. so help me out here. Im trying to install my ATI drivers and sound drivers but i dont get all these kernal things and codes. [Found this tutorial]("http://wiki.linuxquestions.org/wiki/Installing_ATI_drivers") but I am totally clueless on all of it.Can someone help me out here(questionmark. sorry my keyboard is acting weird right now. i type quetion mark it comes out as É)

[Picture]("http://i33.tinypic.com/2qum70p.png") 

also another thing, whats the default session to be in. I previously had trouble logging in because Im selling this comupter tonight and so i took out my graphic card for my new rig. Then when i try logging in, it would accept but then go pale screen, black, then back to login page. im currently on the first session after the option (previously loaded). Is that right. I logged in after i did this ATI thing linux told me to do called restricted drivers. 

thanks to all

PS. I want to install Avira AntiVir as well. And again its like these kernal things... not the same as windows

---

### Post by Mardoct909 on 2008-11-15
> **k00ks said:**
> (questionmark. sorry my keyboard is acting weird right now. i type quetion mark it comes out as É)

Did you set the keyboard to Canada? If you did, you want the US layout. The Canada one is for French Canadians.

You can also install the ATI driver easily through a program called envy. Run this in a terminal to get it.

```
sudo apt-get install envyng-gtk
```

---

### Post by k00ks on 2008-11-15
> **Mardoct909 said:**
> Did you set the keyboard to Canada? If you did, you want the US layout. The Canada one is for French Canadians.

You can also install the ATI driver easily through a program called envy. Run this in a terminal to get it.

```
sudo apt-get install envyng-gtk
```

Thanks so much for the reply. I'm downloading right now. 

Edit: Got everything working now. Perfect. Thanks so much!

---

### Post by Mardoct909 on 2008-11-15
Oh, poopcicles. I forgot envy doesn't work on Intrepid yet.

Ok, we need to know what card you have... Do you know?

As for flash, that's a known bother for everyone with Ubuntu. Try this:

[http://tombuntu.com/index.php/2008/10/16/install-adobe-flash-player-10-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/16/install-adobe-flash-player-10-in-ubuntu-804-and-810/)

And as a note, Linux NEVER uses .exe files. When executables are needed, they're usually .run or .sh . 

Now, do you know what sound car you have?

---

### Post by k00ks on 2008-11-15
> **Mardoct909 said:**
> Oh, poopcicles. I forgot envy doesn't work on Intrepid yet.

Ok, we need to know what card you have... Do you know?

As for flash, that's a known bother for everyone with Ubuntu. Try this:

[http://tombuntu.com/index.php/2008/10/16/install-adobe-flash-player-10-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/16/install-adobe-flash-player-10-in-ubuntu-804-and-810/)

And as a note, Linux NEVER uses .exe files. When executables are needed, they're usually .run or .sh . 

Now, do you know what sound car you have?

Actually. I got flash working. I installed it through youtube when it says i'm missing flash. i download. still nothing. so i used envy (i had installed the wrong version before, didn't follow that code you gave me. tsk tsk)and it installed my drivers fine. now my sound is working as well.
Only thing is now, I can't get shockwave to work.

Thanks

Edit:
Aiie. Now i got a problem
I'm trying to get shockwave to work and following [This]("https://help.ubuntu.com/community/Shockwave") tutorial but when it gets to
this:
Now you need to configure mozplugger to use the Windows version of Firefox for Shockwave files. From a terminal, type:

sudo gedit /etc/mozpluggerrc

Add the following two lines to the end of the file:

application/x-director: dir,dcr,dxr,cst,cct,cxt,w3d,fgd,swa: Macromedia Director file
swallow(firefox.exe) fill: wine "C:\\Program Files\\Mozilla Firefox\\firefox.exe" -chrome "file://Z:$file"


part it won't work. I can't get into the mozpluggerrc file. When I try to get it in terminal, it says that /ect can't be found. Any ideas?

---

### Post by Mardoct909 on 2008-11-15
If you just want all this multimedia stuff to work, try Linux Mint. It's pretty much Ubuntu with the multimedia stuff slapped on it. (And some other things.)

That requires reinstalling the drivers, but that isn't a huge deal.

---

