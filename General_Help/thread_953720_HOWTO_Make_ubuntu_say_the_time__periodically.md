---
title: "HOWTO: Make ubuntu say the time  *periodically*"
date: 2008-10-20
forum: General Help
---

### Post by rbolio on 2008-10-20
So...thanks for reading this in advance... and well this is my first tutorial; so some feedback would be nice!....Enjoy!

Have you ever heard a friends mac say the time any given hour or w/e and wished YOU could have that! follow these steps to have this on your own Ubuntu machine (hey i use Hardy Heron....dont know about the rest).

1) Open terminal
2) type as follows!

  ```


 sudo apt-get install sox libsox-fmt-all saytime gnome-schedule


``` 

3) wait for install to finish...
4) once install is finished , in terminal type
  
```

sudo gnome-schedule
  
```

5)the gnome-scheduler window should now open;  click "new" and select recurrent task.

6) a smaller window will open,  fill it out as follows:
  > 
Description:  time say thing (or what you may call it)
command:   saytime  (plain and simple!) 

Next it says time and date; select advanced.
Minute: 0,30   (this is at what minutes will the command be run, change it if you wish)
Hour: leave an asterisk 
day:leave an asterisk
month: leave an asterisk
weekday:leave an asterisk



in the bottom, right above close you should see some black text saying 

[B]Preview:
at minute: 0, 30, every hour, every day of month every month[/B]


7) press apply
8) accept (or press dont show again) 

And You are done!!
Enjoy!

---

### Post by Rodney9 on 2008-11-03
Thank You :biggrin:

---

### Post by Rodney9 on 2008-11-04
Is it possible to make SayTime still say the time when music is playing ?

---

### Post by lenswipe on 2008-11-04
why would you want to do this? Dont know about you, but it would drive me insane!

---

### Post by dustman on 2008-11-04
> **lenswipe said:**
> why would you want to do this? Dont know about you, but it would drive me insane!

so if you're gaming like a maniac at 3 AM, it is a small reminder to exit everything and go to bed :D. (some Counter-Strike 1.6 servers already have this functionality, but hey, not all of us play CS).

Cheers!

Radu

---

### Post by Rodney9 on 2008-11-04
> **dustman said:**
> so if you're gaming like a maniac at 3 AM, it is a small reminder to exit everything and go to bed :D. (some Counter-Strike 1.6 servers already have this functionality, but hey, not all of us play CS).

Cheers!

Radu
 
Quite right, and there are many other reasons.

I know my sound system can play two sounds at once, as my new email wav sound will play during streaming audio, but not saytime.

So does anyone know how to get saytime to be heard at the same time as a game, music, etc is playing ?

Rodney.

---

### Post by Rodney9 on 2008-11-05
Does anyone know how to get saytime to be heard at the same time as music is playing ?

---

### Post by KeyserSoze93 on 2008-11-05
Why use saytime? Why not just run ```
date +%H:%M | espeak
```

That way you don't have to install any extra packages.

---

### Post by Rodney9 on 2008-11-05
> **KeyserSoze93 said:**
> Why use saytime? Why not just run ```
date +%H:%M | espeak
```

That way you don't have to install any extra packages.

$ date +%H:%M | espeak
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000

Espeak does not play also when music is, any other ideas ?

---

### Post by Rodney9 on 2008-11-07
Well I got Ubuntu 8.10 to tell me the time every half hour even if playing streaming audio, as I like to do.

I had to install 'Festival' and 'alsa-oss'

Then I used sudo gnome-schedule to set a recurrent task and set for 00,30 with the command -

echo "Its `date +\%l\%M\%P` oclock" | aoss festival --tts

Rodney

---

### Post by Rodney9 on 2008-11-07
> **Rodney9 said:**
> Well I got Ubuntu 8.10 to tell me the time every half hour even if playing streaming audio, as I like to do.

I had to install 'Festival' and 'alsa-oss'

Then I used sudo gnome-schedule to set a recurrent task and set for 00,30 with the command -

echo "Its `date +\%l\%M\%P` oclock" | aoss festival --tts

Rodney

Actually I did not have to use sudo, only gnome schedule from applications/system tools/scheduled tasks.

---

### Post by daleus on 2008-11-07
> **rbolio said:**
> 
Have you ever heard a friends mac say the time any given hour or w/e and wished YOU could have that!

not really.

But thankyou for making this, it would be useful for keeping track of time when playing games and looking at the clock and going "I have work in the..I mean, now"

---

### Post by rbolio on 2008-11-13
This thread should be in tutorials or how-to's  =X hahaha

---

### Post by DougieFresh4U on 2009-01-06
I had 'saytime' working at one time. It quit working, so I tried to run again but this is what terminal is saying and I don't understand what is the problem or how to fix. Any ideas would be great help.
Thanks
```
sox formats: can't open output file `/dev/audio': Permission denied
child process returned a non-zero status 2
Press ENTER to continue and close this window.
```

---

### Post by DougieFresh4U on 2009-01-07
Any one, please.

---

### Post by DougieFresh4U on 2009-01-08
Any 'gurus' up tonite, please

---

### Post by DougieFresh4U on 2009-01-08
sorry, Gotta 'bump'

---

### Post by DougieFresh4U on 2009-01-21
Is there any out there that can give me some kind of clue. The out put from terminal is a few post up. Maybe some one has a clue.

---

### Post by rbolio on 2009-01-21
ha i've had that outcome (sorry for delay...i've been busy)

im not sure what I did to solve it tho.... let me chec it and ill get you back later.... tomorrow.... =X

---

### Post by ActionParsnip on 2010-07-16
If you read the manpage for saytime you can use the -r switch

-r sec Repeat at the specified interval in background mode.

So gnome-schedule is NOT necessary you can have a startup item to run:

saytime -r 1800

and it will repeat every 30 mins. Life is so much simpler if you read the man pages sometimes kids.:popcorn:

---

### Post by Iowan on 2010-07-16
"Time" (no pun intended) for this thread to sleep.

---

