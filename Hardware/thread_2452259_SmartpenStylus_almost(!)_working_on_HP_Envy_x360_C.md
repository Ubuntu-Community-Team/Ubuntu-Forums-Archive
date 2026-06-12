---
title: "Smartpen/Stylus almost(!) working on HP Envy x360 Convertible 13-ag0xxx"
date: 2020-10-19
forum: Hardware
---

### Post by kebens on 2020-10-19
[COLOR=#333333]Hey All!

I first installed Ubuntu 20.04 in dual boot on my HP Envy x360 a few months ago. I am very impressed, everything is working and it seems faster and more stable than windows. There is just one thing that keeps me from only using Ubuntu: I would love to use my HP-Pen (stylus/smart pen, [https://store.hp.com/us/en/pdp/hp-pen](https://store.hp.com/us/en/pdp/hp-pen)) with it, since I like to take notes on Powerpoint slides and do math homework etc.

I already stated that it works almost, I will now explain the two problems in Detail:

1)
The Stylus works totally fine in Settings -> Wacom Tablet -> Test your settings. That's why I believe I can not be far from a solution :-)

In all other programs, e.g. LibreOffice Draw the Pen works like a mouse: it does not make a line, but only highlights texts that is there. I can click on draw line ('Curves and Polygones'), I can perfectly draw one line and as soon as I lift the pen from the screen it jumps back to being like a mouse. So it is just about telling the program to deal with the pen as pen, and not as a mouse.

2)
When I add an external screen to the laptop, the location of the pen is not correct anymore. (I would love to watch lectures on the screen and take notes meanwhile, so this is quite important to me.)
It confuses the two screens to be one, so I can click on a location of my (non-touch) external screen, while I touch only my touch-screen on the notebook.
If I add the external screen to be on top of my notebook screen the location of the location of the pen is perfect on the lowest point of my notebook screen. The more I go upward on the touchscreen of my notebook, the more wrong the position of the cursor on the screen becomes. The cursor switches to the external screen, though I am still only touching the notebook screen. When I am on the top point of my notebook with the pen, the cursor is far away at the top of my external screen. 
So I think it is just about restricting the usage of the smart pen on the screen of the notebook.


I hope some of you can help me. I bought my notebook before I knew I would switch to Ubuntu and now I am doing a technical study program. As I said, everything else is working - and it would be so nice it the pen works to. For now I have to reboot all the time and switch between windows and Ubuntu, which just takes so much time. 

(I do not know but maybe this can also be solved by buying a wacom pen... Please tell me if it is like this.)

'xinput' gives back two interesting lines in section Virtual care pointer:
ELAN0732:00 04F3:262B                       id=15    [slave  pointer  (2)]
ELAN0732:00 04F3:262B Pen (0)               id=23    [slave  pointer  (2)]


Please tell me if you need anything else to get more information from me to solve this :)

Best,
khebens



[/COLOR]

---

### Post by kebens on 2020-10-21
The first problem is solved. It was just present in Draw and in  px3-onenote. It is fine in the apps Xournal++ and Write, both detect the  stylus.
So there is just the second problem persisting...

---

### Post by kebens on 2020-10-27
I found a solution to my problem, you can see it here:
[https://askubuntu.com/questions/1285604/external-display-screws-up-stylus-pen-cursor-position](https://askubuntu.com/questions/1285604/external-display-screws-up-stylus-pen-cursor-position)

---

