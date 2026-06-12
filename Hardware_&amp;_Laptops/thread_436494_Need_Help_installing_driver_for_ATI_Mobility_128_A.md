---
title: "Need Help installing driver for ATI Mobility 128 AGP"
date: 2007-05-07
forum: Hardware &amp; Laptops
---

### Post by rmc234 on 2007-05-07
Will a Ubuntu or Linux Guru Please Help!

I left windows for good and I have no clue how to use the CLI in order to find the right driver to improve my resolution from 800X600 to 1600X1200 or something better.

Can someone kindly tell me where to locate the file and how to install it in Ubuntu line by line?:confused: 

Beginner here and need help, converting my IBM Thinkpad A21P laptop runing 7.04

Thank you for your help in advance.

rmc234

---

### Post by Ken_Lewis81 on 2007-05-09
> **rmc234 said:**
> I left windows for good and I have no clue how to use the CLI in order to find the right driver to improve my resolution from 800X600 to 1600X1200 or something better.

Can someone kindly tell me where to locate the file and how to install it in Ubuntu line by line?:confused: 
If your monitor can use 1600x1200, then the quick way to do it is to open up a terminal (Applications -> Accessories -> Terminal) and then issue the command (without the quotes): "sudo dpkg-reconfigure xserver-xorg"  Choose the suggested default options -- it picks up what's already configured -- and don't worry about changing anything before it asks you about Monitor Autodetection.  The next screen should give you the option to pick what resolutions you'd like available.

Take care.
Ken.

---

### Post by rmc234 on 2007-05-11
Ken:
I tried and failed, I am now stuck in Terminal and do not know how to boot up in GNOME.  There were 12 questions I answerd in the configuration that you gave me, but no success.  Is there a better way or another way to do this?

Roland

---

### Post by Ken_Lewis81 on 2007-05-16
Well, here's the get-hand-dirty-in-configuration-files way.

If your X Server isn't working now, but was working before my suggestion fouled it up, you'll have a backup copy of the /etc/X11/xorg.conf file.  when you do a 'dpkg-reconfigure', it stores a backup, using the date and time you ran the file.  What these next steps do is to restore the original X Server config; create a new backup; and add in the lines to get you the screen resolution you want.

[LIST=1]
[*]At your command prompt, move to the /etc/X11 directory: type 'cd /etc/X11/'
[*]Type 'ls' to list the files there.  There should be an 'xorg.conf' and an 'xorg.conf.200705xxxxxx', where the x's are numbers
[*]type 'sudo mv xorg.conf.2007blahblah xorg.conf', replacing the blahblah with the numbers from the file listed as a result of the 'ls' command of the line above
[*]Then type 'sudo cp xorg.conf xorg.conf.backup' to make a copy that serves as a backup
[*]Now type 'sudo nano xorg.conf' to enter a text editor and fix up xorg.conf
[*]Find the lines below 'Section "Screen"', and where there is a 'Subsection "Display"'
[*]Add to each line with Modes "1024x768" etc. the resolutions you want: some may not work with your screen or monitor, and putting in numbers too large may damage your display hardware, so be careful
[*]Typically, you'll want "1600x1200" "1280x1024" "1024x768" and the rest
[*]Sort them with the one you want to appear, first, then the next one, and so on (they can be changed when you're in the desktop with Ctrl-Alt-Keypad-Plus and Ctrl-Alt-Keypad-Minus)
[*]Save, pressing Ctrl-O, and exit, pressing Ctrl-X
[*]Restart the X Server by typing 'sudo /etc/init.d/gdm --restart'
[/LIST]

This should have you more resolutions to play with and back in GNOME.

Take care.
Ken.

---

