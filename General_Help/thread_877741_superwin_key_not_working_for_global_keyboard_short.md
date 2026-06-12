---
title: "super/win key not working for global keyboard shortcuts"
date: 2008-08-02
forum: General Help
---

### Post by chitresh4u on 2008-08-02
I want to configure some global shortcut key, for music players & others, with combination of win/super key. I have a standard Windows keyboard (US layout) with 104 keys. [here]("http://images.techtree.com/ttimages/story/TVS-gold-keyboard.jpg") is an image of my keyboard.

Navigating to System > Preferences > Keyboard Shortcuts, I tried to change the shortcut for play/pause. I changed the shortcut to Mod4+X. But the shortcut does not seems to be working. I tried changing to some different shortcut like Ctrl+Alt+X. And it works. It play/pauses my media player. But changing to any shortcut with combination of super/win key does not work. 

My keyboard layout is set to Generic 105-key (Intl) PC with default settings. I am using Ubuntu 8.04 Hardy.

Am I doing something stupid ????

---

### Post by coffeecat on 2008-08-02
I'm curious. How did you get the Mod4 code into the shortcut field? In Keyboard Shortcuts, if I highlight one of the functions, I get 'New Accelerator..' appearing in that field, and then when I press the Windows key alone, the code 'Super L' appears, and using the Windows key activates that function.

By experimenting, I found I could combine the Windows key with shift and alt, but with any of the character keys, only 'Super L' got written to the shortcut field or I got a message telling me I couldn't use a character key as a shortcut.

One oddity I found while investigating this. When I pressed Windows Key + 3, the screen zoomed in. Super+2 does a lesser zoom and Super+1 zooms out to the ordinary desktop again. Which is strange because in Keyboard Shortcuts, both Zoom in and Zoom out are said to be disabled. :-k

---

### Post by geirha on 2008-08-02
In System -> Preferences -> Keyboard. Under the Layout-tab, choose your layout and hit the "Layout Options" button. In there, try changing the values under Alt/Win key behavior. I have "Super is mapped to the Win-keys" there, and I've mapped Win+t to open a terminal.

---

### Post by chitresh4u on 2008-08-02
> **coffeecat said:**
> I'm curious. How did you get the Mod4 code into the shortcut field? In Keyboard Shortcuts, if I highlight one of the functions, I get 'New Accelerator..' appearing in that field, and then when I press the Windows key alone, the code 'Super L' appears, and using the Windows key activates that function.


yeah you are right... I also got 'Super L'. But after few trial I found how to get Mod4+<anything>. here are the steps

1. click once on any function to get 'New Accelerator'
2. press win key. you will get 'Super L' (L denotes left win key)
3. click on the function again holding, the win key(i.e. keep win key pressed once you press it the 1st time)
4. now you have win key pressed & 'New Accelerator' in the shortcut. Now just press any new character. you should get Mod4+ <character>

---

### Post by chitresh4u on 2008-08-02
> **geirha said:**
> In System -> Preferences -> Keyboard. Under the Layout-tab, choose your layout and hit the "Layout Options" button. In there, try changing the values under Alt/Win key behavior. I have "Super is mapped to the Win-keys" there, and I've mapped Win+t to open a terminal.

I had already tried that without any success. But after your post I tried again, but this time I modified the shortcut for new terminal. And it worked. 

But the interesting part is that the similar shortcut (win+X) when configured for the music player does not work. I configured the shortcut for play/pause. I tried with another shortcut (Ctrl+Alt+X).. & it worked :confused:

It seems that my music player (rhythmbox) is not happy with win key. I tried with a few different functions. I found that 'Home Folder' option also do not work with shortcuts with win key.

I am highly confused. :mad: :confused:

---

### Post by jhenager on 2008-08-27
You aren't the only one. I figured this out once, but now cannot get the Super key to work by itself. If I press "Z" it will come up Mod4+Z but still doesn't work.
It shouldn't be this hard.
Standard 104 keyboard with Wake, Sleep, and Power.
Hardy 64 bit on the hardware listed in sig.

---

### Post by deepcyan on 2009-01-18
hi all. i tried the "Super is mapped to the Win-keys" option under keyboard settings and after removing conflicts with the compiz effects, was able to configure the Win key with other modifier keys to control rhythmbox (play/pause, next, etc.), start a terminal and control gnome volume, without any hitches. thanks to all for the advice.

btw, i'm using ubuntu 8.10, probably the bug (if any) was removed in this release.

---

### Post by chitresh4u on 2009-01-31
I checked again with "meta mapped to win-keys" on Ubuntu 8.10 and it works.
thanks to all for the advice.

---

### Post by unimatrix on 2009-02-13
Using Ubuntu 8.10. The Win/Super key stopped working for some reason. And when I reinstalled Ubuntu (8.10) it still doesn't work. :(

It's not even detected by xev

---

### Post by lucaa on 2009-04-29
> **geirha said:**
> In System -> Preferences -> Keyboard. Under the Layout-tab, choose your layout and hit the "Layout Options" button. In there, try changing the values under Alt/Win key behavior. I have "Super is mapped to the Win-keys" there, and I've mapped Win+t to open a terminal.

This worked for me, I have a Dell Inspiron 1501 laptop and Ubuntu Jaunty. Thanks!

---

### Post by pooyaplus on 2009-04-30
Hi, I recently installed 9.04 on my hptx2000 laptop which 8.10 was running on previously. After the new dist install, the Super L key is not functioning when bound to an action in the keyboard short cuts.

I have tried meta mapping too with no luck. Any ideas?

Cheers.

---

### Post by pooyaplus on 2009-05-03
I also tried to bound it to some other actions. But it seems to be dead. It is actually returning signal when checking with xev. What I do not understand is that why it is not working OTB.

---

### Post by pooyaplus on 2009-07-13
Bump!

---

### Post by persio on 2010-04-30
I'm having the same problem. It's odd:

win+e opens my home directory, as I set it
and win+u shows me the windows
and win+y shows me the desktops
but win+w does not close the windows,
nor does win+q minimize them
or win+up maximize them

I've trying mapping the key, but don't have any option saying anything about super, all my options say alt, control, hyper, left alt, meta.

I really don't know which keyboard I'm using. I'm on a gateway FX P-7805u, using the bundeled one.

[HALF-SOLVED]
The problem was compiz, some keybindings where overlapping. But there's there's still some others not working.
**Is it possible to disable compiz key bindings?**

---

### Post by jondiced on 2010-05-27
> **jhenager said:**
> You aren't the only one. I figured this out once, but now cannot get the Super key to work by itself. If I press "Z" it will come up Mod4+Z but still doesn't work.
It shouldn't be this hard.
Standard 104 keyboard with Wake, Sleep, and Power.
Hardy 64 bit on the hardware listed in sig.

I'm having the same problem with Lucid, and would love to know if you found a solution.

---

### Post by Marceau on 2010-07-07
> **geirha said:**
> In System -> Preferences -> Keyboard. Under the Layout-tab, choose your layout and hit the "Layout Options" button. In there, try changing the values under Alt/Win key behavior. I have "Super is mapped to the Win-keys" there, and I've mapped Win+t to open a terminal.
This worked for me on an Asus eee pc 1000HE. Placing this here in case anybody ever has the same problem
The language appears to have changed though. I chose the option 'Meta is mapped to the Win-keys'.

---

### Post by Redsandro on 2012-11-29
How would we do this in Ubuntu 12.10?

In 12.04 and 12.10, Super stopped responding to custom shortcuts. I used it for a lot of things. Now I have to replace everything with multiple key combo's.

Come on, the menu is not so important that the super key is solely reserved for opening that menu. Let's share functionality. :)

---

### Post by Vaphell on 2012-11-29
it is not solely reserved for opening that menu

press and hold WIN, you should get the list of unity shortcuts

---

### Post by Redsandro on 2012-11-29
Nope, first thing I do when installing Ubuntu is to remove Unity and install Cinnamon. :D

Either way, why can't I use it anymore like the good old 10.04 days?

Super+L -> lock screen
Super+T -> Terminal
Super+R -> Run
and a lot more.

For example, I was trying Super+A for play/pause of no avail. But for this key Ctrl+Alt+A and Shift+Ctrl+Alt+A also aren't working.

Is A also reserved?

---

### Post by overdrank on 2012-11-29
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

