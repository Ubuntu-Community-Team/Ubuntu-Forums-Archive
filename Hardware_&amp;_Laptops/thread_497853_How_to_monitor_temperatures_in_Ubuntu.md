---
title: "How to monitor temperatures in Ubuntu"
date: 2007-07-10
forum: Hardware &amp; Laptops
---

### Post by murak on 2007-07-10
First "How to" I make, sure hope I do it right :-?

First, install Xsensors with the Add/Remove tool by opening

Applications>Add/Remove...

Choose System Tools on the left and scroll down to X Sensors to the right.

Mark X Sensors and press the button Apply.

After the install is done you may open the program from 

Applications>System Tools>X Sensors

but you may be disappointed at the result. Dont worry, instead open the Terminal and write

```
sudo sensors-detect
```

Follow the instructions on the screen and answer Yes to all questions. (I answered Yes to the last one, but if you are uncertain, answer No or cunsult someone with more experience than me. However I dont know what happens if you answer No, so I guess I recommend you to answer Yes.)

When done, reboot your computer and start Xsensors by clicking

Applications>System Tools>X Sensors

All should now be well and you temperatures displayed something like this:

---

### Post by loserboy on 2007-07-10
does lm-sensors need to be installed/configured 1st?

---

### Post by tgm4883 on 2007-07-10
> **murak said:**
> First "How to" I make, sure hope I do it right :-?

First, install Xsensors with the Add/Remove tool by opening

Applications>Add/Remove...

Choose System Tools on the left and scroll down to X Sensors to the right.

Mark X Sensors and press the button Apply.

After the install is done you may open the program from 

Applications>System Tools>X Sensors

but you may be disappointed at the result. Dont worry, instead open the Terminal and write

```
sudo sensors-detect
```

Follow the instructions on the screen and answer Yes to all questions. (I answered Yes to the last one, but if you are uncertain, answer No or cunsult someone with more experience than me. However I dont know what happens if you answer No, so I guess I recommend you to answer Yes.)

When done, reboot your computer and start Xsensors by clicking

Applications>System Tools>X Sensors

All should now be well and you temperatures displayed something like this:

I don't know about answering yes to all the questions.  I'm not sure what they all do, but I chose the defaults over selecting yes every time.  You can get the default by just hitting enter.

---

### Post by floke on 2007-07-10
you could try (from terminal)

acpi -t

(or 'watch acpi -V')

---

### Post by murak on 2007-07-11
@loserboy, no, not as far as I know =)

@tgm4883, ok, you answered No to the last and your temp monitor is working? If so, Ill have to change the How to.

@floke, that is a good tip! On my pc it shows me the battery status and cpu temp. 

Cheers all!

---

### Post by louieb on 2007-07-11
On my laptop I use GKrellm

---

### Post by tgm4883 on 2007-07-15
> **murak said:**
> @loserboy, no, not as far as I know =)

@tgm4883, ok, you answered No to the last and your temp monitor is working? If so, Ill have to change the How to.

@floke, that is a good tip! On my pc it shows me the battery status and cpu temp. 

Cheers all!

Just checked it, the last question is the one where it adds everything to /etc/modules.  For some reason, one of my sensors doesn't work with conky very well and makes conky refuse to start.  So I don't load that module.  For a majority of people though, adding them automatically should work.

---

### Post by RedSquirrel on 2007-07-15
> **loserboy said:**
> does lm-sensors need to be installed/configured 1st?
When you run 'sudo sensors-detect', you *are* configuring lm-sensors. xsensors is just a graphical frontend to lm-sensors. ;)

---

