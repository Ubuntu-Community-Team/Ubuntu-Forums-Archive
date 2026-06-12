---
title: "HP Pavillion dv9000 having trouble with wireless card and sound card :("
date: 2009-05-27
forum: Hardware
---

### Post by ForeverKokubetsu on 2009-05-27
[SIZE=2]So a few days ago, I wiped Windows XP from my laptop (HP Pavillion dv9000) and installed Ubuntu 9.04.

Ever since I first ran Ubuntu, the wireless hasn't worked at all. "Wireless Network" didn't even show up until my boyfriend spent about 6 hours two days ago trying to find drivers and install stuff to fix it :( The wireless switch on the side of mylaptop has been turned to on the whole time, but the light's still red, a sign that it's not connected, even though my boyfriend has come over multiple times and has connected to my wifi with his laptop (that also has Ubuntu 9.04 and has had a lot less problems than mine :\)

About the sound - I have buttons near the keyboard that can control the sound. First day, it worked. After that, the buttons didn't work at all anymore. My laptop used to beep if I pressed backspace too much in a chat window or etc (yeah, THAT beep. The one that rings through your entire house seemingly from the deep, dark innards of your computer, making everyone annoyed after only the third beep...) so my boyfriend recommended:[/SIZE] [SIZE=2][COLOR=#000000]nano /etc/modprobe.d/blacklist.conf in the terminal and I added "blacklist pcspkr" under his advice. It seemed to work, but yesterday, I had to go find a youtube link. Finally got the flash working, but my sound didn't work at all, and if I had my volume up past halfway for at least a minute, it would buzz and hum and still not play any sound. And then I'd turn the volume back down. I wondered if what we did with the sound was causing this problem, so I went back to try and delete it, but it wouldn't let me anymoar :( I opened my terminal, opened the file, and tried to take out "blacklist pcspkr", but it would always say "error writing: permission denied"

If that was confusing, I'm very sorry :( I'm not good at this, but I do know that I really want my laptop to work so that I won't have to dual boot XP for everything to work together. Thanks a bunch for anyone who tries to help :(
[/COLOR][/SIZE]

---

