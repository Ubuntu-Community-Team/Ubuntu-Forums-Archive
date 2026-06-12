---
title: "&quot;Unknown Display&quot; stuck at 1024x768 xrandr not working 16.04 LTS Intel"
date: 2017-02-10
forum: Hardware
---

### Post by Alduins_Khajiit on 2017-02-10
I have a Dell Optiplex 760 that has an Intel graphic card that will not get off of 1024x768 whatsoever. Even setting 1600x900 using xrandr doesn't work. It only works temporarily until I restart my computer. I followed the instructions here: [http://askubuntu.com/questions/860735/unknown-display-in-ubuntu-16-04](http://askubuntu.com/questions/860735/unknown-display-in-ubuntu-16-04) but every time I turn off or restart my machine, it always reverts back to only 1024x768.

When I type: ```
shrunken-human@Toilet:~$ grep -i vga
```
the terminal always just hangs and does not show hardware information

However, the next thing supposedly worked:
```
xrandr --newmode "1600x900_60.00"   118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync
```

and then:
```
sudo xrandr --addmode VGA1 1600x900_60.00
```

but if I turn off my machine or restart it, it always reverts back to only 1024x768 as the option. It does not stay like indicated in that post.

Does anybody know what the problem could be?

---

### Post by zohaib442 on 2017-02-10
this worked for me on loki

[https://www.youtube.com/watch?v=FRV3Vz4lbWk](https://www.youtube.com/watch?v=FRV3Vz4lbWk)

---

### Post by Alduins_Khajiit on 2017-02-11
That's basically what I did. It didn't work. As I said, it reverts to 1024x768 upon restart

---

### Post by Yellow Pasque on 2017-02-11
Show your /var/log/Xorg.0.log file (use code tags or pastebin because it's a lot of text)

---

### Post by Alduins_Khajiit on 2017-02-11
I got that Youtube video link to work. I just didn't see the other part of the nano ~/.xprofile part because the text in the video was so small. Doesn't suit well with the small area given by YouTube for the video

---

### Post by zohaib442 on 2017-02-11
Steps are also written in the description area

---

