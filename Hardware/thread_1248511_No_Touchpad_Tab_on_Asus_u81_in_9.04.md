---
title: "No Touchpad Tab on Asus u81 in 9.04"
date: 2009-08-24
forum: Hardware
---

### Post by Khidr9 on 2009-08-24
Hey.   So, I've been spending the past few months transitioning my house to an allbuntu paradise, and everything has been working out of the box on all of my computers.  I figured it was time to bring my fiancee in on the fun, so needless to say, her laptop is the first out of 5 computers to have a problem. :)   

The problem is this.   It's an Asus U81a laptop (u80 series, that I think is custom configured for best buy).  It has an Elantech touchpad with multitouch features.  

The Touchpad is basically working in Jaunty (and Karmic), including two finger scrolling, and three finger "Right click," but, my fiancee wants to be able to disable the touchpad while scrolling.   "No Problem" I tell her as I show her the touchpad tab on my eee pc.  Problem is, there is no touchpad tab on her system.   Trying to install gsynaptics, touchfreeze, gpointing devices, etc...  all fail, with the message that it could not initialize because I need to enable shmconfig to 'true' in xorg.conf (which does not exist, probably because it's no longer necessary with these newer builds).  

From what I can tell, it's just not recognizing the touchpad as a touchpad.   
Here's the output from my xinput list: 

```
"Virtual core pointer"    id=0    [XPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
"Virtual core keyboard"    id=1    [XKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"AT Translated Set 2 keyboard"    id=2    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Video Bus"    id=3    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Macintosh mouse button emulation"    id=4    [XExtensionPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
"ImPS/2 Logitech Wheel Mouse"    id=5    [XExtensionPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1

```

Anyhow, I appreciate any help you guys can offer, I've spent many hours already and am just plain stumped as to how to get it to recognize the touchpad as one so I can get the touchpad tab, and since it's not recognizing it correctly, why is it working well with all of the multitouch features.  

Thanks in advance.   I'm typing this on it right now, so let me know if you need anything else.

---

### Post by jama999 on 2009-09-16
I have this same problem, ever figure out how to get some control of the touchpad on the U81a?

---

### Post by xonecas on 2009-10-01
I have the same issue !

---

### Post by dusanyu on 2009-10-04
known bug and has been for a while 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/123775](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/123775)

only wish I known about this before I bought the U81

Sadly The Comunity associated the elantech touchpad with netbooks so don't expect much movement on this driver for real computers

---

### Post by jama999 on 2009-10-12
> **dusanyu said:**
> known bug and has been for a while 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/123775](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/123775)

only wish I known about this before I bought the U81

Sadly The Comunity associated the elantech touchpad with netbooks so don't expect much movement on this driver for real computers

I read elsewhere the distro "Linux MInt" has the proper drivers for this - I dont know a thing about it other than its Ubuntu based, but Im actually thinking of giving it a try since the touchpad thing makes the computer almost unusable.  Anyone else used this distro?

J

---

### Post by ekoecho on 2009-10-12
I'm having the same issue on a Dell 11z. It also has an Elantech touchpad which seems to be incorrectly detected as a Logitech mouse.

---

### Post by dusanyu on 2009-10-20
> **jama999 said:**
> I read elsewhere the distro "Linux MInt" has the proper drivers for this - I dont know a thing about it other than its Ubuntu based, but Im actually thinking of giving it a try since the touchpad thing makes the computer almost unusable.  Anyone else used this distro?

J

intriguing, downloading now to give it a try

---

### Post by jama999 on 2009-10-25
> **dusanyu said:**
> intriguing, downloading now to give it a try

So whats the verdict?

---

### Post by jama999 on 2009-10-29
> **jama999 said:**
> So whats the verdict?


[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/418282]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/418282")

I saw in this bug report this is a problem acknowledged by Ubuntu support and at the time (9.10 alpha release) still existed in 9.10.  Can whoever installs 9.10 first and is watching this thread please post whether or not this is resolved?  I was thinking seriously about downloading 9.10 and installing from scratch if this is the case.

Thanks in advance,

J

---

### Post by dusanyu on 2009-10-29
> **jama999 said:**
> So whats the verdict?
Same problems in Mint

---

### Post by jama999 on 2009-11-11
BUMP - If anyone has had any success with this laptop/touchpad combination, I am all ears. I am working with the canonical team to try to get a kernel patch, but the process has stalled and I figured an appeal to the forums is always a good next step.

Anyone get anywhere with this, or should I just sell the laptop now?

TIA,

J

---

### Post by asaturn on 2009-12-15
identical problem on an asus UL50AG

---

### Post by Mishootka on 2009-12-16
Got the same problem with ASUS K40IN :(

---

### Post by Bender2k14 on 2010-04-28
I think we have found the solution to this problem.

See this bug report:
[http://ubuntuforums.org/showthread.php?p=9175201#post9175201](http://ubuntuforums.org/showthread.php?p=9175201#post9175201)

...and this thread:
[http://ubuntuforums.org/showthread.php?p=9175201#post9175201](http://ubuntuforums.org/showthread.php?p=9175201#post9175201)

---

