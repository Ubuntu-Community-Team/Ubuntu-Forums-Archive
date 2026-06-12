---
title: "USB memory stick not showing up when plugged in."
date: 2012-01-25
forum: Hardware
---

### Post by lornt78 on 2012-01-25
USB memory stick not showing up when plugged in. My laptop is a Dell Inspiron 1545. It used work. The memory stick works in other computers. Other USB devices work in my laptop.

---

### Post by madvinegar on 2012-01-25
2 questions:

i) You said "it used to work". Did it stop working after a kernel update maybe...?

ii) You said "other usb devises work". Are these other devices storage devices? Or just a usb mouse or a usb web cam etc? Have you tried pluging another USB stick in your laptop to see if that will work?

---

### Post by lornt78 on 2012-01-25
madvvinegar,

i) Could have been after an update, not sure.

ii) My camera works when I plug it in, that's a storage device. I don't actually have another memory stick available to try out.

---

### Post by madvinegar on 2012-01-26
Open a terminal, **log in as root** and write:

```
modprobe usb-storage
```

Then plug the USB flash drive and check if it will mount.

If it does, let me know and I will tell you what to do next.

---

### Post by lornt78 on 2012-01-26
I think I am normally logged in as root.

Tried typing that command into the terminal and it's still not working.

[IMG]http://i26.photobucket.com/albums/c107/lornt78/Screenshotat2012-01-26140836.png[/IMG]

---

### Post by madvinegar on 2012-01-26
I think you are not logged in as root in terminal.

Open terminal and write

```
su
```

give the password and then you will see that your "address" will start as "root".


If you have not set ap a root password do the following:

Open terminal and write:

```
sudo passwd
```

Then give your normal password.
Then give a unix password
re-write your unix password

and you are ready.

Then again follow the instructions at the beginning of this post to login as root.


P.S.: Just a clarification. When you say that your USB is not showing up, you mean that it does not work at all (i.e. you do not see the lights flashing?).
Maybe it is just a matter of different type of formating.

---

### Post by lornt78 on 2012-01-26
Looks like I wasn't logged in as root.

I have followed those instructions, and still no joy.

My memory stick doesn't have a light.

It used to work, that's why I can't see how the formatting could be the problem. Should I put it in another computer and format it?

[IMG]http://i26.photobucket.com/albums/c107/lornt78/Screenshotat2012-01-26144916.png[/IMG]

---

### Post by madvinegar on 2012-01-26
Try to format it in another computer (I suppose you do not have another computer with linux installed?).

Format it in FAT32 mode and try again.

Also, with the USB stick plugged in get in terminal and write:

```
lsusb 
```

and post the results.


Also try this one.
Plug the usb flash drive and restart the computer with the USB flash drive plugged in and see if it will be recognised.

---

### Post by lornt78 on 2012-01-26
Formating did the trick! Thanks for all your help, brother.

Below is the results from entering that command. "Sandisc Cruzer Blade" is my memory stick. Any idea what "Microdia" is? Nothing other than the mouse and power cable are connected.

[IMG]http://i26.photobucket.com/albums/c107/lornt78/Screenshotat2012-01-26165713.png[/IMG]

---

### Post by madvinegar on 2012-01-26
Glad I helped !!!

Microdia must be something like a webcam or a flash memory card (or something like that).

Please mark this topic as "solved".:D

---

