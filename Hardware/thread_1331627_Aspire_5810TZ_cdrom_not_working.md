---
title: "Aspire 5810TZ cdrom not working"
date: 2009-11-19
forum: Hardware
---

### Post by X1R1 on 2009-11-19
hi all, 

I installed ubuntu on my laptop without any problems, I can also remember that the drive USED TO work fine, but now (I think it was after upgrade) It wont read any CD that I put in it, I checked the group permission and I do have permissions to use cdrom drives, no Idea how to proceed from now on, I really need to burn some cds for a stuff we need at work so I desperately need the drive working.

Thanks in advance for the help.

2 things I forgot to mention:
- I installed jaunty on the laptop and recently upgraded to karmic

-The cdrom indeed shows on "My computer" but when I double click it does nothing (obviously with a cd in it)

---

### Post by Arlanthir on 2009-11-23
> **X1R1 said:**
> hi all, 

I installed ubuntu on my laptop without any problems, I can also remember that the drive USED TO work fine, but now (I think it was after upgrade) It wont read any CD that I put in it, I checked the group permission and I do have permissions to use cdrom drives, no Idea how to proceed from now on, I really need to burn some cds for a stuff we need at work so I desperately need the drive working.

Thanks in advance for the help.

2 things I forgot to mention:
- I installed jaunty on the laptop and recently upgraded to karmic

-The cdrom indeed shows on "My computer" but when I double click it does nothing (obviously with a cd in it)

I think you're just running into a known bug.
Don't open the CD tray in any way other than writing "eject cdrom" in the terminal. The next time you put something there, it should work (close the tray normally).

If you *ever* press the hardware button to open the tray, it won't work until you reboot. This is what happens to the majority of users with CDROM problems, as far as I know (me included) ;)

---

### Post by serxxx on 2009-11-23
> **Arlanthir said:**
> I think you're just running into a known bug.
Don't open the CD tray in any way other than writing "eject cdrom" in the terminal. The next time you put something there, it should work (close the tray normally).

If you *ever* press the hardware button to open the tray, it won't work until you reboot. This is what happens to the majority of users with CDROM problems, as far as I know (me included) ;)

This is interesting.  My wife's laptop (Acer Timeline 4810) was randomly dropping the wireless connection, and no matter what I tried, I couldn't get it to come back up without a reboot.  Just the other day, we *tenuously *linked it to the fact that she occasionally swipes her finger across the top of the keyboard -- thereby hitting the wireless button and turning it off.

It may just be coincidence, but I find the fact that:

[LIST]
[*]Hit the button to eject the drive, and the drive stops working, and
[*]Hit the wireless button to toggle the wireless, and the wireless stops working
[/LIST]
to be very similar.  And, no, pressing the wireless button never does turn the wireless back on; neither does reloading the ath9k module, or any combination thereof.  The strangest thing is that Linux can still see the device, and thinks that it is available -- it just stops working until the next reboot.  I wonder if the two issues are related to some kernel regression?

--- SER

---

### Post by Arlanthir on 2009-11-24
> **serxxx said:**
> This is interesting.  My wife's laptop (Acer Timeline 4810) was randomly dropping the wireless connection, and no matter what I tried, I couldn't get it to come back up without a reboot.  Just the other day, we *tenuously *linked it to the fact that she occasionally swipes her finger across the top of the keyboard -- thereby hitting the wireless button and turning it off.

It may just be coincidence, but I find the fact that:

[LIST]
[*]Hit the button to eject the drive, and the drive stops working, and
[*]Hit the wireless button to toggle the wireless, and the wireless stops working
[/LIST]
to be very similar.  And, no, pressing the wireless button never does turn the wireless back on; neither does reloading the ath9k module, or any combination thereof.  The strangest thing is that Linux can still see the device, and thinks that it is available -- it just stops working until the next reboot.  I wonder if the two issues are related to some kernel regression?

--- SER

My wireless switch works well, both in turning off and on the wireless O.o
Running Karmic final.

---

### Post by X1R1 on 2009-11-24
Same for wireless switch here...works perfect, and now that you say it, I HAVE NEVER used that command to eject the CD, I ALWAYS press the button, and I have noticed thatI have to press it like 3 times in order to get the tray open. I will try this out in a while and come back with results.

hope it works :popcorn:

**Just Tried it: WORKED!!! like a charm, what I did was I created a new panel (click the taskbar, add to panel, select custom launcher, and on the launcher properties type "eject cdrom"). That way you dont have to open the terminal everytime you need to eject :D**

thanks for the help

---

### Post by Arlanthir on 2009-11-24
> **X1R1 said:**
> Same for wireless switch here...works perfect, and now that you say it, I HAVE NEVER used that command to eject the CD, I ALWAYS press the button, and I have noticed thatI have to press it like 3 times in order to get the tray open. I will try this out in a while and come back with results.

hope it works :popcorn:

**Just Tried it: WORKED!!! like a charm, what I did was I created a new panel (click the taskbar, add to panel, select custom launcher, and on the launcher properties type "eject cdrom"). That way you dont have to open the terminal everytime you need to eject :D**

thanks for the help

Good to know :)
Remember to mark the thread as solved, using the thread tools!

---

### Post by X1R1 on 2009-11-24
you read my mind lol....I was about to :guitar:

---

### Post by exosyst on 2009-11-25
> If you ever press the hardware button to open the tray, it won't work until you reboot. 

Just as an aside but you can also sleep/suspend and wake up to get the drive redetected. It's still bloody annoying but less so than having to shut down and lose your work flow :D

Is there any ongoing work on this as from what I can see in dmesg it seems that the kernel thinks the drive has been disconnected and reconnected (broken). If anyone is tutoring on how to fix these sorts of hardware faults I'd love to put my name down.

---

