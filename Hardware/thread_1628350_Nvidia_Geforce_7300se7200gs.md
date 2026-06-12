---
title: "Nvidia Geforce 7300se/7200gs"
date: 2010-11-22
forum: Hardware
---

### Post by ricecake on 2010-11-22
Hello everyone, i'm new using Linux, so i decided to try Ubuntu. Well i have this problem, when i was trying to install Ubuntu on my machine everything when fine until i press "Install Ubuntu" on the live cd, the installation start but it freezes in the Ubuntu loading page. I did some research and i found on a forum post, a guy there was having the same problem and he said it was because of the video card (He had an ATI radeon 9200) so i did the same, i removed my video card and the installation process was smooth. After i entered the system, install some stuff, click here and there, i decided to put my video card once again but now every time the system is loading it crash, i get a bunch of line codes but thats it, i tried to initialize the system in safe mode but with no luck, a crash still occurs, is there anything i can do? I really want to keep using my video card instead of the inboard video and i don't want to go back to Windows.

P.D: Sorry for my crappy english, is not my native language :)

---

### Post by Fafler on 2010-11-22
You really should try posting those "codes." Chances are it's trying to tell you what went wrong. A thing you could try is from the boot menu, select safe mode, press e to edit the boot options, remove the last two words "quiet splash" and press ctrl+b or whatever the command is to make it boot. If it still crashes, it might give even more detailed information andf it provides you with a login screen in text mode, we can most likely fix it from there.

What onboard graphics do you have?

---

### Post by ricecake on 2010-11-22
This is what i get when i try to start Ubuntu normally with the video card.

[http://img408.imageshack.us/img408/7686/p2211101937.jpg](http://img408.imageshack.us/img408/7686/p2211101937.jpg)

And this is what i get when i try in recovery mode.

[http://img268.imageshack.us/img268/425/p2211101940.jpg](http://img268.imageshack.us/img268/425/p2211101940.jpg)

The second pictures is kinda blurry, bad angle i guess.

And this is my onboard video.

  	 	 	 	p { margin-bottom: 0.08in; }  display  
              description: VGA compatible controller  
              product: 82915G/GV/910GL Integrated Graphics Controller

---

### Post by Fafler on 2010-11-23
It's complaining about a filesystem error. If you have another harddrive lying around, try to make a clean install on that instead. This might just be a case of a half broken drive and bad luck.

---

