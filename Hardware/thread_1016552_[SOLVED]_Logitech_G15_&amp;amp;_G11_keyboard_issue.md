---
title: "[SOLVED] Logitech G15 &amp;amp; G11 keyboard issues"
date: 2008-12-20
forum: Hardware
---

### Post by Cadeyrn on 2008-12-20
That was pointless. I just spent a LONG time getting my Logitech G11/15 keyboard working perfectly, G-Keys and all, in Ubuntu, and the whole reason I did it was because I wanted my Caps Lock and Num Lock lights fully operational instead of staying off regardless of the lock's position. Well, it's probably because I haven't restarted yet, and if it works after I restart I'll mark solved, but in the meantime, maybe someone could give me a solution just in case. And by the way--if restarting didn't work, I'll make a new post.

The problem is after all of the configuration was done, I pressed caps lock and the light went on. I rejoiced as I pressed the button again, and although caps lock went off, the light did not. The exact opposite of the problem I was having before. And the num lock light is unchanged--still always off. I did notice before I installed Ubuntu that on the LiveCD Preview, my lock lights worked perfectly. What's up???

---

### Post by Cadeyrn on 2008-12-20
The plot thickens--none of the lock lights or M123 or MR are working at all after I restarted. Help, damnit!

---

### Post by Cadeyrn on 2008-12-20
BUMP.

Isn't there ANYONE out there who can help??!!

---

### Post by ugm6hr on 2008-12-21
What did you try?

I don't have that keyboard, but there is a System->Prefs->Keyboard menu.

In the Layouts tab, you can change the keyboard model.  There is a Logitech G15 extra keys option (in Hardy).  Try that, or any of the other Logitech layouts.

And you might have been better served by a more helpful thread title.

---

### Post by Cadeyrn on 2008-12-21
Yeah, I've already tried that. And I can't change the title! >.<

As far as how I did it, I don't remember the guide's address because I copy+pasted it into Tomboy Notes. Which means I can put the guide into this post:

```
Introduction

This will walk you through the process of installing and configuring your Logitech G15 keyboard in Ubuntu. After doing this, you will be able to use the LCD display and all of the special keys will work just like normal keys that you can bind shortcuts to. To do this, you will need to do three things: download and install drivers so that Ubuntu recognizes the LCD and extra keys, add symbols to X so that the extra keys exist in X, and bind the extra keys on the G15 to the symbols you created.

Installing G15 drivers with G15tools

First, install the required libraries: libusb and libdaemon, and if not already installed the build-essentials package.

sudo apt-get install libusb-dev libdaemon-dev build-essential

Download libg15, G15Composer, and libG15Render from http://g15tools.sourceforge.net/, and G15daemon http://sourceforge.net/projects/g15daemon/ . Extract the packages anywhere, then type these commands for each of the three:

tar -xjvf <directory of zip file>
cd <directory that it extracted into>
./configure
make
sudo make install

Note: If you see an error while running ./configure, make a note of what it said was missing before it failed. This is most likely the name of a program or library that you need to install. You can open up the Synaptic Package Manager in the System->Administration menu and search for that file. You will most likely want to install the one that ends in -dev.

Once you have done this, it is safe to delete the .tar.bz2 files as well as the directories you made; the programs have been installed and you do not need the source anymore.

Now load the uinput module and set it to load when you start the computer:

sudo modprobe uinput

Run gksudo gedit /etc/modules and add "uinput" to the list.

After you've done this, run sudo g15daemon. If you see a clock appear on the LCD screen, it is working properly. If not, refer to the Troubleshooting section below. To set g15daemon to run automatically at startup, edit the sudoers file by running the following:

sudo visudo

Add the following line to the bottom of the file -

ALL ALL= NOPASSWD: /usr/sbin/g15daemon

Warning: If visudo complains about syntax errors when you exit the program, do not ignore them! Go back and look at the file and see what went wrong. If you mess up the sudoers file you might not be able to run sudo at all, which you'll need a LiveCD to fix.

After you have done this, add g15daemon to your session by going to menus System -> Preferences -> Sessions, selecting New under the Startup Programs tab, and adding one with the name G15Daemon and the command sudo /usr/sbin/g15daemon.
```

And then there was a whole bit about manually configuring the G-keys, but since I'm not interested in doing that and since I can do it automatically with that file that has "g15capture" or something somewhere in its title, I skipped that.

---

### Post by Cadeyrn on 2008-12-22
Ugh, it looks like this problem'll never get solved. So I'm gonna give up and mark it as solved.

---

### Post by ugm6hr on 2008-12-23
> **Cadeyrn said:**
> Ugh, it looks like this problem'll never get solved. So I'm gonna give up and mark it as solved.

That is unhelpful for future searchers on the forums.

The SOLVED mark is for exactly that - solved problems.

Sometimes threads get a response months after the original post.

---

