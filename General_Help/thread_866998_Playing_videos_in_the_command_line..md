---
title: "Playing videos in the command line."
date: 2008-07-22
forum: General Help
---

### Post by Vivaldi Gloria on 2008-07-22
In my CLI-only Hardy system (without X) I can watch videos using mplayer's framebuffer output. It plays great. 

When I try to use vlc with one of

```
vlc video_file
vlc --vout fb video_file
```

something weird happens. It plays the video as ascii animation. It uses only the text console! It's really fun. You've got to see it to believe it.

But there is a problem. I don't know how to stop the video! To stop I goto ALT+F2 console and kill vlc from there.

Hence my questions:

1) Does anybody know how to stop the videos in a normal way?

2) How can I make vlc to use the framebuffer?

---

### Post by dracayr on 2008-07-22
q and Ctrl+C don't work?

there is an option --key-stop <integer>

for more info:

vlc -H|less

dracayr

---

### Post by dracayr on 2008-07-22
how did you get that ascii stuff work? sounds really cool and I might install it for my LFS system

EDIT: for the framebuffer, I think you have to use fbdev instead of fb after the vout. And I think you have to use mplayer instead of vlc (I can only get it to work with mplayer). So:```
mplayer -vo fbdev video_file
```. and mplayer stops by simply pressing q

dracayr

---

### Post by Vivaldi Gloria on 2008-07-22
> **dracayr said:**
> how did you get that ascii stuff work? sounds really cool and I might install it for my LFS system


I have "vga=795" at the end of the kernel line in menu.lst. This gives me 1280x1024 resolution framebuffer. See this page for framebuffer:

[http://ubuntuforums.org/showthread.php?t=258484](http://ubuntuforums.org/showthread.php?t=258484)

Then I installed

```
sudo apt-get install mplayer vlc
```

Now I can watch videos with

```
mplayer -vo fbdev -fs -vf scale=1280:-3 FileName
mplayer -vo fbdev -fs -vf scale=-3:1024 FileName
```

Use the first one if the width of the video is larger than the height. Otherwise, use second. I have an alias in .bashrc so I don't have to remember them.

mplayer works as it's supposed to. shortcut keys also work.

Now when I start 

```
vlc FileName
```

it doesn't use the framebuffer and uses ascii text to show the video!! Really impressive. I'm yet to find how to enable shortcuts or how to utilize framebuffer in vlc.

As I said above, to stop I goto ALT+F2 console and kill vlc from there. This leaves the original terminal (ALT+F1) in a weird state so to get it back use the command

```
reset
```

I looked at the flag you suggested in the second post but I couldn't make it work. I cannot find any decent references on the web. Let me know if you find anything useful.

EDIT: I saw your edit now. :-)

---

