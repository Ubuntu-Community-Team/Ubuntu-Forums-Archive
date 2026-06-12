---
title: "keytouch: shortcuts do not work"
date: 2007-11-26
forum: Hardware &amp; Laptops
---

### Post by punischdude on 2007-11-26
Hi there,

I've installed Xubuntu Gutsy on my HP Pavilion dv9533eg and everything was fine, except the Multimedia-Keys (using gnome they worked perfectly)

So I started keytouch to configure these keys and the keycodes were recognized correctly. After restarting my notebook I got some of them to work. (except brightness control, lock screen and so on - all of them have been recognized by keytouch!)

But keytouch broke my shortcuts, too. copy and paste do not work anymore, also I can not open new tabs in firefox pressing ctrl+t.

Any ideas?

punischdude

---

### Post by KumoriJinsoku on 2007-11-29
> **punischdude said:**
> Hi there,

I've installed Xubuntu Gutsy on my HP Pavilion dv9533eg and everything was fine, except the Multimedia-Keys (using gnome they worked perfectly)

So I started keytouch to configure these keys and the keycodes were recognized correctly. After restarting my notebook I got some of them to work. (except brightness control, lock screen and so on - all of them have been recognized by keytouch!)

But keytouch broke my shortcuts, too. copy and paste do not work anymore, also I can not open new tabs in firefox pressing ctrl+t.

Any ideas?

punischdude
The problem seems to inlie with the laptop itself. I have a HP dv2000 laptop myself and I found that, using the xev utility, both control and Fn+F2 both output keycode 134. Keytouch thinks that this is the Print command instead of the control key.

I am not sure how to fix it either other than to uninstall Keytouch. Right now I'm looking into a keyboard configuration as well as a possible script that will allow me (and HP users alike) to get this functionality back.

I'm also slightly steamed as my mouse (a touchpad) made me lose a whole writeup of this problem. :(

UPDATE: I just uninstalled keyTouch to try out xev without keyTouch installed. The control key and the Fn+F2 key are now registering correctly as KEYPRESS and KEYRELEASE events. That didn't happen when I had keyTouch installed. More work is needed.

UPDATE2: Just found this: [http://www.notebookreview.com/default.asp?newsID=3262&article=HP+Laptop+Keyboard+Problems](http://www.notebookreview.com/default.asp?newsID=3262&article=HP+Laptop+Keyboard+Problems)

It doesn't look like my keyboard is going to work anytime soon. :mad:

---

