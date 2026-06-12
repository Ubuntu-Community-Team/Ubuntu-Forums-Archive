---
title: "Apple keyboard/function keys"
date: 2009-10-30
forum: Hardware
---

### Post by dullo on 2009-10-30
Hi I just upgraded to Ubuntu 9.10 yesterday and so far I love it. However I have been using one of Apples aluminium keyboards since Jaunty. I am using the wired one without the number pad. And ever since I have installed Karmic I realised that the F2 key no longer works to rename files or folders and I can't assign my F3 and F4 keys to do anything at all.
Why is this? Any help would be great

---

### Post by coffeecat on 2009-10-30
I've been using an Apple aluminium keyboard, but with the numeric keypad, for some time. At the moment I'm only using Jaunty with it. (I'm using Karmic on another machine.) For the F2, etc keys to work in Jaunty I have to press the Fn key at the same time. Actually, I have to hold it down before I press the function key. So - two questions. Did F2, etc work by themselves in Jaunty for you? And is there a Fn key on the numeric keypad-less keyboard?

The other thing to check is which keyboard you have selected in System > Preferences > Keyboard. Go to the layouts tab and under "Keyboard model" make sure you've got Vendor = Apple and Model = Macintosh. If you had that before it's just possible it reverted when you upgraded.

---

### Post by dullo on 2009-10-30
Yes in Jaunty the F2 key worked on its own and renamed files/folders by default. And yes the keyboard without the numeric keypad also has a 'fn' key in the bottom left of the keyboard.

---

### Post by dullo on 2009-10-30
Hey wait a second, I just tried using F2 while holding the fn key down and it works to rename files. That's strange.. how can I get it back to the way it was in Jaunty, I need it to work on its own.

---

### Post by dullo on 2009-11-01
bump

---

### Post by dullo on 2009-11-03
Ok I have figured it out. Holding down the fn while pressed any of the function keys will do exactly that. It becomes a function key. However if you don't hold the fn key down and press one, for example lets say you press F12 it reads as "XF86AudioRaiseVolume"

Now here is my problem, I want to make the Expose key (F3) to Initiate Window Picker. But when I try to do that in keyboard shortcuts and I press the expose key it reads it as "0x80" and nothing happens when it is pressed.

---

### Post by traffas on 2009-11-04
There are several posts with fixes to get the keyboard to respond normally when using function keys. Does anyone know of a way to remove the need to use the 'fn' modifier to get the function keys to work with Karmic Koala?

---

### Post by Vadikus on 2009-11-09
[https://help.ubuntu.com/community/AppleKeyboard]("https://help.ubuntu.com/community/AppleKeyboard")
Take a look there. I've fixed mine keyboard with second variant (through conf file)

---

### Post by goatgonads on 2009-12-01
> **Vadikus said:**
> [https://help.ubuntu.com/community/AppleKeyboard](https://help.ubuntu.com/community/AppleKeyboard)
Take a look there. I've fixed mine keyboard with second variant (through conf file)

Thank you for linking this! Works great!

---

