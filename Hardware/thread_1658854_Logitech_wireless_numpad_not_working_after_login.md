---
title: "Logitech wireless numpad not working after login"
date: 2011-01-03
forum: Hardware
---

### Post by bmach on 2011-01-03
Hey guys,

I have a strange situation. I have a logitech wireless numpad ([N305 - click for link]("http://www.logitech.com/en-au/434/6355")) That works absolutely fine at the login screen - as in when I press numbers they show up in the username text field. When my wife logs in as her username the numpad continues to work for her. However, as soon as I log in the numpad stops working and does funky things like paste text when I press the buttons.

Any ideas as to what could be going wrong here that would only affect a single user? Which config settings should I look at?

The laptop I have is a HP Pavilion DV6.

Thanks for your help.

---

### Post by bmach on 2011-01-03
Also I forgot to mention I'm using Ubuntu 10.10 - the Maverick Meerkat - released in October 2010

---

### Post by Fafler on 2011-01-03
How does it connect to your PC? USB reciever, bluetooth...?

---

### Post by bmach on 2011-01-03
USB receiver. Thanks for helping

---

### Post by Fafler on 2011-01-04
And this isn't just a silly issue of you having pressed the numlock key or something?

I don't really have any idea on what configuration file could be the problem. You could run xev to confirm the keyboard sends the same codes with both users, but i'm not really sure it will get us any further.

---

### Post by bmach on 2011-01-04
Hehehe thanks Fafler. I thought it was something silly like that myself until I realised my HP laptop keyboard doesn't even have a numlock key or setting. But maybe Ubuntu has decided it's on for me and not my wife for some reason...

I used xev as you suggested. The output when pressing the "7" key on the numpad is different between me and my wife. I've attached the two files to do a compare in what ever diff tool you like.

**Me**
```
KeyPress event, serial 73, synthetic NO, window 0x5400001,
    root 0xa6, subw 0x0, time 77712169, (-806,-77), root:(352,291),
    state 0x10, keycode 77 (keysym 0xff7f, Num_Lock), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

**Wife**
```
KeyPress event, serial 37, synthetic NO, window 0x4400001,
    root 0xa6, subw 0x0, time 77883552, (-199,-30), root:(941,148),
    state 0x10, keycode 79 (keysym 0xffb7, KP_7), same_screen YES,
    XLookupString gives 1 bytes: (37) "7"
    XmbLookupString gives 1 bytes: (37) "7"
    XFilterEvent returns: False

KeyRelease event, serial 37, synthetic NO, window 0x4400001,
    root 0xa6, subw 0x0, time 77883616, (-199,-30), root:(941,148),
    state 0x10, keycode 79 (keysym 0xffb7, KP_7), same_screen YES,
    XLookupString gives 1 bytes: (37) "7"
    XFilterEvent returns: False

KeyPress event, serial 37, synthetic NO, window 0x4400001,
    root 0xa6, subw 0x0, time 77883912, (-199,-30), root:(941,148),
    state 0x10, keycode 77 (keysym 0xff7f, Num_Lock), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

Weird eh? I googled searched how numlock works on my keyboard but found nothing.

---

### Post by bmach on 2011-01-04
I just found and installed the GKrellM plugin "gkrellm-leds" which allows me to see the status of my numlock, caps lock, and scroll lock on the keyboard. Numlock is definitely off for me as a user. Even when I turn it on (can do this via the plugin) the numpad still doesn't work :(

---

### Post by Fafler on 2011-01-04
One thing that is quite odd is that the input seems to come from another device. I don't know what the "serial" value refers to, but i could imagine it's the raw HID device.

Have you been to Keyboard settings and made sure the "Pointer can be controlled using the keypad" option is unchecked?

Similar threads:
[http://superuser.com/questions/224753/numlock-is-so-weired-in-ubuntu](http://superuser.com/questions/224753/numlock-is-so-weired-in-ubuntu)
[http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/numlock-issue-with-a-usb-keyboard-on-my-acer-travelmate-laptop-677415/](http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/numlock-issue-with-a-usb-keyboard-on-my-acer-travelmate-laptop-677415/)

And here seems to be a bug report on the same problem:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/182421](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/182421)

The bug report suggests installing numlockx and running numlockx off

---

### Post by bmach on 2011-01-04
> **Fafler said:**
> Have you been to Keyboard settings and made sure the "Pointer can be controlled using the keypad" option is unchecked?

Ahhh thank you so much! This fixed my problem and I have a numpad again! As soon as I unchecked that checkbox the numpad works fine. I have no idea when or why I would have checked the checkbox. Probably when I was playing around with the settings prior to even buying the numpad.

Thanks again Fafler - your help was much appreciated.

---

### Post by Fafler on 2011-01-04
You're very welcome. I should learn to use the GUI more. It should have been the first to make you look.

---

### Post by luc765 on 2012-10-16
Hello,

Follow the tuto given by this URL to have your logitech N305 working 100%.
Its in french but easy to understand

[http://users.skynet.be/linux-rixensa...es.html#keypad](http://users.skynet.be/linux-rixensa...es.html#keypad)

Lucien

---

### Post by luc765 on 2012-10-16
Hello,

Follow the tuto given by this URL to have your logitech N305 working 100%.
Its in french but easy to understand

[http://users.skynet.be/linux-rixensart/3_peripheriques.html#keypad](http://users.skynet.be/linux-rixensart/3_peripheriques.html#keypad)

Lucien

---

### Post by lisati on 2012-10-16
From the forum code of conduct:
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

