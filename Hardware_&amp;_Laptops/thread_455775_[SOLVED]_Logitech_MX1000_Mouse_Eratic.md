---
title: "[SOLVED] Logitech MX1000 Mouse Eratic"
date: 2007-05-26
forum: Hardware &amp; Laptops
---

### Post by jusmurph on 2007-05-26
My mouse jumps around like crazy at random intervals. It used to happen in windows and it required a driver fix. All my searches bring up how to program the buttons.

Anyone know how to fix this? Thank you.

---

### Post by merlinus on 2007-05-27
Same problem.  Wouldn't it be wonderful if Logitech decided to support Linux!

-merlin

---

### Post by jusmurph on 2007-05-27
So it is a case of Logitech aren't supporting it and there is no third party help. Sweet ... :(

---

### Post by merlinus on 2007-05-27
I am afraid so.  Logitech only has windows and mac drivers available, and in response to my complaint said they have no plans to offer Linux drivers for any of their products.

You can be sure I will never buy anything from them again, until this ignorant policy changes.

I have tried a number of suggested workarounds, but every one crashed my system upon bootup.  Fortunately I was able to copy over my backup config files from a terminal.

-merlin

---

### Post by jusmurph on 2007-05-27
Any recommendations on a Linux happy gaming mice?

---

### Post by PoisoN2003 on 2007-05-30
i would also love to know if anyone was able to fix it in any possible way because i love my mouse and would love it to work with linux

---

### Post by wolfsburged on 2007-06-01
I have a similar issue, where my mouse is very difficult to click on things because it jumps around a lot. This is not an issue when I plug in my generic USB logitech optical corded mouse (no extra buttons). I love my MX1000 though, and don't want to give it up.

---

### Post by Cappy on 2007-06-20
Taken from my tutorial for mouse polling:
[http://ubuntuforums.org/showthread.php?p=2452789](http://ubuntuforums.org/showthread.php?p=2452789)

```

gksudo gedit /etc/modules

```

Add these two lines onto the end:
```

-r usbhid
usbhid mousepoll=1

```
(reboot)

Still not working? Do this too:
```

sudo apt-get install lomoco
sudo lomoco -g

```

You may need to set your mouse sensitivity differently in System-->Preferences-->Mouse-->"Motion" tab

---

### Post by jusmurph on 2007-06-20
This works on Improving it... the mouse still twitches only 0.5cm at a time, even with the sensitivity turned right down.

I'm experimenting with surfaces atm, but this is so much better thank you!

---

### Post by PoisoN2003 on 2007-06-21
So far its been great it doesnt jump all over the plae anymore

---

### Post by bclark on 2007-06-25
I have the bluetooth version of the mx1000 and it works except for all the extra buttons, any idea on how to get these activated?

---

### Post by John.Michael.Kane on 2007-06-25
> **bclark said:**
> I have the bluetooth version of the mx1000 and it works except for all the extra buttons, any idea on how to get these activated?

Read here [https://help.ubuntu.com/community/MX1000Mouse](https://help.ubuntu.com/community/MX1000Mouse)

For help heres the corresponding thread.
[http://ubuntuforums.org/showthread.php?t=97936&highlight=mx1000](http://ubuntuforums.org/showthread.php?t=97936&highlight=mx1000)

---

