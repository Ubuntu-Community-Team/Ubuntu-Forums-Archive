---
title: "Can't get live cd to work"
date: 2006-03-23
forum: Hardware &amp; Laptops
---

### Post by xXx 0wn3d xXx on 2006-03-23
Hi I have a I have a Gateway MX7118 (It's a laptop) with the following:

2.2 ghz AMD processor
512 of ram
Ati Radeon Xpress 200M graphics card

On the live cd I can't start X so I can't do anything. What should I do ? I really want to install Ubuntu but I can't get it to work.

---

### Post by andrewsawyer on 2006-03-24
Can you please tell us what error messages you get (if any), and where you end up?  Is it just at a bash prompt?  If so, have you tried typing 'startx'?

---

### Post by xXx 0wn3d xXx on 2006-03-24
[QUOTE=andrewsawyer]Can you please tell us what error messages you get (if any), and where you end up?  Is it just at a bash prompt?  If so, have you tried typing 'startx'?[/QUOTE]

I'll check but after all the messages, I get a bash prompt.

---

### Post by xXx 0wn3d xXx on 2006-03-24
I can't get a bash prompt and I only get Failed to Start X server.

---

### Post by Sef on 2006-03-24
Do you have another computer that you can use the Live CD?

If so, see if it starts up:

If it starts up, then the problems is likely with the video.

If it fails to start, then the disk would be bad.

---

### Post by xXx 0wn3d xXx on 2006-03-24
I can't test it on another computer b/c this is the only computer that I have with an AMD processor.

---

### Post by xXx 0wn3d xXx on 2006-03-24
anyone ?

---

### Post by xXx 0wn3d xXx on 2006-03-24
nope I still can't start x. Should I just give up ? If I can't get this can anyone give me some distros that are simple to use a debian based. Are their any simular to ubuntu. I'm thinking Suse or Fedora Core. Any other ideas. I also need to be able to dual boot it with windows xp.

---

### Post by audax321 on 2006-03-25
You can try this if you get a prompt (everything is case-sensitive):

1. sudo nano /etc/X11/xorg.conf
2. find a line in the file that says:
```
Driver    "ati"
```
3. change that line to:
```
Driver    "vesa"
```
4. CNTRL+X
5. Press 'y' to save and exit the nano text editor.
6. sudo /etc/init.d/gdm restart
7. hope for the best!

If this works, it basically means the open source ati driver isn't going to work with your video card. So, you will need to use this work around to get into Ubuntu from where you can deal with the driver issue (I'm not sure if the offical fglrx drivers support your card or not).

---

