---
title: "[SOLVED] Can't login (root or user)"
date: 2008-07-27
forum: General Help
---

### Post by Fredizdman on 2008-07-27
Okay, so I was having some problems getting an emulator to install, and after multiple tries at different solutions I got a little impatient. I began copying and pasting code without taking quite as much time to sort through it as I usually do....bad I know.

Anyway, the code had a

```
sudo cp /lib/* /lib32/
```

or something very similar which of course copied alot of unneeded files along with the ones it was meant for and ended up breaking a few things including wine. Wine complained about a library file being a 64 bit version instead of a 32bit version. I then decided to delete the library and then find out where I could redownload and copy in the 32 bit version of the file (it was libdl.so.2)....I deleted the instance of the file from both 

/lib   and
/lib32

This was another _**big mistake**_. Apparently, that file is needed for absolutely everything! I couldn't use adept or apt-get to install the new library because it depended on the old one.I tried rebooting and boot failed, even to recovery mode or whatever,so I booted to live cd, downloaded the 64 bit package that contained the 64 bit version of the file, extracted it, and copied to my hard disk installation. ( at /lib ) not (/lib32)

Great, everything works way past where it failed before, all services start...until login.

Kdm doesn't start and I am brought to a tty login.

No matter what I type, nothing happens. For example

```
fredizdman-desktop login: fredizdman

Ubuntu 8.04.1 fredizdman-desktop tty1

fredizdman-desktop login: fhrfrfyfrh

Ubuntu 8.04.1 fredizdman-desktop tty1

fredizdman-desktop login:
```

This loops over and over again, never asking for a password.

I'm not sure how much of that information was needed...but since I'm not sure how I broke it, I thought the entire procedure needed to be lined out.
I know I still don't have the proper 32 bit version of the file, but I'm pretty certain it shouldn't be needed to login.
Should it? 

Anyone know what I did?

---

### Post by Fredizdman on 2008-07-27
anyone? I know bumping can be considered rude, but I'm kinda stuck here....I'm going to try to get the 32 bit version put into (/lib32) when I get a chance between work and moving....and then I'll post again if it works.

---

### Post by coffeecat on 2008-07-27
Firstly, bumping isn't considered rude at all, as far as I know. This is a busy forum, and unanswered posts easily get swamped by the deluge of new threads. You have to bump now and then. I think the problem is when impatient adolescents bump after about half an hour. Yes, it does happen!

Anyway, is that a 64-bit install you've got there? I should imagine the problem is not just with libdl.so.2. I should think other libraries have been affected, and you've probably got a problem with different release versions of libraries being expected by various applications. My first thought was to boot up the live CD and simply copy in the contents of /lib and /lib32 from the live environment, which would re-overwrite the libs that were overwritten when you did your cp. But that won't work, because you'll end up with release version incompatibilities - you've no doubt updated your system several times since the CD was realeased.

My next thought was, have you a spare partition to which you could make another (temporary) install? Or perhaps on another machine, although it would have to be however many bits compatible with the first machine. If you have, do an install and update it completely. Then copy the contents of /lib and /lib32 (or whatever folders you think were affected) from the new install to the old install. Hopefully this will restore your system libraries to a state in which you can at least boot up. If you get errors thereafter with apps complaining about missing or incompatible libraries (including apps that are on the old install but not the temporary one), you can fix them one at a time with apt-get.

Goodness knows whether this would work, but it's the best I can offer.

---

### Post by Fredizdman on 2008-07-27
Yes, it is a 64 bit machine.That sounds like it would probably fix my problem, unfortunately I don't have much hard drive space. So I'm going to work on clearing up some space for an additional install. Hopefully I will not have to install many apps to get things working. I'll let you know as soon as I get things sorted out. Thanks for your help!

---

### Post by Fredizdman on 2008-07-28
Okay, things are getting better. Things have taken an interesting turn though. I still am unable to login with my main username. However, I downloaded a 64 bit livecd and booted to it, installed ia32-libs and copied /lib and /lib32 to my hard drive installation. Now the GUI login prompt (in my case kdm-kde4) does come up. When I type in my main username, however, it simply flashes and returns to the login screen. Pretty much the same thing that happened before only graphical this time. I do have a 2nd user, one I've never really logged in as and I didn't think of at the tty prompt. I am able to login under this name. I suppose its a startup script that runs on the other user that is causing X to reboot. Yes, I am running Compiz, and I guess my first shot at this will be to disable compiz on startup and then boot back in to fredizdman.

If that doesn't work...is there a log that would show me what process is killing X? I don't think any of the logs I'm familiar with show running processes when X dies.

EDIT:: So disabling compiz didn't work. Another thing, I can login to both root and fredizdman at a tty login now, so I am really confused I thought for sure the tty login and the GUI login problems were related, but it seems one of them is fixed now.
My konsole will not start either. If just disappears after loading. Unfortunately my normal method of starting it from a terminal is kinda impossible...

---

### Post by coffeecat on 2008-07-28
Would the /var/log/Xorg* logs be of any use? I can't think of any others offhand.

But I've got another idea. :) Have you got administrative rights with that secondary account? If you have, create a third account (also with administrative rights) and then copy .kde and whatever other config files you need from your primary account /home into the third account home. This should transfer all your configurations and settings, but you'll have to make sure not to accidently activate compiz in the new account, and not to copy config files that might simply transfer the log in problem.

Now log in to the new third account, and if everything is satisfactory, delete the original fredizdman account and create a new one. Now copy .kde, blah blah from the temporary account into the fresh fredizdman /home. You'll need to do a bit of chowning along the way.

I suppose you could do the .kde copy and everything else into the secondary account, but I would prefer to work at arm's length as it were.

Of course, you could always reinstall. :wink: Might be quicker. :p

---

### Post by Fredizdman on 2008-07-28
Thanks for all your help, but I think I am going to take your last bit of  advice. I think I had things headed in the right direction, but a good fresh install wouldn't hurt anyway, I was getting tired of the way it looked anyhow. I'm going to do a fresh install. Any idea if just copying ~/.wine will save all of my wine installed programs? Or is there something else I need to copy? All of the linux programs aren't a problem reinstalling, tis the beauty of package managers!

---

### Post by Fredizdman on 2008-07-29
Okay, so a fresh install is working wonderfully, I think it may have been a good idea anyway. Problem Solved.

---

