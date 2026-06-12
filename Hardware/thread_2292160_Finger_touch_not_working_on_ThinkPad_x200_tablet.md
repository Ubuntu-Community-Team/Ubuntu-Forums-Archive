---
title: "Finger touch not working on ThinkPad x200 tablet"
date: 2015-08-25
forum: Hardware
---

### Post by Nalavanje on 2015-08-25
Can't make finger touch work on my ThinkPad x200 tablet. Stylus works fine. Finger touch doesn't work at all, I get no response.

Here is some info

xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                       id=10    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Serial Penabled 1FG Touchscreen stylus    id=12    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Serial Penabled 1FG Touchscreen eraser    id=13    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Serial Penabled 1FG Touchscreen touch    id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=9    [slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                      id=11    [slave  keyboard (3)]



xsetwacom --list
Wacom Serial Penabled 1FG Touchscreen stylus    id: 12    type: STYLUS    
Wacom Serial Penabled 1FG Touchscreen eraser    id: 13    type: ERASER    
Wacom Serial Penabled 1FG Touchscreen touch    id: 14    type: TOUCH

---

### Post by Nalavanje on 2015-08-26
Does anybody have any input or experience with this problem? I'm doing it in Ubuntu Mate, but I tested it in Ubuntu 14.04 and it's doing the same thing.

---

### Post by Nalavanje on 2015-08-27
Bumping this the last time. Really hoping somebody has some experience or insight with this problem.

---

### Post by PaulW2U on 2015-08-27
Hi Nalavanje, sometimes, and you never know when, tagging the thread with the flavour that you're using doesn't help attract potential helpers so I've amended the thread title and removed the thread prefix for you. 

Hope that helps. :)

---

### Post by mörgæs on 2015-08-28
I have seen some bug fixes for finger touch lately, though not all for Thinkpads. Have you tried [15.10]("http://cdimage.ubuntu.com/lubuntu/daily-live/current/") (beta) in a live boot?

---

### Post by Nalavanje on 2015-08-31
Thanks PaulW2U. I appreciate the help.

> **mörgæs said:**
> I have seen some bug fixes for finger touch lately, though not all for Thinkpads. Have you tried [15.10]("http://cdimage.ubuntu.com/lubuntu/daily-live/current/") (beta) in a live boot?

I didn't. That might be a good idea. I'll let you know how did it go after I try it. Thanks.

---

### Post by Nalavanje on 2015-09-23
Finally I found out why finger-touch didn't work. This specific model ThinkPad X200 [FONT=arial, sans, sans-serif][COLOR=#000000]([/COLOR][/FONT][COLOR=#000000][FONT=arial]7449-9FU) does not include finger-touch by design. Some later X200 did, but not this one. [/FONT][/COLOR]

---

