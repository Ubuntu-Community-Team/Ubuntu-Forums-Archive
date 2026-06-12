---
title: "How would I disable touchpad when I plug in mouse?"
date: 2009-03-25
forum: Hardware
---

### Post by peter_q on 2009-03-25
Say I wanna set up my baby to turn off the touchpad whenever I plug in my USB mouse. How would I do that?

I don't exactly know how to use ubuntu. At all... So I might need the Idiot's Guide version of instructions. :)

---

### Post by SirFalcon on 2009-03-25
System>pref>mouse>touchpad tab then disable

---

### Post by xMarine73 on 2009-05-14
Try the attached file.  It only requires one change to be made by you to match your system.  Instructions are included in the file.  Make the file executable and add it to your startup applications.

Hope it helps!

---

### Post by binbash on 2009-05-14
> **xMarine73 said:**
> Try the attached file.  It only requires one change to be made by you to match your system.  Instructions are included in the file.  Make the file executable and add it to your startup applications.

Hope it helps!

I will test this, thanks for the script

---

### Post by Mbradley1980 on 2009-05-15
well i got it to find my mouse but i can't get it to turn off my touchpad:) not sure..:(

---

### Post by xMarine73 on 2009-05-15
> **Mbradley1980 said:**
> well i got it to find my mouse but i can't get it to turn off my touchpad:) not sure..:(

You probably need to make sure SHMConfig is "on".  

See section (1) here: 
[Turn on SHMCONFIG]("http://ubuntuforums.org/showthread.php?t=271052&highlight=touchpad+detection")

---

### Post by Mbradley1980 on 2009-05-15
[http://ubuntuforums.org/showthread.php?t=271052&highlight=touchpad+detection](http://ubuntuforums.org/showthread.php?t=271052&highlight=touchpad+detection)

Now i tried doing that but well with my xcong file... 

```
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```^^^above is my file^^^
I don't see the right section in there and i copyed it all minus the "talking" in it... that is all commented out ... so i am notsure if i make a new section or somthing?:)  i do appreciate this

also i have found this and still don't work at all:(  not sure what i am doing wrong i edited the file and still nothing in there:(

[https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig](https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig)

---

### Post by xMarine73 on 2009-05-15
> **Mbradley1980 said:**
> Now i tried doing that but well with my xcong file... 

```
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```^^^above is my file^^^
I don't see the right section in there and i copyed it all minus the "talking" in it... that is all commented out ... so i am notsure if i make a new section or somthing?:)  i do appreciate this

also i have found this and still don't work at all:(  not sure what i am doing wrong i edited the file and still nothing in there:(

[https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig](https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig)


Alright, let's get some information about your setup there.   Toss the out output of the following from a terminal window:

synclient -l

and also the output of the following from a terminal window:

xinput list

---

### Post by Mbradley1980 on 2009-05-15
well i think i got it... i was roaming around and found some coding that allows me to do it... not sure exacly but it was on that last link i sent and it worked:) i can no or am able to use the sydeamon to do the work then i just added ur script with my mouse in there:)   to startup and vola

so after all ... both things i ended up doing and it worked one of them :) LOL  to scared to change them.... now i have to write a script that disabies my mouse when i have my synergy mouse on this pc:) LOL   but that will be a lil more difficult as that is not dealt with on the end i am thinking:(   anyways thnx and i hope this thread does help out someone.....   SO in the #7 post there are 2 ways to get the SHMconfig on ...

---

### Post by xMarine73 on 2009-05-15
Good to hear you got it working! :D

Don't be too skerred to change things, it's the only way you'll learn what you did right or wrong.  I do understand the concern though and at times I've felt the same way.

---

