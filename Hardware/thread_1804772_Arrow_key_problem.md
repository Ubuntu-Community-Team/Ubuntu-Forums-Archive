---
title: "Arrow key problem"
date: 2011-07-15
forum: Hardware
---

### Post by Robboti on 2011-07-15
I'm using a dual boot laptop (eMachines 250) with Windows XP on my internal hard drive and Ubuntu 11.4 on external hard drive. Here's my problem:
One day I downloaded (from indiedb), installed and tried a game called BOH. After launching the game, my keyboard started acting strange. Left and Down Arrows work now as Alt GR, Page Up gives me /, my Alt Gr is now Enter, my right Ctrl functions as Page Down and my Right Arrow, Home and End do not work at all. I don't know what my Page Down is, but if I push it down and press A twice, I get Å. Up Arrow on the other hand works as Up Arrow and Delete is Delete.
     This only happens on my primary (and only) account on Ubuntu. If I boot to Windows or sign in as guest on ubuntu, everything works as they should. Even if I go to view my keyboard layout, it says that everything works as charmed. (And Fn functios are normal altough when I set screen brighter, i also get ±)
     Which brings us to the fact that *changing keyboard language does not help* changing things back. (I'm using Fi-fi layout, since I'm in Finland)
    The funniest part is, that I had the same problem once before, but I didn't know back then how I got it or how it miracously got fixed. **And by fixed, I mean that every button works the way they were meant to work**.
Could someone please help?

P.S. sorry if this is in wrong section.
P.P.S. sorry, that's Ubuntu 11.04, not 11.4

---

### Post by Robboti on 2011-07-20
I could really use some help. Or am I the only one with this problem?

---

### Post by Robboti on 2011-07-27
I take that as yes

---

### Post by beirut on 2011-08-03
Hey!
No, you aren't the only one. I've got _exactly_ the same problem. Have you found a solution yet?

some additional information:
- using Ubuntu 10.04 with compiz
- during a session the mis-arrangement of the keyboard sometimes gets  worse: after some time additional errors occur like the [.]/[:] button  (on the German Keyboard) suddenly does work any more.
- plugging the keyboard in and out during a running session helps to fix the problem for the the duration of the running session. After performing a restart, the same problem as described above re-appears.


Ben

---

### Post by Robboti on 2011-08-06
I guess I just have to buy a USB keyboard to plug in and plug out every time.

---

### Post by beirut on 2011-08-17
Hey! ¹²³¼½¬{[]}\"§$$%%&/( @@@€€€€€

No precise idea what solved it but a trace (Thanks to my nice IT support):
Go to
System>Settings>Keyboard. Go to the second tab (should be sth. like key assignments or so) One of these two solved it: 
*Either*
check the language settings or play around with them
[I]Or/And
[/I]Click the options button at the bottom>there should be sth. like "key for shifting into the 3rd key level". There choose the right Alt key (Alt Gr?) as changing key to the 3rd level.

Y€@h B@by!  :guitar:


ben

---

### Post by Robboti on 2011-08-19
Well... I tried the second one first, but it didn't have any effect. Then I decided to play around the language settings and the window froze (everything else worked fine, only the keyboard window didn't respond; it didn't even quit). Then I decided to restart, since usually anything takes effect after reboot, and all I get now is a blinking Caps lock light and Ubuntu won't boot at all after Grub screen.
  However, if I choose older version of Ubuntu when I'm on Grub, It boots fine... and the main problem still remains... Windows on the other hand works fine.

Maybe I just let my Ubuntu to collect dust until Oneiric is out and try again then. (Or not, becouse [http://ubuntuforums.org/showthread.php?t=1829151](http://ubuntuforums.org/showthread.php?t=1829151))

Edit again: After updating, Ubuntu boots fine

---

### Post by Robboti on 2011-08-21
Holy Schipperke, Batman. I FIXED IT. All i had to do was ```
setxkbmap fi
```Edit: Well. It works until I reboot. So** is there a way how the command would run automatically on startup** So I don't have to type it every time.

EDIT: Pretty please. I can't find a tip that works. I have tried creating a file which has the command in it, but no. I also tried adding the "setxkbmap fi" in "command" in where I can choose which programs run at startup. I also tried locating setxkbmap and making it run on startup.

---

### Post by Robboti on 2011-08-28
Putting "gnome-terminal  --command setxkbmap fi" to start up in system settings did the trick

---

