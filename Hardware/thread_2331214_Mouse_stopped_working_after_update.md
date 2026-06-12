---
title: "Mouse stopped working after update"
date: 2016-07-19
forum: Hardware
---

### Post by petene31 on 2016-07-19
I updated the software of my lubuntu distribution recently during which the process stopped because of a power cut. Restarted the machine and completed update BUT the mouse doesn't work anymore although it is detected. If I boot from a live CD the mouse works fine. It is a dual boot system and the mouse also works fine in Windows.

Running - I think version 14.04

Any suggestions very gratefully received

---

### Post by QDR06VV9 on 2016-07-19
Yikes!.. and I am not sure if I can help here... but give us the output back from this in the terminal
```
xinput
```

---

### Post by petene31 on 2016-07-19
Output:

```
Virtual core pointer                              id=2    [master pointer (3) ]

         Virtual core XTEST pointer         id=4   [slave pointer   (2) ]
   
Virtual core keyboard                          id=3   [master keyboard (2) ]

         Virtual core XTEST Keyboard     id=5  [slave keyboard (3) ]
         Power Button                            id=6   [slave keyboard (3) ]
         Power Button                            id=7   [slave keyboard (3) ]
         AT Translated Set 2 Keyboard    id=8   [slave keyboard (3) ]
```

---

### Post by QDR06VV9 on 2016-07-19
Do you by chance have another mouse you can plugin?
And what kernel are you running? to find that out enter the below in a terminal
```
lsb_release -a && uname -r
```
And Paste back here...you probably don't have a mouse to this I know but type it back.
And is this a Laptop?

---

### Post by petene31 on 2016-07-19
Yes - you are spot on - I have to type everything seen in the terminal into this message which I have to send from a laptop as I cant launch and use the browser on the machine without the mouse. The problem is on a PC. I have tried another mouse and the same result - doesn't work in lubuntu but does from the lubuntu live CD and in Windows. The above command produces lines and lines of text so I'm hoping the last few lines below provide what you are after:

Distributor i.d. Ubuntu
Release:         14.04
Codename:     trusty
3.13.0-92-generic

Interestingly I tried the upgrade command to see if this resolved the iproblem but the command said I had the latest release - which clearly I haven't.

---

### Post by QDR06VV9 on 2016-07-19
The only thing I can think to try here as I seen no mouse detected by xinput is to upgrade your kernel 
But first see if we can get lucky with
```
sudo apt-get dist-upgrade
```
That will not take you to a Newer Release but fully upgrade all for trusty.
And if that has already been ran and "nothing to do" shows..we could add the wily HWE stack by way of
```
sudo apt-get install --install-recommends linux-generic-lts-wily
```
Which should upgrade your system to 14.04.4 but I do not know for sure if that will not have more problems for your Specs...It is running just fine here, but your mileage may vary.
So if you decide to take this route be sure to have a good back-up in place..IE Picture, Documents, Music,etc etc

---

### Post by petene31 on 2016-07-19
Brilliant - first solution 
sudo apt-get dist-upgrade worked perfectly and mouse started working during the upgrade.

Thanks a million

---

### Post by QDR06VV9 on 2016-07-19
You are very welcome!:)
And just to clean up a bit don not forget to run
]```
sudo apt-get autoremove
``` 
Thanks for marking as Solved also.
Kind Regards

---

