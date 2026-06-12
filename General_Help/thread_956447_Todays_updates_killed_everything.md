---
title: "Todays updates killed everything"
date: 2008-10-23
forum: General Help
---

### Post by irishrm on 2008-10-23
I can log into a blue screen nothing left.  I tried recovery mode-nothing. Tried different kernel-no joy.   How can I recover my OS. I have xbuntu 8.40 Thanks
Irishrm

---

### Post by Peter09 on 2008-10-23
What do you get in recovery mode. You need to go to the shell prompt. This will give you a black screen with a command prompt at the bottom.

Try typing 

```
startx
```

at that point.

---

### Post by irishrm on 2008-10-23
Thanks peter 09 that sorted my problem. Everything back working again. May have to re-arrange the desktop

---

### Post by Peter09 on 2008-10-23
Hi,
just to check. Have you been able to reconfigure your video drivers so that you can log in normally. 

Just that recovery mode is exactly that - not for long term use.

---

### Post by irishrm on 2008-10-23
Thanks for getting back again. I seen to be logged in as root so I need to set up a user account again any help would be appreciated. Whats the best way to test the video drivers?

---

### Post by Peter09 on 2008-10-23
No you do not need to create a new account. Once the video drivers are set up you can log in as normal to your old account.

here is a guide

[http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)

Basically you need to run this command from a terminal.

```
dpkg-reconfigure xserver-xorg
```

---

### Post by irishrm on 2008-10-23
Sorry for delay in getting back.  I've being trying to follow your instructions with no success. The commands in the thread you recommended when entered return as bad commands. So I don't know what I'm doing wrong. I now find that some of the letters on the keyboard are not being recognized. thats down to the reconfiguration I'm sure. It looks like a long haul to get going again but I'll keep at it. thanks

---

### Post by Peter09 on 2008-10-23
You can do the reconfigure again with no problems, that will sort your keyboard. What commands are not being recognized? Try pasting the command line into a terminal.

I sugest you just do the command that I listed.

Additional- you may see no difference in the screen display, but do try a normal login when you have done the command.

---

### Post by irishrm on 2008-10-23
I'm running  xbuntu hardy heron 8.4. It seems that this fix doesn't work for hh. could you take a look.

---

### Post by Peter09 on 2008-10-23
Can you post the output of

```
 lshw -C display

```

---

### Post by irishrm on 2008-10-23
I'm using a different computer to type this. I'm afraid my keyboard is not working properly as some of the letters are not being recognized also the internet connection is not working. If fact nothing is being recognized so it looks like a fresh install will be needed.  I have Xbuntu installed on this computer also and the same updates are available for installation. I won't download them but what is the solution to this problem.

---

