---
title: "Linux, X10 Home Automation, and BPL"
date: 2010-10-03
forum: Hardware
---

### Post by souta95 on 2010-10-03
I have been seeing articles around about using X10 home automation stuff with Linux.

I was given a starter kit from a friend.  It is an old IBM Home Director set from the mid 90's (Controller model 75H8381).

My first (and primary) question is that if I am able to get it set up would it mess with my Internet connection?  I have IBEC BPL, broadband over powerline.

Secondly is there relatively easy to use GUI software that will work with Ubuntu 10.04?  (I do plan on updating once 10.10 comes out, though).

I read that Heyu will work will work with this controller, is there a GUI front-end for it?

I had put it away because the software that came with it gave an error about not running on an IBM computer, and the software from X10's website wouldn't work the controller.

---

### Post by P4man on 2010-10-03
Here is a front end:
[http://domus.link.co.pt/](http://domus.link.co.pt/)

This link may also interest you if you havent seen it yet:
[http://www.linuxha.com/athome/index.html#Software](http://www.linuxha.com/athome/index.html#Software)

---

### Post by souta95 on 2010-10-03
Thanks, that answers part of it, now I just need to find out if it is safe to use with BPL.

---

### Post by efflandt on 2010-10-03
I used to play around with that a long time ago when serial ports were still common on PC's.

I did find a gui app somewhere that used xfig.  You could make a diagram of your home and where the X10 units were.  And I think you could control them from there.  But I didn't think it was practical to run a computer just to control the lights and the computer control unit eventually failed.

So now I just use a Plug'n power unit from Radio Shack that can individually tell multiple X10 units what time to turn on/off, and some of the X10 modules also have wireless remotes, so I can turn them back on if the lights go out when I am still up.

X10 is probably a totally different frequency than powerline networking, and since they only need to send brief signals to switch on or switch off, it would not interrupt you for long if they interrupt you at all.

---

