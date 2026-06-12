---
title: "Volume and Brightness FN keys not working on Asus"
date: 2008-09-10
forum: Hardware
---

### Post by takerphenom on 2008-09-10
I have an Asus m50s laptop and I installed Ubuntu on it because Vista sucks obviously, and I run Ubuntu on my desktop.  I can't however, use the volume or brightness controls via the fn key.  Volume is only adjustable through the volume applet or rebinding.  The volume through the fn key was working perfectly fine just yesterday and now it does not and I have not installed anything new or updated.  The brightness keys never worked, and in fact I cannot adjust the brightness of the backlight at all, which means my screen is really dull when plugged in making it hard to see.  There is no option to adjust the brightness through the powermanagement applet and the brightness applet available to add to the main panel also does nothing.  I have looked all around but it seems impossible to find any information on this laptop model and it's really annoying me because it's a good laptop and I cannot use it to it's full potential.

---

### Post by Pizzadox2 on 2008-12-06
Yea. I have such prblems =(

---

### Post by sfraga on 2008-12-19
> **takerphenom said:**
> I have an Asus m50s laptop and I installed Ubuntu on it because Vista sucks obviously, and I run Ubuntu on my desktop.  I can't however, use the volume or brightness controls via the fn key.  Volume is only adjustable through the volume applet or rebinding.  The volume through the fn key was working perfectly fine just yesterday and now it does not and I have not installed anything new or updated.  The brightness keys never worked, and in fact I cannot adjust the brightness of the backlight at all, which means my screen is really dull when plugged in making it hard to see.  There is no option to adjust the brightness through the powermanagement applet and the brightness applet available to add to the main panel also does nothing.  I have looked all around but it seems impossible to find any information on this laptop model and it's really annoying me because it's a good laptop and I cannot use it to it's full potential.

Same here.. although the scary part is that when i turn off the brightness to the minimum there is no effect on Ubuntu, but when i restart the laptop (mine is a ASUS PRO50GL) the screen is all dark and i have to use the same combination of keys to put it back to normal..
Sound combination with Fn, isnt working either though.
Help would be great...

---

### Post by Stillwellean on 2009-01-12
i had some trouble with this and still do.

The only thing I've found to fix the brightness issue has been to run the following code in the terminal every time I restart. :(

sudo su
echo 10 > /sys/devices/platform/asus-laptop/ls_level

I realize that this is only a temporary fix, but it help to be able to see your screen when you're trying to fix other things.
Note, you can't run it as just sudo echo... for some reason.  Not sure why, just know you can't.

Hope this helps you, and I hope someone finds a fix for this bug someday soon.

edit:  I forgot to mention that i have an m50s.

---

### Post by tjeremiah on 2009-01-12
im on a sony vaio and same problem. I cant figure out how to fix the brightness. No matter what I do it doesnt work. Only time it did was when I inserted a code but after reset it doesnt work. This is basically the only thing im fustrated about. Not so much about the headphone and speaker problem.

---

### Post by studentidiot on 2009-01-12
> **tjeremiah said:**
> im on a sony vaio and same problem. I cant figure out how to fix the brightness. No matter what I do it doesnt work. Only time it did was when I inserted a code but after reset it doesnt work. This is basically the only thing im fustrated about. Not so much about the headphone and speaker problem.

Same here on my Vaio.

---

### Post by tjeremiah on 2009-01-14
any help?

---

### Post by SketchyClown on 2009-02-20
Stillwellean is on the right track.

I have the M50VM-A1 with the newest v.209 firmware installed which fixed the ambient light sensor which was broken in v.207.

After upgrading I found that the light sensor auto-adjusting my brightness was annoying as it was never the level I wanted.

So I Googled for some fixes and found that after I did the following, I had control of my brightness back.

1: Edit as 'sudo' the file **/sys/devices/platform/asus-laptop/ls_switch** and change the value from a '1' to '0'. '1' sets it to auto-adjust and '0' sets it to full brightness that you can adjust manually with the FN keys.

2: I also edited that other file **/sys/devices/platform/asus-laptop/ls_level **to '20' from '0'.

Now I have full control of the keyboard brightness control.

You can make the changes survive rebooting by installing **sysfsutils** and editing the **/etc/sysfs.conf** file by adding these lines:

devices/platform/asus-laptop/ls_switch=0
devices/platform/asus-laptop/ls_level=20

Add your own level that suits your taste.

---

### Post by lordyoyo on 2009-08-31
I have a problem on my ASUS X58L, but only with the sound shortcut. It recognizes the Fn F10-12 commands as mute, volume up and down in Keyboard shortcuts, but it only changes the Realtek OSS mixer's in-gain channel, while it should change the master volume :( (btw what are ALSA and OSS mixers, I don't know anything about these things). What can I do for it to work properly?

---

### Post by aruseni on 2011-07-18
> **Stillwellean said:**
> i had some trouble with this and still do.
sudo su
echo 10 > /sys/devices/platform/asus-laptop/ls_level

I realize that this is only a temporary fix, but it help to be able to see your screen when you're trying to fix other things.
Note, you can't run it as just sudo echo... for some reason.  Not sure why, just know you can't.

That is because only the  “echo” command itself runs from superuser, while the redirection (>) is performed from your user, which doesn’t have write permissions for writing to that file.

So, to perform the redirection from superuser, you can run it this way:

sudo sh -c "echo 10 > /sys/devices/platform/asus-laptop/ls_level"
****

---

### Post by sunsetslave on 2011-12-21
I found a solution... OK someone else did but... hooray that was bothering me

[http://www.webupd8.org/2010/05/enable-fn-keys-on-your-asus-eeepc-and.html](http://www.webupd8.org/2010/05/enable-fn-keys-on-your-asus-eeepc-and.html)

---

### Post by tristan13 on 2012-01-31
I just bought at ASUS K53T and the brightness key worked but only to change one level of brightness, now it doesn't work at all. Can anyone help?

---

### Post by lordyoyo on 2012-02-01
tristan13 do you have TeamViewer or any other program that uses it's own display drivers? If so, remove it's display drivers and it should work properly. I've had the exact same problem on my girlfriend's DELL and this fixed it imediately.

---

