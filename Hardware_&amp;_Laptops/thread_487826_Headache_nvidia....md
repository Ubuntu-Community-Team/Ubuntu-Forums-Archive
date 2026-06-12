---
title: "Headache: nvidia..."
date: 2007-06-29
forum: Hardware &amp; Laptops
---

### Post by Tvinky on 2007-06-29
I know that there is more than 100 posts about it, but I don't understand one... 

I got nvidia 8600GT, and in restricted driver there is no driver for my video card. I tryed sudo apt-get install nvidia-glx, but x server didn't started. I have tryed to install driver from nvidia homesite, but i don't understand how to do it.

I tryed to do it by easy way, using envy - yeah, thats great. After restart I got direct render support and 3d. But after once more restart, again, x server didn't start.

So where is the joke in this? Why after restart linux don't understand thet I have installed driver already? Why this is that? Could somene tell me? (I have seen this to my friend too). Maybe if someone could tell where is the problem, and how to fix it - then all problems would be gone...

P.S Sorry about language.

---

### Post by NewJack on 2007-06-29
First off, do you have a separate /home partition?

If so, try this.  It worked for me:

-Perform a clean install of Feisty.

-Before installing/upgrading anything, get ENVY and install that.

-Run ENVY and follow the dialog and configure.

-Restart your box and then you can install any updates/programs you wish.

This is what took me 7 re-installations of the NVIDIA drivers and/or Feisty to figure out.  I know that it doesn't happen this way for everyone, but just something to try to get it to work.

---

### Post by stchman on 2007-06-29
> **Tvinky said:**
> I know that there is more than 100 posts about it, but I don't understand one... 

I got nvidia 8600GT, and in restricted driver there is no driver for my video card. I tryed sudo apt-get install nvidia-glx, but x server didn't started. I have tryed to install driver from nvidia homesite, but i don't understand how to do it.

I tryed to do it by easy way, using envy - yeah, thats great. After restart I got direct render support and 3d. But after once more restart, again, x server didn't start.

So where is the joke in this? Why after restart linux don't understand thet I have installed driver already? Why this is that? Could somene tell me? (I have seen this to my friend too). Maybe if someone could tell where is the problem, and how to fix it - then all problems would be gone...

P.S Sorry about language.

I was lead to beleive that the 8xxx series of nvidia cards are not supported in Feisty.

---

### Post by Tvinky on 2007-06-29
I was doing like you said, installed clearly and installed envy, after that updates, beryl etc.. All stuff worked until i restarted PC :)

But why after install I got direct rendering, and all 3d stuff, but after restart not. Why this is that? Whats happening after restart, can I stop it someway? I'm intresting in this, why after install i have 3d and all, but after reboot all is gone? Where the driver go? Thit is headache for me..

---

### Post by NewJack on 2007-06-29
Did you restart immediately after installing and configuring ENVY?  If not that may be the problem.  Don't do any updates/installs after ENVY until after restarting your computer.

---

### Post by Topfs on 2007-06-29
I did an update after install of envy and before I rebooted, wich ended with Xserver error, A reinstall of the nvidia through ENVY fixed all my problems, ENVY Rocks :)
(You need to add extra repositories to install ENVY)

---

### Post by NewJack on 2007-06-29
Glad to hear everything worked out.

---

### Post by mjthfx on 2007-06-29
> **Topfs said:**
> I did an update after install of envy and before I rebooted, wich ended with Xserver error, A reinstall of the nvidia through ENVY fixed all my problems, ENVY Rocks :)
(You need to add extra repositories to install ENVY)

ENVY ROCKS is an understatement!!!!!!!!!!

Let me recap my woes today

Today I see there are some upgrades and notice its some kernal updates and a nvidia update... so being fairly new to Ubuntu... I of course say... YES of course... so there I go I do my apt-get upgrade at 10:30 AM this morning....

I think to myself, before I continue, I should reboot being a kernel update and all...
](*,)

No more X... just a blank black screen with a cursor flashing in the top left hand of the screen

I tried everything... uninstalled, used lynx to surf the web and search the problem... all kinds of suggestions and guides i thought would help me.... 

:-\"

4:00pm... I am still staring at a blank screen... I am about to reinstall Feisty... then I went home and said to myself I GOT TO GET THIS GOING!

Found this little topic... looked at ENVY and said... oh well let me give it a try as I was dry of ideas, as was my buddy at work who is a more seasoned Linux user than myself.

Thank you to Whoever wrote ENVY... I ran it in text mode

```
sudo envy -t
```
[LIST]
[*] Selected 6elected 6 first to clean all of my failed installation attempts
[*] Then 1 to install the Nvidia driver... it asked me if I wanted to restart X...

Thanks again ENVY!
[/LIST]

---

### Post by Tvinky on 2007-06-29
Ohh, maybe it's after updates. Okey I'll try reinstall drivers with envy!

Edited: 
Thanks to all! It worked, now I'll know, that after updates (if update something with kernel), i'll need to reinstall drivers (; Yeah! No more headache!

P.S But all with this updates and reinstalling is bad for new users in Ubuntu (and linux). Because when they see the back screen and etc... They get back to windows ;( In some version of Ubuntu, there need to think on this. Like in openSUSE if i'm not wrong, there is some dialog in console but if 3d not working correctly, you are back in nv or vega. I think this is better than console D:

---

### Post by RevThain on 2007-08-05
I have to thank you also everyone...

I have had the same problems for weeks installing my nvidia drivers in Kubuntu 7.04. 
searching through the web, and multiple installs (10 or so) to no avail. This was the only post that actually solved the problem.

Hat's off to you all. :popcorn:

---

