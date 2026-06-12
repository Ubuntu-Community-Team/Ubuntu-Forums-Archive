---
title: "Mouse Keyboard Issues"
date: 2006-09-25
forum: Hardware &amp; Laptops
---

### Post by jpatt on 2006-09-25
Ubuntu 6.0.6 x386. New life breathed into my 650MHz Dell Lattitude. Thanks Ubuntu.

Anyway, the problem is this... My mouse is a PS/2. It is irratic, all over the place, hangs, moves itself off screen. Touchpad installed but not used. The usb external keyboard has a specific issue. When at the command line, I'll enter sudo /file. The next thing to happen is for me to enter a password. Every single time after entering the first line, the password line does not input a visual password, even though I typed it. I have worked around it with cut and paste. First enter the password, copy, delete, type the sudo file. Then when the next line asks for a password, I paste. That works, but again nothing is visible, nothing shows it has been pasted. I just paste and pray. It works, sigh ](*,)

---

### Post by Mr Frosti on 2006-09-25
Your password will not show any characters, or anything at all when entered. This feature is called "masking" and is designed to prevent someone looking over your shoulder discovering how many characters your password contains. 

Try typing in your password at one of these prompts, and then press enter and see if it accepts the credentials.

As for the mouse issue, when was the last time the mouse worked without issue? If this is an older mouse, try cleaning the wheel or optical eye. This is a common issue. 

If the problem persists, see if you have the same issue with a different mouse if possible. If not, see if booting to the Ubuntu CD in Live mode has the same erratic results.

---

### Post by Henry Rayker on 2006-09-26
If it's an optical mouse, make sure you're using it on a nice dark surface with little or no reflection. Using such a mouse on wood or something like that will cause the behavior you explained.

---

### Post by jpatt on 2006-09-26
Well I don't know if it is masking characters or not. I would think my password would show as *****. But no. Also, If i just try typing at the prompt without pasting, password not found. It is very strange. I've done this little run around for days now. Nowhere else is there an issue. Just at the password prompt.

As for the PS/2 mouse, It works fine under M$. I started out with an optical, then just replaced it with a cheap ball mouse. Same problem. No amount of mouse settings work. Maybe a new driver or maybe a usb mouse? Also, none of the mouse issues appear nor bad behavior is found at the login screen. Everywhere else, hang, drag, irratic, opens files on its own, sometimes shuts down my session, some time opens 10 windows. Exorcist?

---

### Post by jpatt on 2006-09-26
I was able to provide a password correctly just by typing, not cut and paste

---

### Post by Joebewan on 2006-09-29
I don't have an answer, but maybe we can brainstorm.  I have the same problem with my Latitude. (CPx650j)  I should also mention that I'm using a "c-dock" docking station.

My mouse / touchpad works fine in XP Pro and worked in Red Hat, though that's been a couple of years ago.

I have the erratic behaviour in Ubuntu 6.06 both with Live CD and Installed.

I looked at my /etc/X11/xorg.conf and found some entries for a "wacom" pointing device that were referenced as being for tablet pc's which the Latitude is not.  I backed up my xorg.conf and removed those entries.  Wrong answer; X would not start.

After restoring the original xorg.conf using a tip from another post: (cp xorg.conf~ xorg.conf) I noticed that I got failures when the "wacom" device was referenced as well as a failure pertaining to the Synaptics touchpad, which is what we have in the Latitude.

That makes me wonder if we have a compatibility issue with the Synaptics touchpad.  I also wonder why the entries for the "wacom" device are there and why removing them kept X from starting.

Have you tried using the touchpad only without external mouse ?

Can anyone tell me how I reconfigure the mouse under Ubuntu.  I seem to recall an X configuration, but can't remember the command or precedure. (I'm getting old)

Joebewan

---

### Post by skymt on 2006-09-29
> **jpatt said:**
> Well I don't know if it is masking characters or not. I would think my password would show as *****. But no. Also, If i just try typing at the prompt without pasting, password not found. It is very strange. I've done this little run around for days now. Nowhere else is there an issue. Just at the password prompt.

This actually increases security. This way, someone looking at your screen can't see how long your password is. It can be a little hard to get used to at first, but you will. It was also easier to implement. The program just has to tell the terminal not to echo what the user types to the screen.

By the way: if you make a mistake at a terminal password prompt, don't bother hitting backspace. Ctrl-U is what you need. It erases everything you typed, so you can start from scratch.

---

### Post by Joebewan on 2006-10-04
Update:
I switched to a USB mouse, which helped.  It's still "jumpy" but no longer goes off on a tangent moving the cursor and clicking it's own buttons.

I also opened device manager and clicked the "Ubuntu Device Database" button which sends a list of my hardware to Ubuntu along with comments as to how everything works.  Maybe something will come of that as well.

I'll post again if anything changes or I find a solution.

Joebewan

---

