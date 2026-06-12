---
title: "how to disable touch-to-click on asus netbook running ubuntu?"
date: 2010-10-06
forum: Hardware
---

### Post by frizz327 on 2010-10-06
I recently bought an ASUS Eee PC Seashell series (1015PEB) netbook from Best Buy. I realized that I needed a portable computer to use for my programming courses, which require us to use Ubuntu and other specific programs and versions in Ubuntu. However, I cannot figure out how to turn off the touch-to-click function on the touchpad and it is driving me crazy! It is preventing me from even using the netbook at all. When I do (like right now) my WPM decreases drastically as I try to not touch the touchpad or as I repeatedly type paragraphs that get messed up from my cursor deciding to make me type elsewhere -_- I've never understood why some people love this function, as I disable it on all my computers, but that is beside the point.

Ideally what I want to do is be able to use the touchpad for mouse  cursor movement, but only be able to actually click by using the touchpad  buttons. When I go into System > Preferences > Mouse, there are only 2 tabs: General and Accessibility. (Other help forums I've tried perusing often say there is a 3rd tab that I don't have?) General just has Mouse Orientation, Locate Pointer, Pointer Speed, Drag and Drop,  and Double Click Timeout. Accessibility has Simulated Secondary Click and Dwell              Click options. I would settle for just using a plug-in mouse, but I can't even figure out how to turn off any part of the touchpad, so I still have the problem of my cursor changing my typing location on me. When I try to hit Fn+F3 (a little touchpad symbol crossed out), nothing happens - the touchpad remains fully functional.

Any help would be GREATLY appreciated. Maybe there is some sort of command line prompt that I could use? Or a really obvious answer I'm not seeing? (I am only a sophomore computer science student and a total noob at ubuntu, so that is a big possibility :P ) thanks!

---

### Post by P4man on 2010-10-06
Install 'pointing devices' from the software center.

---

### Post by Oreo on 2010-10-31
I have the same problem on my 1015p. When I call up Pointing Devices, there are only a couple of settings (scroll wheel emulation), but nothing for disabling. Using Touchfreeze doesn't seem to have any affect on the touchpad. The only thing that has worked so far is to use
sudo modprobe -r psmouse

Please help.

---

