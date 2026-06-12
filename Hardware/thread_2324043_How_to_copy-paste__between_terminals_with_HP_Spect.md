---
title: "How to copy-paste  between terminals with HP Spectre x360 - touchpad"
date: 2016-05-10
forum: Hardware
---

### Post by xadder on 2016-05-10
Hi,

After years of working with Thinkpads, I now have a HP spectre x360, with Xubuntu 16.04. I can't figure out how to copy-paste between terminals though. I can left-click (in the touchpad) to mark text, but left-clicking destroys that. Attempting to move to a new terminal and pasting isn
t working. What can I do?  (I do 95% of my work in terminals, this is a real pain!)

Thanks!

---

### Post by him610 on 2016-05-10
> how to copy-paste between terminals 

I believe most touchpads are similar in operation. Try this on your touchpad....

While pressing the left button, drag your finger across the pad to highlight the text you want to copy, release left button, press the right button, select copy then move to the area where you want to paste it and press left button to anchor the cursor, release, press the right button, select paste.

It works for me; although, I hardly ever use it, finding a touchpad to be cumbersome to use. I use a mouse 99% of the time.

Another option is to use your keyboard: after highlighting your text,  press ctrl+c to copy, anchor your cursor, ctrl+v to paste.

Yet another option, get a mouse!;)

---

### Post by jeremy31 on 2016-05-10
> **him610 said:**
> I believe most touchpads are similar in operation. Try this on your touchpad....

While pressing the left button, drag your finger across the pad to highlight the text you want to copy, release left button, press the right button, select copy then move to the area where you want to paste it and press left button to anchor the cursor, release, press the right button, select paste.

It works for me; although, I hardly ever use it, finding a touchpad to be cumbersome to use. I use a mouse 99% of the time.

Another option is to use your keyboard: after highlighting your text,  press ctrl+c to copy, anchor your cursor, ctrl+v to paste.

Yet another option, get a mouse!;)

I actually think CTRL + ALT + c to copy from terminal and CTRL + ALT + v to paste into a terminal
Use CTRL + T to get to terminal as copy/paste doesn't work in xterm the last I tried

---

### Post by QDR06VV9 on 2016-05-10
> **jeremy31 said:**
> I actually think CTRL + ALT + c to copy from terminal and CTRL + ALT + v to paste into a terminal
Use CTRL + T to get to terminal as copy/paste doesn't work in xterm the last I tried

Mine is always Ctrl+ Shift+c to copy from terminal and Ctrl+Shift+v to paste into the terminal.
And Xterm works the same for me at least.
And there is always highlight the selected text to copy and then right click and choose copy and then next terminal right click in that and choose paste. 
Kind regards

---

### Post by xadder on 2016-05-11
Hi guys,

Thanks for the suggestions, but nothing works. For example CTRL-ALT-C just causes ^C, and any "paste" I get to won't paste. Maybe xfce4-terminal (which I use) behaves different to xterm, but on this system simple xterm doesn't work so well.

There must be some solution apart from a mouse. Nothing against mice, but I use my notebook on trains, planes and in not always spacious conditions. Odd that something so simple (and crucial to coders?) turns out to be so hard!

---

### Post by QDR06VV9 on 2016-05-11
Just a suggestion have you tried Terminator dose not pull-in a lot of other Deps.
And easy to install "sudo apt-get install terminator"
Kind Rgeards

---

### Post by QDR06VV9 on 2016-05-11
Ok something just jogged my memory from a few years back.
At the top of the terminal you should see something along the lines of < File Edit View Search Terminal and Help>.
Click on the Edit and down to Key Board Shortcuts and check if it shows the Copy and Paste there.
I included a Screenshot.
And one more keyboard shortcut "Shift+Insert" to paste and "Ctrl+Insert" to Copy.
That is if you have a Insert key of course.
Hopefully?!?

---

### Post by xadder on 2016-05-11
Hi Folks,

Solved (I will mark it). Checking those terminal settings (suggested by runrickus) I saw Shift-CTRL-c and -p, and this works! The CTRL-shift-c didn't. The order seems to matter, which I hadn't expected for those keys.

Anyway, I'll remember to check those settings if I get confused again.

As often happens, the solution is simple once one knows it. Thanks!


(Quick additional cool thing. Now I can mark text with my finger on the touch-screen, and shift-ctrl-c,v also works after that. Nice :-)

---

### Post by QDR06VV9 on 2016-05-11
Very nice glad that worked out for you;)
It is a joy when things work the way we are accustom to.
Best Regards

---

