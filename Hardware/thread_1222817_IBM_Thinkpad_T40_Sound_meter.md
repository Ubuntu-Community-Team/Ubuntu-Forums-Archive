---
title: "IBM Thinkpad T40 Sound meter?"
date: 2009-07-25
forum: Hardware
---

### Post by Geeky Warrior on 2009-07-25
Hello all, 
I am a new user to ubuntu. After toying around with various live CDs, I finally decided to dual install it on my laptop along with Win XP, especially since it throws them on the same partition, makes life a lot easier.

Anyway, I've had a lot of fun with this OS. A lot of headache free uses, and it fixed some hardware glitches I was experiencing with Windows (and I tried EVERYTHING to fix in windows, various drivers, reseating hardware,etc)

Anyway, I was wondering about the 3 sound buttons I have on my laptop, Vol Up/Down and mute.  They seem to control the speakers inside the laptop rather than affect the software sound mixer. Which is fine. I was wondering, is there anyway to make a meter for the speaker sound buttons. There was in XP, though I think a Thinkpad App is what made the meter work. Just so I could see how loud/quiet my speaker settings are so I don't have to adjust by ear.

Thanks!

---

### Post by egruber on 2009-10-29
I have a T40, too.  Prior to installing 9.03, a graphic with a horizontal bar was displayed when I pushed the volume buttons on the laptop.  The bar moved left and right as I adjusted the volume.

When I upgraded to 9.04 and now to 9.10, the graphic is gone.  And as the previous poster stated, it does not control the sound mixer.

This feature used to work properly.  Any idea what happened and I what I should do?  Thanks!

---

### Post by Aunt Phyllis on 2009-11-02
I have a thinkpad T60 and have the same problem.  My volume works but I don't have a meter to show me how loud or quiet I'm going.  Would love to know how to get that meter showing.  anyone gotta solution?

---

### Post by cssa1 on 2009-11-08
I suggest that those with this problem read towards the end of
[http://ubuntuforums.org/showthread.php?p=8269773#post8269773](http://ubuntuforums.org/showthread.php?p=8269773#post8269773) 

The code "echo ..../ibm/hotkey" should be added above the "exit 0" referred to by Bismark.

The solution worked for me when I did a fresh install of Ubuntu 9.10 on my T60.

If like me you needed guidance on how to log in as root, I suggest that you read [http://www.jonathanmoeller.com/screed/?p=1199](http://www.jonathanmoeller.com/screed/?p=1199)

Good luck

Chris

---

### Post by egruber on 2009-11-08
Wow.  That worked!  Thanks very much!

---

