---
title: "Microsoft lifecam NX6000 not working on 11.04"
date: 2011-07-30
forum: Hardware
---

### Post by notoold on 2011-07-30
Hi!

I am a newbie, have installed the Ubuntu 11.04 on my desktop, however, everything is working fine, but have found out that, the Webcam Lifecam NX6000 is not working, thought I have installed the Cheese, it works on Cheese but not on Skype etc., Could anyone give me instruction how to config it? Many thanks

---

### Post by UltraAnders on 2011-08-10
Did you get this working? I've got the same problem here on my fresh install of 11.04. Used to work on 10.04.
lsusb shows this:
Bus 001 Device 002: ID 045e:00f8 Microsoft Corp. LifeCam NX-6000

---

### Post by UltraAnders on 2011-08-14
Worked it out. If I run this command from the terminal, Skype loads and my camera works:
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```
If you see the error:
```
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
```
Then it could be you're using 64 bit version, in which case try:
```
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
```
or libv4l-0 isn't installed. Follow the instructions [here]("http://www.ubunturoot.com/2010/05/how-to-fix-webcam-problem-in-skype.html").

If you want to create an icon instead of running Skype each time from the terminal, and if you're using Unity (like I), then adding a shortcut isn't as simple as it should be:
- follow the instructions in [post 50 here]("http://ubuntuforums.org/showpost.php?p=9172669&postcount=50")
- then follow the instruction in the second answer [here]("http://askubuntu.com/questions/13758/how-can-i-edit-create-new-launcher-items-in-unity-by-hand"), putting "skype2" in the command box. The Skype icon can be found in /usr/share/icons.

---

