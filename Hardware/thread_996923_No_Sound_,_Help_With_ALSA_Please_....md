---
title: "No Sound , Help With ALSA Please ..."
date: 2008-11-29
forum: Hardware
---

### Post by Dragon6 on 2008-11-29
Hello
I followed the steps exactly as they are in this : [http://ubuntuforums.org/showthread.php?t=551615](http://ubuntuforums.org/showthread.php?t=551615)

when I type the tar command for the ALSA driver , the response is :
tar: alsa-driver-1.0.15.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

What's going on ? Am I missing something ?
by the way I am running Ubuntu 7.10 on a Dell Vostro 1510 which has the Realtek ALC268 sound card , please help ... and I am also new to Linux

thanks 4 help or suggestion given in advance

---

### Post by Bucky Ball on 2008-11-29
Have you downloaded the alsa-driver-1.0.15.tar.bz2 file and are you in the appropriate directory (the same one as this .tar file)? Basically, the message is telling you the file doesn't exist in the directory you are in.

---

### Post by Dragon6 on 2008-11-29
Hi thanks 4 ur response 
yes I did  and located it on the "Desktop" and I made sure to type in the terminal : cd ~

---

### Post by Bucky Ball on 2008-11-29
Okay. Try putting in a terminal:

```
cd /home/username/Desktop
```... where 'username' is your username, then at the prompt:

```
dir
```and see if your .tar file is there. If it is, you should be good to go. :)

But, you should put that file in the directory you want to untar it first. That is one thing that is not mentioned on the page you posted.

---

### Post by Dragon6 on 2008-11-29
Ok you are right , it worked 
but I typed this command : ./configure     and the response in the terminal was : bash: ./configure: No such file or directory
Why ? sorry for getting you involved in this but I am kinda beginner
Thanks

---

### Post by Bucky Ball on 2008-11-29
Get involved in other people's (computer) problems is what we're here for (!) and you're welcome. I have been fiddling with Studio for the last few days, so ...

It might pay you to have a look at this site:

[http://alsa.opensrc.org/index.php/Quick_Install](http://alsa.opensrc.org/index.php/Quick_Install)

You need to put an option at the end of ./configure, ie:
```
./configure --with-sequencer=yes && make
```Check the link I've posted and that should help. :)

---

### Post by Dragon6 on 2008-11-29
Ok , it's compiled
but when I type : make install , the response is : 
install: cannot create regular file `/usr/include/sound': Permission denied
make: *** [install-headers] Error 1

what should I do now ?

---

### Post by Dragon6 on 2008-11-29
ok no need , I installed them but the result of : make install was :

WARNING!!! The mixer channels for the ALSA driver are muted by default!!!
**************************************************************************
You would use some ALSA or OSS mixer to set the appropriate volume.

is that done ? still no sound

---

### Post by Dragon6 on 2008-11-29
Please could anyone respond ?
I followed all the instructions correctly and finally I got in the terminal :
WARNING!!! The mixer channels for the ALSA driver are muted by default!!!
**************************************************************************
You would use some ALSA or OSS mixer to set the appropriate volume.

and still no sound , what's the next move ? 
Thanks

---

### Post by Bucky Ball on 2008-11-29
> **Dragon6 said:**
> Ok , it's compiled
but when I type : make install , the response is : 
install: cannot create regular file `/usr/include/sound': Permission denied
make: *** [install-headers] Error 1


You may have discovered this, but you possibly need to put 'sudo' before that command?:
```

sudo make install
```As for your last post, that is difficult because not quite sure of your setup. I'd say unmute them in the alsa mixer though. External hardware and what software you are trying to run etc. Some things need jack  to be running and using alsa also. You probably need to get a bit more detailed about your gear and what you are attempting to do at this point. Let us know and will get back to you tomorrow unless someone beats me to it. Have fun, off to bed for awhile ... :)

---

### Post by Dragon6 on 2008-11-29
Yes I did , and it's done , but still no sound and the result in the terminal right after the effect of sudo make install command was :

WARNING!!! The mixer channels for the ALSA driver are muted by default!!!
**************************************************************************
You would use some ALSA or OSS mixer to set the appropriate volume.

---

### Post by Bucky Ball on 2008-11-30
[http://alsa.opensrc.org/index.php/TroubleShooting#Troubleshooting_ALSA_Problems](http://alsa.opensrc.org/index.php/TroubleShooting#Troubleshooting_ALSA_Problems)

That might help, but starting to wonder: what exactly are you intending to use alsa for? The Realtek is a pretty generic card, not really high end, and should work just fine out of the box. You have some specific purpose behind all this?

The other point is, doesn't look like it is supported anyhow:

[http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)

More detail, please. :)

---

### Post by Bucky Ball on 2008-11-30
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

That page is informative and there is a tip for getting AC'97 going at the bottom of the guide from [SIZE=2]**webbca01**[/SIZE], just before the section called Advanced Guides.

---

