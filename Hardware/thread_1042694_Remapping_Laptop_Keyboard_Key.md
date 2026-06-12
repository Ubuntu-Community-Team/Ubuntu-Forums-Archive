---
title: "Remapping Laptop Keyboard Key"
date: 2009-01-17
forum: Hardware
---

### Post by Represto on 2009-01-17
I just picked up a new laptop.  It's an MSI Megabook S430X.  Retail on it is $389...can't go wrong. 

One thing that really bothers me is the placement of a key adjacent to the left shift key.  It's a < key with > shifted.  No need.  I already have those characters on other keys.  Not only is it completely redundant, I keep hitting it when I'm trying to hit the shift key.

My question:  how can I re-assign that key to be another shift key?

I'm running Ubuntu 8.04 (64-bit)

---

### Post by Represto on 2009-01-17
It looks like I can use xmodmap to do it.  

[http://www.columbia.edu/~djv/docs/keyremap.html]("http://www.columbia.edu/~djv/docs/keyremap.html")

Although, I haven't found out the keycode for the trouble key....

---

### Post by monkeyjohn on 2009-01-18
see this thread:

   [http://ubuntuforums.org/archive/index.php/t-273437.html](http://ubuntuforums.org/archive/index.php/t-273437.html)

---

### Post by Represto on 2009-01-18
Fixed.  Here's what I did to make a shitty useless key into an additional left shift key.

I was having a difficult time determining what the keycode for my shitty key was.  It was labeled as a \ key, | when shifted.  However, it was actually mapped as a < key, > when shifted.

I installed the program xkeycaps ([http://www.jwz.org/xkeycaps/](http://www.jwz.org/xkeycaps/)).  it's a GUI that brings up a picture of your keyboard.  You hover over the key you're interested in and it displays the keyCode, keySym, modifiers, etc.

This told me that the key was keycode 94 and the my current left shift key was keycode 50.  I got further into using xmodmap....

$ xmodmap -pke | grep 50
keycode 50 = Shift_L

The -pke switch gives you output in the correct syntax to feed back into xmodmap...so from here it was a copy and paste

$ xmodmap -e "keycode 94 = Shift_L"

Since I'm making it a special kind of key, I had to add this key to the shift modifier group.  You would have to do this if you were relocating/making a Control key, Alt key, etc.

I made a text file named xmo.shift that contained the following line and saved it in /tmp

add shift = Shift_L

Then I ran the command the following command while in /tmp

xmodmap xmo.shift

I checked the config...

$ xmodmap -pm | grep -v shift
shift      Shift_L (0x32), Shift_R (0x3e), Shift_L (0x5e)

(32 hex is 50 dec, 5e hex is 94 dec)

Now it works!  No more annoyances.

---

### Post by Represto on 2009-01-18
...however it was all gone after reboot.  

I added the commands to ~/.xsession but that messed up something because now I can't log into my account.  bah.  I'll remove the .xsession file.

Anyone have any ideas?

---

### Post by Represto on 2009-01-18
Just put the xmodmap commands in ~/.profile   She works after a logout/login.

---

