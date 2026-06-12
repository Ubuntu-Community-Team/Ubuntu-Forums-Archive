---
title: "DisplayLink driver installation"
date: 2013-11-01
forum: Hardware
---

### Post by akrabi on 2013-11-01
[SIZE=2][FONT=arial]Hello.

I am running Ubuntu 12.04 on my laptop and trying to connect a monitor through a DisplayLink adapter.

I was following the steps of this guide: [http://how-to.cc/get-a-displaylink-video-adapter-working-with-ubuntu-12-04](http://how-to.cc/get-a-displaylink-video-adapter-working-with-ubuntu-12-04)

First I needed to install the DisplayLink drivers.  
When I tried: 
[/FONT][/SIZE]```
[SIZE=2][FONT=arial][COLOR=#333333]sudo apt-get install xserver-xorg-video-displaylink[/COLOR][/FONT][/SIZE]

```[RIGHT][SIZE=2][FONT=arial][COLOR=#333333]

[/COLOR][/FONT][/SIZE][/RIGHT]
[SIZE=2][FONT=arial][COLOR=#333333]I got a dependency problem:[/COLOR][/FONT][/SIZE]
```
[SIZE=2][FONT=arial][COLOR=#333333]Reading package lists... Done
[/COLOR][/FONT][/SIZE][COLOR=#333333][FONT=lucida grande][SIZE=2][FONT=arial]Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you haverequested an impossible situation or if you are using the unstabledistribution that some required packages have not yet been createdor been moved out of Incoming.
The following information may help to resolve the situation:[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande][SIZE=2][FONT=arial]The following packages have unmet dependencies: 
xserver-xorg-video-displaylink : Depends: xorg-video-abi-11
                                  Depends: xserver-xorg-core (>= 2:[1.10.99.90]("http://1.10.99.90/")1)
E: Unable to correct problems, you have held broken packages.[/FONT][/SIZE][/FONT][/COLOR]

```[SIZE=2][FONT=arial]
So I installed these dependencies:
```
sudo apt-get update
[COLOR=#333333]sudo apt-get install xserver-xorg-core
sudo apt-get install xorg-video-abi-11[/COLOR]
```

I tried to reboot but now Ubuntu doesn't load.
It doesn't reach the login screen.

Any advice?

Thanks, Assaf.[/FONT][/SIZE]

---

