---
title: "URGENT! new monitor giving me problems"
date: 2009-03-14
forum: Hardware
---

### Post by windows-killer on 2009-03-14
I just bought a new monitor **Viewsonic Optiquest Q19wb**
I plunged it in and it worked, but I started changing the resolution and suddenly the monitor blanked out and I got an error message saying Out of frequency, I restarted X server and it turned back on, but as soon as I log on it turns black again.

here is what I tried to fix the problem:
I pressed CTRL+ALT+F1 to go to the command line session and I typed 

```
sudo dpkg-reconfigure xserver-xorg
```
I answer all the questions but its still not working, then I tried

```
sudo X-configure
```
But then I get the command not found error

next I tried ```
xrandr -s1024x768
```this worked once but I messed up again by adjusting the resolution:x I put the same command many times but its not working

finally I tried ```
sudo nano /etc/x11/xorg.conf
``` it brings me to a screen with shortcut keys but am unable to use them, but if I press F3 to write to the file it says file not found:S

I have a 128 MB ATI 92500 video card if that helps at all

is there a screen like the one in recovery mode that provides me the option to chose my resolution?
someone please help me, I have been very frustrated working this out.:S

EDIT: I am getting the command not found message when I put this command as well ```
sudo dpkg-reconfigure xserver-xorg 
```

---

