---
title: "Ubuntu does not shut down properly any more"
date: 2009-03-06
forum: Hardware
---

### Post by beastrace91 on 2009-03-06
So I have been running ubuntu with out issue for awhile now but starting two days ago my laptop has developed a new error. When shutting down it appears that everything is working properly but after the splash screen disappears (and it is just at a black screen) the laptop is still running... I have to press and hold the power button (cold shutting it off) in order to get it to actually turn off... Is there some form of debug mode/code I can use to see where it is hanging while trying to shut down?

~Jeff

---

### Post by dwasifar on 2009-03-06
This is a shot in the dark, but try going to System>Preferences>Sound and on the Sounds tab, disable the Desktop>Logout sound.  

I have one system that has a problem shutting down because of a quirk in the sound hardware, no matter what OS is running, and that fixes it.  I don't know if that's your problem but it can't hurt to try.

---

### Post by clw3388 on 2009-03-06
Does it do the same in another tty or just X?
you might try to issue a shutdown command on another tty to see if it geterates any errors before shutting down..

I had this problem with my inital installations of 8.10 x64 and 8.10 32bit but after running the updates (specifically the kernel updates) issue stopped...

---

### Post by beastrace91 on 2009-03-06
What is the shut down command once I am in tty? I did just recently update my gfx drivers... I'll revert to the old version and see if the solves the issue.

As for updating, I'm running a custom 11-generic, but as I said it has been running fine for awhile now with out this issue so I am inclined to think it is the gfx drivers causing the issue... will try switching them later tomorrow and see if that helps.

thanks for the input,
~Jeff

---

### Post by beastrace91 on 2009-03-07
It appears the latest NVidia 180.3x drivers are causing the shutdown to hang... I tried both .35 and .37, guess I will just stick to the .27 for now.

~Jeff

---

