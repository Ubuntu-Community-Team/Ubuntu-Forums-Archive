---
title: "F1 key stuck - remapping the boot?"
date: 2009-12-19
forum: Hardware
---

### Post by lil.one on 2009-12-19
Hi everyone,
This is the 3rd day I am trying to get the Ubuntu 9.10 installation work on my EEE PC 901 netbook. So please forgive me for the beginner questions.
The problem is the following: Due to the crappy quality of the keyboard in the 901(i read about more people having this issue) my F1 key is stuck, it acts as if its being pressed all the time, so in windows it would open million of help windows. I removed the key and tried to play with whats under it, but with no sucess. I found a software solution for windows, but now I would like to have one for Linux.
xmodmap -e 'keycode 67='
works, however. this is only after loading the x thingie(or whatever its called, the graphical user interface). The problem is that when Linux is trying to load, the F1 is pressed all the time, and aborts some i-guess-important commands or processes. So if I am rebooting the computer, the touchpad would not work(and probably some other things). The solution I found for that was basically clicking on one of the other keys, like, a or b. That way everything is loaded correctly and I can work with it.
But I am wondering if there is any way to "really" fix it. I mean, there must be a file which is used for loading Linux and all the components, and if i could enter a remapping command in the beginning of this file, i would not have to do the "a trick". 
Oh, important to mention, if i am clicking CTRL + C while linux is loading, and then typing the xmodmap command, it would give me the error: 
xmodmap: unable to open display ''

so there must be another way to disable the F1 key...


Hope someone can help me and thanks alot in advance!

---

### Post by moddie666 on 2009-12-19
Hi.

So the key is still being "pressed" all the time?

If so:

I'd physically take the Netbook apart, as far as you need to get to the keyboard. Anything else would be a semi-permanent solution at best.

Just out of curiosity, how did you do it in Windows?

greetings
/moddie

---

### Post by lil.one on 2009-12-19
Wow, that was quick, thank you!!

Yes, the key is pressed all the time, its funny, before i was playing with xmodmap to check that it really functions, i changed it to xmodmap -e 'keycode 67=b'
within few seconds the terminal was full of bbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbb
;)

in windows i first changed in the registry the help program pointer to another very-light program, that way i had few minutes to breath after loading windows, otherwise it will just open million trillion help windows before i can even do something. Then I used an application called sharpkeys(SharpKeys is a Registry hack that is used to make certain keys on a keyboard act like other keys.) mapped the F1 to nothing and voila!

I dont have the hardware knowledge to taking the laptop apart, right now I have a functioning(up to 1 thing) laptop, and wouldnt like to lose it just because I didnt know what x or y is going to do. Because of the warranty rules in Germany I cant send it to be fixed although its only one year old, not to mention that after taking the key out, I might have void the warranty.

Any one? Ideas?:(

---

### Post by moddie666 on 2009-12-19
Hi.

Sorry for not being more helpful, but if you still have Warranty, I'd just get it replaced.

If you still want a software solution see if there is something you can add to a startup script that would be run before X initializes, but thats not really my area of expertise.

I have however another "low-tech" idea:
I assume the key you removed left behind a hole. If so try fiddling around in there with a toothpick (!nothing metallic because you dont want to damage anything!) and see what you can "dig up".

greetings
/moddie

---

### Post by lil.one on 2009-12-19
Tried removing some other keys and playing arround the area, and it seems more and more that it is done randomly/it is a problem not in the key itself but in the interface between the key to the other components.

Photo attached:) so unfortunately no low-tech solution.

Do you know how the start up script is called? that is actually what im trying to find out, so maybe i can google it.

Thanks so much for your help!

---

### Post by lil.one on 2009-12-19
this is btw how the xev output is looking like:


KeyPress event, serial 36, synthetic NO, window 0x4200001,
    root 0x104, subw 0x0, time 2208864, (-82,417), root:(440,468),
    state 0x0, keycode 67 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x4200001,
    root 0x104, subw 0x0, time 2208897, (-82,417), root:(440,468),
    state 0x0, keycode 67 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 36, synthetic NO, window 0x4200001,
    root 0x104, subw 0x0, time 2208897, (-82,417), root:(440,468),
    state 0x0, keycode 67 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 36, synthetic NO, window 0x4200001,
    root 0x104, subw 0x0, time 2208900, (-82,417), root:(440,468),
    state 0x0, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x4200001,
    root 0x104, subw 0x0, time 2208931, (-82,417), root:(440,468),
    state 0x4, keycode 67 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 36, synthetic NO, window 0x4200001,
    root 0x104, subw 0x0, time 2208931, (-82,417), root:(440,468),
    state 0x4, keycode 67 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False



so i wonder if this might make the computer slower - if it has to ignore all the time input.

---

### Post by moddie666 on 2009-12-19
You should be fine just searching for "linux startup scripts" or something similar, there are several different ones, but i am not really familiar with the Linux startup procedure.

but they are:
[http://luv.asn.au/overheads/linux-startup.html](http://luv.asn.au/overheads/linux-startup.html)

Well, I wish you the best of luck.

P.S.
Scheiss flache Laptop Tastaturen! ](*,)

---

### Post by moddie666 on 2009-12-19
might make it a little slower, but as long as the button doesnt really do anything, i wouldnt worry

---

