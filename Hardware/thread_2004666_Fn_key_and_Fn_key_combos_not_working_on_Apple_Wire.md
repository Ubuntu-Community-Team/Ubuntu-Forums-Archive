---
title: "Fn key and Fn key combos not working on Apple Wireless Keyboard"
date: 2012-06-16
forum: Hardware
---

### Post by ramplank on 2012-06-16
I'm trying to set up my Apple Wireless Keyboard with my Kubuntu systems. These are PC hardware powered by Intel Atom and Intel i5 respectively. The keyboard has a US keyboard layout and has model number A1314 written on the back. It takes two AA batteries.

I have a 10.04 and 11.04 system available, and using a bluetooth dongle and the KDE bluetooth notification tray applet, the keyboard can be connected to either of the systems. In both cases it shows up as "Apple Wireless Keyboard".

Almost everything works as expected, in fact, I'm typing on it right now. But one thing doesn't: The Fn key. I'd like to use Fn + Down Arrow as PgDn / Page Down, I understand this is default behaviour on Apple keyboards. And of course I'd like the same for Page Up, Home and End. I'll stick to Page Down in my example.

I used the xev tool to see the keycodes the system receives, and if I press on Fn nothing happens, and nothing is registered. If I press Fn + Down Arrow, xev only registers the down arrow. Here's the output from my 11.04 system to illustrate:

Press just the Fn key: no output

Press Down Arrow key:
```
KeyPress event, serial 36, synthetic NO, window 0x4400001,
    root 0x15d, subw 0x4400002, time 2699773, (44,45), root:(1352,298),
    state 0x10, keycode 116 (keysym 0xff54, Down), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x4400001,
    root 0x15d, subw 0x4400002, time 2699860, (44,45), root:(1352,298),
    state 0x10, keycode 116 (keysym 0xff54, Down), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```Press Fn+Down Arrow Keys together:

```
KeyPress event, serial 36, synthetic NO, window 0x4400001,
    root 0x15d, subw 0x4400002, time 2701548, (44,45), root:(1352,298),
    state 0x10, keycode 116 (keysym 0xff54, Down), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x4400001,
    root 0x15d, subw 0x4400002, time 2701623, (44,45), root:(1352,298),
    state 0x10, keycode 116 (keysym 0xff54, Down), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```I've been searching this forum and other Linux-related forums for hours but I still have not found a solution. I mostly found advice on how to fix this when using Apple hardware, but I don't have that. They said to try something like the following

```
echo 2 > /sys/module/hid_apple/ ...
```But since there's no hid_apple directory present on my systems, I've been unsuccesful.

I'm cool with changing some config files, or compiling my own patched kernel if that's necessary. 

So to sum up my question: Can anyone help me get Page Up, Page Down, Home and End to work on this keyboard, when that requires me to use an Fn key which is currently not registered?

---

### Post by ramplank on 2012-06-17
Surely someone else must have hooked up that keyboard model to Ubuntu... Did you have trouble? Did everything work? Does it have the same model number on the back?

I've tried this on two different systems and it doesn't work on either, so I suspect a serious bug somewhere, but then why hasn't anyone else run into it yet?

---

### Post by ramplank on 2012-06-19
*bump*

---

### Post by ramplank on 2012-06-20
I upgraded to 11.10 and I still have the problem.

I'm going to try 12.04 now...

---

### Post by ramplank on 2012-06-20
Nope, it's still there in 12.04. I'm willing to pay someone to help me fix this... I've been fiddling with this problem for almost five hours now, spread over multiple days.

---

### Post by ramplank on 2012-06-21
Same issue when hooked up to Windows 7. No Fn keys.

Hooked up to an iPad 2 it only works in combination with the F1-F12 keys. Not with the arrow keys. If the screen of the ipad is off, and I press just the Fn key, the screen will come on, so the key itself is not broken or anything.

---

### Post by ramplank on 2012-06-22
This has to be a software issue of some sort, since I've established the key does work on my iP;;ad, even when pressed alone and not in combination with something else.

How do I go about troubleshooting this? If it means I have to write a kernel patch, I'm willing to try my hand at that, I program Ruby for a living, C will be different but if this fixes a bug in the kernel I'm happy to help. I'm however at a complete loss on how to proceed.

I am asking this question on other forums as well, but have received no replies there either.

---

### Post by ramplank on 2012-07-04
I eventually solved this, it appears to be a known bug, but with a solution: [http://unix.stackexchange.com/questions/41537/linux-apple-wireless-a1314-fn-key-not-registered-looks-like-software-bug](http://unix.stackexchange.com/questions/41537/linux-apple-wireless-a1314-fn-key-not-registered-looks-like-software-bug)

---

