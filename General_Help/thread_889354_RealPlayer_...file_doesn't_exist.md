---
title: "RealPlayer ...file doesn't exist"
date: 2008-08-14
forum: General Help
---

### Post by utnubuuser on 2008-08-14
Hi -- I've recently downloaded the RealPlayer.bin file, and I've tried installing it by chmoding to a+x, but terminal responds with ...file doesn't exist!
Any idea why?
Thanks

PS file is sitting on desktop RealPlayer11GOLD.bin:)

---

### Post by prshah on 2008-08-14
> **utnubuuser said:**
> 
PS file is sitting on desktop RealPlayer11GOLD.bin

Must be a case/path mismatch.

In any case, right click the file on the desktop, then choose properties-permissions, and enable (check, tick) the execute permission..

---

### Post by Uchiha_madara on 2008-08-14
Listen this Link shows the same Problem with installation and 
file Existence this is the Link 

[http://ubuntuforums.org/showthread.php?t=878576](http://ubuntuforums.org/showthread.php?t=878576)


[SIZE="4"]Hint :[/SIZE] : When The Terminal ask you about the Path
of RealPlayer you must to Put Many Points :

1 - the file name after chmod is "Case Sensitive " With the File name

 for example  "RealPlayer11GOLD.bin".

2- the second thing you must to take care with,the Path of the Application

you must to put the clear path for it when the terminal ask you ?? 


good Luck man

---

### Post by utnubuuser on 2008-08-14
> **Uchiha_madara said:**
> Listen this Link shows the same Problem with installation and 
file Existence this is the Link 

[http://ubuntuforums.org/showthread.php?t=878576](http://ubuntuforums.org/showthread.php?t=878576)


[SIZE="4"]Hint :[/SIZE] : When The Terminal ask you about the Path
of RealPlayer you must to Put Many Points :

1 - the file name after chmod is "Case Sensitive " With the File name

 for example  "RealPlayer11GOLD.bin".

2- the second thing you must to take care with,the Path of the Application

you must to put the clear path for it when the terminal ask you ?? 


good Luck man



Thanks - I'll try the filepath thing.  I changed the permissions by right-clicking.

---

### Post by utnubuuser on 2008-08-14
This isn't working....

Terminal just keeps coming back with:  

chmod: cannot access 'RealPlayer11Gold.bin' : No such file or directory

I've tried it as sudo, I've tried as su, I've cd'd to Desktop, and when I do an ls -a, or ls -al, it still comes back with: No such file or directory.

I also made a short note in Gedit, and saved it as a .bin file, just to see if that would show up in terminal, and it's not listed or recognized it either.

????????????Any other ideas?:)

---

### Post by oldos2er on 2008-08-14
Where did you download Realplayer to?

---

### Post by utnubuuser on 2008-08-14
Hello Oldos2er  -- The Desktop

---

### Post by sayakb on 2008-08-14
```
chmod +x /home/yourusername/Desktop/RealPlayer11GOLD.bin
cd /home/yourusername/Desktop
./RealPlayer11GOLD.bin
```

---

### Post by utnubuuser on 2008-08-14
Great -- that worked.  I was missing the step of re-cd'ing to /home/myname/Desktop

now,...   Where is the best place to actually place this bin? 
I've read in a couple post somewhere that if you place it in the wrong directory, you end up having to access the player as su or sudo

oh, and do I need to make a file for it, or does the installer take care of that?

---

### Post by utnubuuser on 2008-08-14
Got it -- Thanks

---

### Post by sayakb on 2008-08-14
I have it in my /home/.realplay folder. Please mark the thread as solved.

---

### Post by oldos2er on 2008-08-14
> **utnubuuser said:**
> Great -- that worked.  I was missing the step of re-cd'ing to /home/myname/Desktop

now,...   Where is the best place to actually place this bin? 
I've read in a couple post somewhere that if you place it in the wrong directory, you end up having to access the player as su or sudo

oh, and do I need to make a file for it, or does the installer take care of that?

 The *.bin file is the installer; once you've run it and Realplayer is installed, you can delete it.

 Just FYI, if you install Realplayer by running "sudo ./RealPlayerGOLD.bin" it will install itself in /opt/real and be available for all users.

---

### Post by Uchiha_madara on 2008-08-15
> **LinuxIsInnovation said:**
> ```
chmod +x /home/yourusername/Desktop/RealPlayer11GOLD.bin
cd /home/yourusername/Desktop
./RealPlayer11GOLD.bin
```



In this case when you access the terminal you must to Log in as roOt


Type : > passwd root
then change the password

then Type > su root
then type the new password that you configured


Now you can access terminal....... when I open the terminal
the first thing I make i access the terminal as root

good Luck

madara:KS:KS:KS

---

