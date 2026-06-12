---
title: "Thinkpad T23 TV-Out (S3 Savage) Help!"
date: 2005-08-11
forum: Hardware &amp; Laptops
---

### Post by akseli on 2005-08-11
Hello, I only just installed Ubuntu Hoary on my T23 laptop. As you probably have heard this laptop is pretty much a perfect fit for ubuntu as everything sets up perfectly by itself. Except ... TV-OUT... could someone please give me a step-by-step walkthrough (linux newbie) as to the steps one must take in order to get the TV-OUT to work so as to use this laptop as a media center with the TV. 

Thank you! I did some research and found the following driver package:
s3savage-driver_1.1.23t-1_i386.deb but I have no clue on how to get it to install ... I also downloaded and actually sucessfully installed (or so it seems) the s3switch software but when I attempt to run it nothing happens.
Thanks in forehand,

akseli

---

### Post by varunus on 2005-08-11
Where did you get that driver package?  Be very careful before installing drivers you find on the internet, they might break your system.

To install it, open a terminal, and type the following command:

```
sudo dpkg -i /path/to/file_to_install.deb
```

The best thing to do would be to do a google search for your laptop or your video card along with TV out...

---

### Post by akseli on 2005-08-11
Yeah, I've spent the last 8 hours straight researching on google and I've been unable to find any actual step-by-step tutorials, just lots of general information everywhere.

If anyone can help I'd be extremeliy thankful!

---

### Post by akseli on 2005-08-13
[QUOTE=akseli]Yeah, I've spent the last 8 hours straight researching on google and I've been unable to find any actual step-by-step tutorials, just lots of general information everywhere.

If anyone can help I'd be extremeliy thankful![/QUOTE]

Ok, so I figured it out, I had to install S3Switch (use synaptics), then plug in the TV into the TV-Out and just open up a Terminal window and simply type in:

```
sudo s3switch TV
``` 

Good luck to everyone, don't hesistate to contact me through private messages if you need help with a similar problem!

---

### Post by Nasso on 2005-11-30
i got a T20 and i got problems with tv-out too. i dont get the tv to show the right resolution. i got 1024x768 on the laptop but the tv only shows the upper left 800x600 or so, pixels. if i change the laptops resolution to 800x600 or 640x480 the tv doesnt give any image at all.

you dont have, or anyone else, this problem?

---

