---
title: "HP Pavillion 9500 series Microphone"
date: 2008-02-19
forum: Hardware &amp; Laptops
---

### Post by teeleef on 2008-02-19
Hi all,  having trawled the forums with little success yet...:-) Has anyone got the inbuilt microphone working with this laptop?

Skype recognises the webcam but I don't know where to start in getting the microphone to work.   It may end up being as simple as going down the usb microphone route.

Just curious.


Teeleef

---

### Post by EXCiD3 on 2008-02-23
Do you know anything about the microphone? I installed Skype the other day but i dont remember actually using it lol...I did however play Counter-Strike Source back on feisty and the microphone worked out of the box...only it was fairly choppy.

---

### Post by teeleef on 2008-02-24
I think its probably a question of me setting it up correctly.  I don't know EXCiD3 how to identify the actual microphone from the command line.  I you have any ideas or suggestions I'm all ears.


BTW your howto with HP Laptops is the dogs!!! (UK saying and it is a compliment)


Teeleef

---

### Post by EXCiD3 on 2008-02-24
> **teeleef said:**
> I think its probably a question of me setting it up correctly.  I don't know EXCiD3 how to identify the actual microphone from the command line.  I you have any ideas or suggestions I'm all ears.


BTW your howto with HP Laptops is the dogs!!! (UK saying and it is a compliment)


Teeleef

Haha thanks, I'm currently testing Hardy Heron and going to be collaborating with 2 other HP owners so that we can have a more up-to-date tutorial since mine is only for Feisty because I didnt think Gutsy was worth the time and effort.

Well your microphone will be together with your sound card so im not sure of any way to show what microphone you have. However I did come across several links you might find useful:

[http://www.g33k.infinitesecond.net/weblog/archives/2008/02/01/sound-problem-with-ubuntu-and-hp-dv9700-laptop-and-how-it-was-fixed/](http://www.g33k.infinitesecond.net/weblog/archives/2008/02/01/sound-problem-with-ubuntu-and-hp-dv9700-laptop-and-how-it-was-fixed/)
[http://ubuntu.wordpress.com/2005/12/05/fixing-the-errant-microphone/](http://ubuntu.wordpress.com/2005/12/05/fixing-the-errant-microphone/)
[http://clet.blogspot.com/2008/02/microphone-on-ubuntu-gutsy-and-hp-6710s.html](http://clet.blogspot.com/2008/02/microphone-on-ubuntu-gutsy-and-hp-6710s.html)

If i can get the time I will try recording audio with my builtin microphones on my dv9000t and see if they work on hardy. This might not mean anything as the audio driver has been changed to PulseAudio but it might shed some light on the topic.

---

### Post by teeleef on 2008-02-26
Many thanks EXCiD3 for the links!!!!   

I used alsamixer and tweaked the settings.  The bloody microphone worked and under Skype too!!!!   

It seems its a fine balance of settings to get it right.  If the capture setting or the digital, front mic and mic boost settings were too high, then all I got was loud clipping sounds from the speakers.  Turning levels down and fine tuning worked a treat.

I now have a great laptop.... 2gb RAM, two 160GB drives a crystal clear 17" screen with nvidia and of course most importantly Ubuntu. 

All I need now is to trial Timevault or Flyback and of course eagerly await a Hardy install sometime in the future.


Thanks again for your dedicated work for HP Pavillion owners across the globe 


Teeleef

---

