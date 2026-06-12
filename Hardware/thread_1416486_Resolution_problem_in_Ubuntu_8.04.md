---
title: "Resolution problem in Ubuntu 8.04"
date: 2010-02-26
forum: Hardware
---

### Post by Imaginary-r4e- on 2010-02-26
Hi! 

I've got a problem. I've been running Ubuntu on my laptop (HP ProBook 4510s) for about a month now and it has been a delight this far. However, when I booted today the screen resolution was 1024x768 when it's supposed to be 1366×768.

What I think is strange is that not everything is set to 1024x768. I attached a screenshot so that you can take a look at what I mean.

I can't recall that I have made any changes in the settings and I do not manage to set it back to 1366x768. I've looked around in both the Monitor Resolution Settings and Screen and Graphics Preferences.

Please help, it's rather annoying to have a cut off desktop.

**EDIT**: I somehow managed to solve the problem by testing things out in the Monitor Resolution Settings. You it in System > Preferences > Monitor Resolution Settings. (In Ubuntu 8.04 that is. I don't know if it's the same in all versions.) 

So, I'm going to share my solution if anyone in the future have the same problem. Correct me if I'm wrong in anything I say now.

If you look to the left top of the Monitor Resolution Settings-window there is a checkbox with the text 'Clone Screens'. When this checkbox is checked, the settings you change applies only to the desktop. However, when it's unchecked, the settings applies to the entire screen. 

My problem was, that when it was unchecked (entire screen) I could change to up to 1366x768 resolution. But when I checked it (desktop) I could only change to 1024x768 resolution. 

This is how I somehow solved it:

[LIST]
[*]Checked 'Clone Screens'.
[*]Chose 800x600 resolution.
[*]Pressed apply. (Can't remember if I confirmed or canceled after pressing apply. Try both.)
[*]Unchecked 'Clone Screens'.
[*]Changed resolution to 1366x768.
[*]Done
[/LIST]
After doing this, I could all of a sudden change the desktop resolution to up to 1366x768. It was a weird solution but it worked.

---

