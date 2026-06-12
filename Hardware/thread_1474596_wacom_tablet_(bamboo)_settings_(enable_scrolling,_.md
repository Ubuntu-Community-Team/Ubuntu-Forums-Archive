---
title: "wacom tablet (bamboo) settings (enable scrolling, using buttons) in ubuntu 10.04 LTS"
date: 2010-05-06
forum: Hardware
---

### Post by mennowo on 2010-05-06
Hello,

using Ubuntu Studio, 64 bit, Lucid 10.04, Wacom tablet works great after installing the system. This means: the mouse pointer moves where it should (over two screens) and the buttons of the pen work (left and right mouse button).

However: I would like to enable scrolling (which normally works like this: holding down left mouse button and touching the tablet while moving the pen up and down. Also: I would like to edit the functions of the buttons, and enable the zoom/scroll touch wheel.

Using Wacom Bamboo Fun, medium.

Any help appreciated!

Menno.

---

### Post by e.m.fields on 2010-05-06
Used to be the only way to configure the "extended functions" of Wacom tablets with Ubuntu was with a driver called wacom-tools. I have it on Karmic system, works great after you figure it out.

However, last I heard wacom-tools doesnt' work under Lucid because it uses the HAL system, which is deprecated in Lucid. ( see wiki: 
[http://www.ubuntu.com/testing/lucid/alpha2#Known%20issues]("http://www.ubuntu.com/testing/lucid/alpha2#Known%20issues"))

I'm seeing encouraging results on google search for "lucid 10.04 wacom-tools", though.

[https://code.launchpad.net/~ubuntu-branches/ubuntu/lucid/wacom-tools/lucid]("https://code.launchpad.net/~ubuntu-branches/ubuntu/lucid/wacom-tools/lucid")

Not sure what this is, but it's a PPA with Lucid and Wacom-tools in the name. sounds encouraging.
please advise if you get it working, this is the one reason I haven't upgraded yet.

---

### Post by mennowo on 2010-05-06
Thanks for your reply. With apt-get install wacom-tools I get a message that the package xserver-xorg-input-wacom has replaced it...

I tried installing the drivers manually but X got quite confused and the tablet stopped functioning altogether. Then I decided I was not gonna spend hours fixing that, and simply reinstalled Ubuntu (the install was fresh anyhow). So, I am a bit reluctant to try and install other drivers...

Hopefully progress will be made with the wacom-tools!

---

### Post by Favux on 2010-05-06
Hi,

Wacom-tools had the xsetwacom comands and wacomcpl (wacom control panel).  Wacomcpl placed a hidden file called .xinitrc in your home directory.  This was with the linuxwacom drivers.  Since they don't work with Xserver 1.7 they won't work in Lucid.  The X driver part of linuxwacom was taken over by Xorg and is called xf86-input-wacom and it does work with Xserver 1.7 and the xsetwacom commands were rewritten and included with it.  So you no longer need wacom-tools to get the xsetwacom commmands.  They are included with the new driver.  However wacomcpl hasn't been rewritten (yet?).

So you need your own xsetwacom script file, call is say .xsetwacom.sh.  You have to manually put in the xsetwacom commands you want, a backup of your old .xinitrc script would be perfect.  Perhaps e.m.fields you could post your .xinitrc, since you are in Karmic and apparently have the same/similar tablet?  Make it executable and enable it to start up with a new session.  The xsetwacom commands are described on the [LWP's HOW TO]("http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom").

---

### Post by mennowo on 2010-05-10
Hi,

Thanks for the advice on xsetwacom.
I've been trying to get xsetwacom to accept the scrolling event.

To do this I got the corresponding id to my devices by doing

```
 xsetwacom -v --list dev --verbose
```That gives me:

```
... Display is '(null)'.
... 'list' requested.
... Found device 'Virtual core XTEST pointer' (4).
... Found device 'Virtual core XTEST keyboard' (5).
... Found device 'Power Button' (6).
... Found device 'Power Button' (7).
... Found device 'Logitech Logitech USB Keyboard' (8).
... Found device 'Wacom BambooFun 6x8 eraser' (9).
Wacom BambooFun 6x8 eraser ERASER    
... Found device 'Wacom BambooFun 6x8 cursor' (10).
Wacom BambooFun 6x8 cursor CURSOR    
... Found device 'Wacom BambooFun 6x8 pad' (11).
Wacom BambooFun 6x8 pad PAD       
... Found device 'Wacom BambooFun 6x8' (12).
Wacom BambooFun 6x8 STYLUS    
... Found device 'Macintosh mouse button emulation' (14).
```This means I have to use device 11 in using xsetwacom to set events for the Bamboo Tablet. Using the name of the device instead did not work for me. So I enter:

```
xsetwacom --set 11 AbsWUp "key core pgup"
```This is accepted by the system, however nothing changes. When trying to scroll (by holding the 'left' mouse button on the pen, touching the tablet and moving down) the same happens when not pressing the button: text is selected. Any ideas on a different command to give xsetwacom for this?

Another thing is the buttons on the tablet, and the touch-scroll0wheel. There is a respons when pressing this, and using xsetwacom I can assign different keys to the buttons. I have to use numers to do this. For example: 

```
xsetwacom --set 11 Button1 1
```This will assign the left-mouse-button action to the first button on the tablet. Pressing it, results in a left mouse click in the very left upper corner of the screen. Number 3 is right click. I don't know the meaning of other numbers (maybe it can be adjusted using xinput?). However, a key event in the very left upper corner is not so useful...

Finally, the command to assign page up does not work here:

```
menno@mennubuntu:~$ xsetwacom --set 11 Button1 "key core pgdn"
Invalid key 'core'.
```The tablet furthermore works great, in absolute mode, left and right clicking is fine, selecting text also. Any ideas on enhancing the functionality?

Thanks!

---

### Post by Evgeny on 2010-05-10
[COLOR="Silver"]**@mennowo**: command
```
[COLOR="Silver"]xsetwacom --set 'Wacom BambooFun 4x5 pad' AbsWUp "key core pgup"[/COLOR]
```
works for me, you probably use wrong syntax..

upd:
this command is magic! this enabled pad buttons, that previously was not working ... :D[/COLOR]

**upd2:** it's my mistake! see explanations below.

---

### Post by mennowo on 2010-05-10
This command does work, either using the id of the pad, or the name as in you example. However, there is no effect on the functioning of the tablet. Or is it necessary to put this command in a script which runs at system startup to function?

---

### Post by Evgeny on 2010-05-11
> **mennowo said:**
> This command does work, either using the id of the pad, or the name as in you example. However, there is no effect on the functioning of the tablet. Or is it necessary to put this command in a script which runs at system startup to function?

Yep. It is not command. I logout and then login again before input commands. And this magic pass enables buttons and touch pad :)

Login/logout probably reloading X-wacom module. I'm trying "xinput reattach x y" but it also does not work. I think it's needs advanced investigations.
Note: I have automatic login.

---

### Post by phoinx on 2010-06-16
> **Evgeny said:**
> Yep. It is not command. I logout and then login again before input commands. 

What? Could you explain better?

---

### Post by Evgeny on 2010-06-17
> **phoinx said:**
> What? Could you explain better?

You have to login into your session, exit and login again.

---

### Post by phoinx on 2010-06-17
You mean you've created a script to be loaded in the beggining of the session, then logged out, then logged in, then logged out and in again? 0o

You are calling the script through that "Session and Startup" under Settings? (In Xubuntu here, is Applications > Settings > Xfce4 Settings Manager > Session and Startup > "Application Autostart" tab.)

Could you reproduce the script here?

---

### Post by dwightjack on 2011-02-15
Hi,

sorry to reopen this thread. I've installed a wacom bamboo pen (CTL-460) and everything works fine. 

Anyway i'm unable to make scrooling feature work. I've tried this command:

```
xsetwacom --set <my-wacom-pad-id> AbsWUp "key core pgup"
```

 with no luck.

Any advice?

thanx in advance!

---

### Post by pSYcl0Ne on 2011-06-03
Same as above. I get

Unknown parameter name 'AbsWUp'.

---

