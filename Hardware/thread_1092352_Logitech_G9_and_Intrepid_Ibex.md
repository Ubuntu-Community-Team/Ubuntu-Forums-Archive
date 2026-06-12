---
title: "Logitech G9 and Intrepid Ibex"
date: 2009-03-10
forum: Hardware
---

### Post by Valentini on 2009-03-10
I'm pretty new to using Linux. Though I think I've been learning quite a lot in the past few months. I'm using Ubuntu Intrepid Ibex x64, but it should not have any importance in this guide.
I've got a Logitech G9 laser mouse which I'm very fond of. Sad thing was that when I booted in Ubuntu the first time, and tried to find drivers from logitech (yes, i've been using windows that much ^^), they weren't there..
At first I tried to find a guide for easily configuring my mouse, though they seemed to be old/not working all of them. At best some of the extra buttons worked in some applications. I gave up then, but this weekend I gave it another chance. Here is the outcome:
First of all I **don't** use xorg.conf as many other suggests. I stumbled across [_this_]("http://mesanna.com/2008/11/02/ubuntu-810-intrepid-ibex-mouse-configuration/") blog, and figured that I should not touch the xorg.conf. Instead, I created a file (you can read a lot more about these [_here_](&#8221;https://wiki.ubuntu.com/X/Config/Input&#8221;): 
```
sudo touch /etc/hal/fdi/policy/mouse.fdi
sudo gedit /etc/hal/fdi/policy/mouse.fdi
```
This is how my (updated) config looks like:
```
<?xml version="1.0" encoding="UTF-8"?>

		<match key="info.product" string="Logitech G9 Laser Mouse">
			<merge key="input.x11_options.Resolution" type="string">3200</merge>
			<merge key="input.x11_options.ConstantDeceleration" type="string">5</merge>
			<merge key="input.x11_options.Buttons" type="string">9</merge>
			<merge key="input.x11_options.ButtonMapping" type="string">1 2 3 4 5 6 7 8 9</merge>
			<merge key="input.x11_options.ZAxisMapping" type="string">8 9</merge>
			<merge key="input.x11_options.Emulate3Buttons" type="string">false</merge>
		</match>
```
If your mouse is too slow after reboot, reduce or remove the ConstantDeceleration.
To find your mouse buttons type xev in a terminal. A little window will be shown. When you mouse over it all events will be shown, you can see the button names in between.

Then I found [_this_]("http://morecode.wordpress.com/2007/11/22/logitech-g9-on-linux/") guide, and made a mouse-button map. You can use this to switch buttons on your mouse. Mine is
pointer = 1 2 3 4 5 8 9 6 7
To create the file do this in the terminal:
```
echo pointer = 1 2 3 4 5 8 9 6 7 > ~/.Xmodmap
```

At last I found the best part of it all. A way to bind keyboard actions to mouse buttons. This allows me to make the back/forward buttons work everywhere, and make firefox etc. switch tab if I tilt the mouse :) I found the hint [_on a page about the G7 mouse_](&#8221;http://help.ubuntu.com/community/G7Mouse&#8221;).. But it works just fine. You have to install some applications and edit a config file:
```
sudo apt-get install xvkbd xbindkeys
gedit ~/.xbindkeysrc
```
I've set it up to go back/forth on the buttons on the side of the mouse, and change tab on wheel-tilt. My config is:
```
  "/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:6
  "/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:7
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Control_L]\[Page_Up]""
  m:0x0 + b:11
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Control_L]\[Page_Down]""
  m:0x0 + b:12
```
It's actually pretty obvious what it does.
```
&#8221;code to run&#8221;
m:mouseHexId + b:button
```

Now you only need to add xbindkeys to your startup programs. You do this in System > Preferences > Sessions. Click the add button, and enter xbindkeys in the field for the startup command.

Et voila! :)

Hope some of you find it useful

---

### Post by Subban on 2009-07-08
Thanks very much for posting this information.

I clean installed 9.04 over my 8.10. The mouse (Same Logitech G9) worked perfectly in 8.10 from a dist upgrade of 7.04 where it was originally set up.

I only did part of your configuration however, as follows:

```
sudo apt-get install xvkbd xbindkeys
```

I had my existing **~/.xbindkeysrc** which I did modify to match yours (I love the addition of side clicking the wheel to change tabs), so it looks like: 

```
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  b:6
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  b:7
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Control_L]\[Page_Up]""
  m:0x0 + b:11
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Control_L]\[Page_Down]""
  m:0x0 + b:12
```

I also already had ~/.Xmodmap which contained the single line:

```
pointer = 1 2 3 4 5 8 9 6 7
```

When I started **xbindkeys** up in a terminal, the buttons all worked correctly, or certainly seem to on the normal desktop, Firefox and Nautilus.

Am I missing some functionality I am not aware of by skipping the section setting up: **/etc/hal/fdi/policy/mouse.fdi** ?

I notice doing a quick test in **xev** now that the sidebuttons and wheel sideclicks don't give a "button" output (oh, **xev|grep button** saves a lot of struggling to read xev's output)

Edit: Added the **/etc/hal/fdi/policy/mouse.fdi** file, rebooted and no difference, Xev still doesn't show those clicks as buttons. I have a feeling that this is a problem in Cedega, the button presses aren't detected. Might have time to test that later, still setting up the system.

Edit2: Just tested Cedega and those button presses are detected even though xev fails to report a button (lots of other output, just not a button). So is the HAL stuff actually needed ?

---

### Post by Valentini on 2009-07-21
Sorry for the slow reply :)

I've had to reinstall my Ubuntu as of late, because I messed too much with it, and ended up not being able to boot. Thus I had to reconfigure my mouse, and the configuration looked kinda like this:

When I booted Jaunty, my mouse was blazingly fast. I looked through the xorg.conf arguments, and found ConstantDeceleration, which did the trick. The higher the number, the slower the mouse.
This is the main reason why I use the hal stuff.

Instead of the mouse.fdi, I made 10-x11-Input.fdi and the content is:
```
<?xml version="1.0" encoding="UTF-8"?>

		<match key="info.product" string="Logitech G9 Laser Mouse">
			<merge key="input.x11_options.Resolution" type="string">3200</merge>
			<merge key="input.x11_options.ConstantDeceleration" type="string">5</merge>
			<merge key="input.x11_options.Buttons" type="string">9</merge>
			<merge key="input.x11_options.ButtonMapping" type="string">1 2 3 4 5 6 7 8 9</merge>
			<merge key="input.x11_options.ZAxisMapping" type="string">8 9</merge>
			<merge key="input.x11_options.Emulate3Buttons" type="string">false</merge>
		</match>
```

My .Xmodmap:
```
pointer = 1 2 3 4 5 8 9 6 7
```

My .xbindkeysrc is unchanged:
```
  "/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[left]""
  m:0x0 + b:6
  "/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[right]""
  m:0x0 + b:7
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Control_L]\[Page_Up]""
  m:0x0 + b:11
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Control_L]\[Page_Down]""
  m:0x0 + b:12
```

And I still love my G9 :)

[edit]
Btw. I think the reason why xev doesn't report mouse button press on side buttons and tilt, is because the get overridden by xbindkeysrc to send the keyboard events instead - alt+left/right and ctrl+page up/down.
[/edit]

---

### Post by Marcel-X on 2010-03-13
Just for the record.

My G9 mouse thumb buttons control the history in Firefox by default. For Nautilus, I had to modify .xbindkeysrc and .Xmodmap.

Unfortunately the history function only works in the top menu of Nautilus. In the folder and file view the buttons are registered as left mouse buttons.

---

