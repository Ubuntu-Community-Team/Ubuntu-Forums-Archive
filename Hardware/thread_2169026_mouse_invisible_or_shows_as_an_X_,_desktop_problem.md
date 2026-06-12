---
title: "mouse invisible or shows as an X , desktop problem"
date: 2013-08-20
forum: Hardware
---

### Post by pcool on 2013-08-20
Hello , I have this issue !!!
I have an issue with my ubuntu-Studio desktop (xcfe 12.04) after i booted the mouse disapeared and then as I open a window the mouse shos as an X , right-click does not work but left click does work , my workspaces shows that it only has 1 available even if my desktop is configured to have 4 , icanot close or move my firefox window (sometimes i can by using the menu ... but sometimes I can't) , then I received new updates showing That i'd have to install ndivia drivers so i did , after reboot I did then I notice that my proprietary driver was diasble after I restarted ... so i reinstalled ndivia driver and rebooted but it didn't helped

this issue seems to come after waking from ... sleep mode ( or hibernate mode)

Ithink I have to edit my xorg-conf file but i don't know where the problem is . 
I had ubuntu_studio 12.10 with the same problem so I formated  and re-install the unbuntu_studio 12.04 verssion ... it worked for about two weeks then i caught the same issue 

i tried to open window manager and it failled 

everything works fine when i login as guest , 

Any help will be apreciated ...  thanks !!!

---

### Post by pcool on 2013-08-20
i searched and found these simular issues....

[http://askubuntu.com/questions/116373/invisible-mouse-cursor](http://askubuntu.com/questions/116373/invisible-mouse-cursor)

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/475917](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/475917)

---

### Post by pcool on 2013-08-20
Yéy ... 
i solved it ,  it happenned to be my window manager ( xfwm4 from ubuntu_studio 12.04)
I...
 -opened synaptic pakage manager
-reinstalled xfwm4 
 -installed xfwm4-dbg
-rebooted

---

