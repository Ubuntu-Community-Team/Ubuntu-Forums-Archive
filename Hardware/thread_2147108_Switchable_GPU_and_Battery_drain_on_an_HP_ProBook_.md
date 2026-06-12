---
title: "Switchable GPU and Battery drain on an HP ProBook 4530s"
date: 2013-05-20
forum: Hardware
---

### Post by m7esain on 2013-05-20
[COLOR=#333333][FONT=Ubuntu Beta]I have HP ProBook 4530s. In Windows 7 after installing all HP drivers the 6-Cell battery works perfectly for 2+ hours but in Ubuntu 12.10 and now in 13.04 the battery time is not sufficient. It works hardly for 1 or 1.5 hours only. I have installed ATI's Linux Driver for the RADEON card. but i have ended with this error "the system is running in low-graphics mode" 

[/FONT][/COLOR][SIZE=4]image: [/SIZE][http://s14.postimg.org/ijkv7fx0f/IMG_20130517_004453.jpg](http://s14.postimg.org/ijkv7fx0f/IMG_20130517_004453.jpg)[COLOR=#333333][FONT=Ubuntu Beta]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]well, my question is how to make my drivers work and will that fix the battery issue?[/FONT][/COLOR]

---

### Post by m7esain on 2013-05-22
[COLOR=#333333][FONT=Ubuntu]any suggestions ??


[/FONT][/COLOR]

---

### Post by snafu006 on 2013-05-22
your video card is not supported anymore ps if you want your drivers to work go to 12.04 LTS

---

### Post by m7esain on 2013-05-24
Thanks for your response, But where did you get that info ? cuz i had this issue with 12.04

---

### Post by giogziro95 on 2013-06-11
You are right, ATI/Intel hybrid problems will exist until Linus Torvalds will take action, like he did about NVIDIA. ;) I hate proprietary Catalyst drivers, it has a lot of bugs, causing problems, like X server crash or WebGL acceleration problems on Chrome/Chromium, but unfortunately I couldn't find a way to make AMD card work with open source drivers on ATI/Intel hybrid system - it runs on integrated GPU anyway (if anybody knows the solution, please reply).
Now for the business, I had the same issue in 13.04 and [this answer]("http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work/288355#288355") from Ask Ubuntu helped me. Don't forget to downgrade and hold xserver-xorg-video-intel package, otherwise you will have the same problem.
Good luck ;)

> **snafu006 said:**
> your video card is not supported anymore ps if you want your drivers to work go to 12.04 LTS
When was it supported? :lolflag:

---

