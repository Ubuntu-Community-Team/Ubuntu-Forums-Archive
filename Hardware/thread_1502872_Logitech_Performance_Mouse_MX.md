---
title: "Logitech Performance Mouse MX"
date: 2010-06-06
forum: Hardware
---

### Post by samuraiii on 2010-06-06
[FONT=Arial][SIZE=3]Hello to everybody,
i have one compatibility q[/SIZE][/FONT][FONT=Arial][SIZE=3]uestion... will [/SIZE][/FONT][B][FONT=Arial][SIZE=3]Logitech Performance Mouse MX work on ubuntu (don't want it to work fully - have dual-boot machine) I'm just concerned about that unified receiver to work with (only) mouse... 
thank for reply in advance
S
[/SIZE][/FONT][/B]

---

### Post by efflandt on 2010-06-06
The worst that could happen is that if it does not work, you might need to edit /lib/udev/rules.d/70-hid2hci.rules to change "hiddev*" to "hidraw*" in the Logitech section.  They changed that between 9.10 and 10.04, as a fix for someone, which broke it for some of us (I have diNovo Edge keyboard/mousepad).

---

### Post by darkerlink on 2010-06-21
I have 10.04 and it works out of the box. everything works except the thumb button and zoom button. They do nothing and I have not figured out a way to program them.:confused:

---

### Post by nochids on 2010-07-05
> **darkerlink said:**
> I have 10.04 and it works out of the box. everything works except the thumb button and zoom button. They do nothing and I have not figured out a way to program them.:confused:

I just bought the mouse tonight and am experiencing the same.  I would love it if someone has the answer.

Thanks.

Jason.

---

### Post by eumel on 2010-07-14
i just found this review of an app called btnx:

[http://www.linux.com/archive/feature/126295](http://www.linux.com/archive/feature/126295)

i also got the performance mx today and i love it.

it seems that the website [http://www.ollisalonen.com/btnx/](http://www.ollisalonen.com/btnx/) is down, but i sucessfully installed it while it in the ubuntu universe repo.

edit: notice that u have to run btnx-config as root user that configuration's can be stored. (they're lay in /etc/btnx/)

---

### Post by ilyatau on 2010-08-31
Hello,
I have a problem with this mouse. More correct problem with USB receiver. Ubuntu don't see this USB receiver. I need to do something with udev?

---

### Post by GrammatonCleric on 2010-09-15
Figured I'd chime in on this.  I have the Performance MX and have tried it on both 10.04 and 10.10.  The issue I have with it is that hangs or rather pauses randomly. If you let the mouse rest it seems to go to sleep and will take several seconds to wake the mouse. 

The mouse runs fine on OSX and Windows.  Pitty too I was thinking of pick up the Logitech K350 keyboard which also uses the same "unifying" receiver.

-GC

---

### Post by jjdarling on 2010-09-17
> **eumel said:**
> i just found this review of an app called btnx:

[http://www.linux.com/archive/feature/126295](http://www.linux.com/archive/feature/126295)

i also got the performance mx today and i love it.

it seems that the website [http://www.ollisalonen.com/btnx/](http://www.ollisalonen.com/btnx/) is down, but i sucessfully installed it while it in the ubuntu universe repo.

edit: notice that u have to run btnx-config as root user that configuration's can be stored. (they're lay in /etc/btnx/)

I just bought the Performance MX as well, and let me just say that out of the box (on 10.04) everything except zoom and the thumb button works. I installed this software and tried to program the zoom button, just to see how it worked. I tried to program it so that the thumb button would be the same as ctrl+shift+s, the key combo for the application switcher in Compiz.

It sort of worked, but it's all sorts of buggy. It acted like it kept holding down ctrl and shift, so that every keyboard character I typed was the same as typing ctrl+shift+[whatever], which made typing impossible. It also affected the mouse in weird ways, like highlighting large blocks of text every time I clicked on text.

I couldn't kill the process in the terminal, as typing a lot of characters was impossible. I was able to uninstall the software because I still had Ubuntu Software Center open as root, and then I rebooted and my computer was back to normal.

I'm guessing this project is pretty much dead, since the site isn't even up, so I don't expect this to be fixed, or any future support. I would look elsewhere to get those buttons programmed. Even if you don't though, it's a great mouse out of the box.

---

### Post by Xavier_To on 2010-10-14
I've found that the project moved to launchpad... Perhaps the repos changed and the bugs have been fixed...

[https://launchpad.net/btnx/](https://launchpad.net/btnx/)

**EDIT:**
Ignore that... didn't find anything on the Launchpad site except for links to the other website that's down....

---

### Post by Marcelo Ruiz on 2010-10-14
There are no files to download in the repo :(

---

### Post by TheSeanKelly on 2010-12-29
Regarding the holding modifier keys down problem, I too have experienced that.  However, a workaround is to assign actions to the left and right click buttons that don't do anything.  Thus, when these buttons are clicked, btnx checks to see what to do and it sees that no modifiers are pressed for this action, clearing the ones held down from a previous action.

---

### Post by Bazirker on 2011-02-22
So if this mouse doesn't have all buttons functioning in Ubuntu, what mice do?  My MX1000 has the same problems as described for this mouse, namely that not all the buttons work and the buggy btnx software seems to be the only way these days to get them.  Does anyone know of a high-end mouse that is fully supported using Ubuntu?

Not related to Ubuntu, but...does this mouse really work on glass?  My wife's desk is actually made of glass, and I hate mousepads.

---

### Post by Bazirker on 2011-03-08
> **Bazirker said:**
> So if this mouse doesn't have all buttons functioning in Ubuntu, what mice do?  My MX1000 has the same problems as described for this mouse, namely that not all the buttons work and the buggy btnx software seems to be the only way these days to get them.  Does anyone know of a high-end mouse that is fully supported using Ubuntu?

Not related to Ubuntu, but...does this mouse really work on glass?  My wife's desk is actually made of glass, and I hate mousepads.

Bought one.  Mouse is awesome, works on glass with no trouble at all.  I'm still working on figuring out which buttons work, but it appears that right/left/middle/forward/back/scroll all work out of the box.

---

### Post by tnt533 on 2011-03-28
Just bought one of these two days ago. Coming from a MX Revolution the only disappointment was the way they changed the charging scheme, ie; no cradle but a usb charging cord instead. I guess it's more portable? 

Nice mouse but just like everyone else I can't seem to figure out how to get the zoom and thumb button up and running under Ubuntu 10.10 AMD64 using btnx. The software sees the two buttons during detection but wont activate any key combo assigned to them. Very frustrating. I was able to map every single button on my MX Revolution with zero issues using btnx.

I'm wondering if someone with some programming chops would be willing to take the source code for btnx and continue dev on the project if Olli is truly done with it.

---

### Post by Bazirker on 2011-03-28
> **tnt533 said:**
> Just bought one of these two days ago. Coming from a MX Revolution the only disappointment was the way they changed the charging scheme, ie; no cradle but a usb charging cord instead. I guess it's more portable? 

Nice mouse but just like everyone else I can't seem to figure out how to get the zoom and thumb button up and running under Ubuntu 10.10 AMD64 using btnx. The software sees the two buttons during detection but wont activate any key combo assigned to them. Very frustrating. I was able to map every single button on my MX Revolution with zero issues using btnx.

I'm wondering if someone with some programming chops would be willing to take the source code for btnx and continue dev on the project if Olli is truly done with it.

I actually much prefer the new charging method, since now you can keep using the mouse even when the battery has died.

I'll put in another vote for btnx improvements.  One of these days I'll start programming outside of Matlab and will get things like this sorted out myself...

---

### Post by KaMZaTa on 2011-04-02
How can configure Logitech MX Revolution and MX Performance in Ubuntu 11.04? Before I used btnx but now with 11.04 seems dosn't work.

How can I do?

---

### Post by Riot@ct on 2011-04-20
But is possible change the DPI (on fly or not)?

is it a good buy?

Thank you!

---

### Post by Riot@ct on 2011-05-13
Any news? :D

---

### Post by captainron042 on 2011-05-25
I've had this mouse for about a year now. When I got it, there wasn't much advice on mapping the thumb buttons. I was hoping there might be some answers by now. :(

BTW, why would anyone prefer a charging station over corded usability while it's charging? I love it, because I consistently forgot to dock my previous mouse overnight and would have to dig out the old factory dell mouse. :/

---

### Post by magicfab on 2011-10-13
I've filed a bug here:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/873628](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/873628)

---

### Post by nLinked on 2011-10-26
> **GrammatonCleric said:**
> Figured I'd chime in on this.  I have the Performance MX and have tried it on both 10.04 and 10.10.  The issue I have with it is that hangs or rather pauses randomly. If you let the mouse rest it seems to go to sleep and will take several seconds to wake the mouse. 

The mouse runs fine on OSX and Windows.  Pitty too I was thinking of pick up the Logitech K350 keyboard which also uses the same "unifying" receiver.

-GC

Just read your post while deciding to get this mouse. It appears that pausing sleep issue has been fixed. Even though the firmware is the same, logitech can replace the mouse with the same mouse which doesn't go to sleep or pause. I read about it [here]("http://forums.logitech.com/t5/Mice-and-Pointing-Devices/Performance-MX-short-sleep-timeout-and-unifying-receiver-problem/td-p/392123/page/3").

---

### Post by jebus_beler on 2012-04-21
I'm considering getting this mouse to use with my desktop and am looking forward to it running on the dark glass the table is made of.  But I'm concerned that the DPI cannot be changed in Linux though I'm not sure what problems this presents in practice.  Is the mouse too sensitive?  Or is it that in linux you can't take full advantage of the high DPI the mouse is capable of?

Can someone who's owned this mouse comment on whether its a worthwhile buy for linux (its ~$70 on amazon I think).  If not anyone have a better recommendation?

thanks

---

### Post by nLinked on 2012-04-22
> **jebus_beler said:**
> I'm considering getting this mouse to use with my desktop and am looking forward to it running on the dark glass the table is made of.  But I'm concerned that the DPI cannot be changed in Linux though I'm not sure what problems this presents in practice.  Is the mouse too sensitive?  Or is it that in linux you can't take full advantage of the high DPI the mouse is capable of?

Can someone who's owned this mouse comment on whether its a worthwhile buy for linux (its ~$70 on amazon I think).  If not anyone have a better recommendation?

thanks

I have this mouse on Ubuntu and it's smooth. I just use Ubuntu's mouse settings to adjust it to my liking. The back and forward buttons work great, the hidden thumb button at the bottom where your thumb rests doesn't, but I haven't bothered making it work using that software on Ubuntu (btx mouse or something). Middle button works too. Best feature is the free rolling scroll wheel with the button to make it not free. I have no complaints of it. Used for 1 year so far.

---

### Post by jebus_beler on 2012-04-22
hi nLinked,

Thanks a lot for the info.  I'm leaning towards getting the mouse but if you understand it could you explain to me what exactly what the issue is with lack of DPI control in Linux?  I mean is there some preset DPI setting on the mouse and if so is it too high (DPI) or too low by default?  Ages ago I had a logitech gaming mouse (wired) and appreciated the higher sensitivity so if I'm gonna invest $70 on a mouse I'd like it to also have that enhanced sensitivity.  Otherwise I might try to find a mouse that has better linux support.

thanks

---

### Post by nLinked on 2012-04-25
Hmm, not sure about any DPI issues/settings. It just works when I plug it in. There's no button on the mouse to change the DPI, it's as it is. It's smooth on Ubuntu, all the changes I make are through Mouse in Settings in Ubuntu itself. Any speed you want at all can be acheieved and fine tuned in there, from very slow to very high. All I need really.

---

### Post by jebus_beler on 2012-04-27
Great.  Thanks for the info!

---

### Post by ldd on 2012-05-19
The issue is that the default resolution is at 800 (or so) DPI, when the mouse can do 1500. There is currently no way to change the DPI under any Linux distribution, as I've pointed out [here]("http://forums.logitech.com/t5/Mice-and-Pointing-Devices/Performance-Mouse-MX-and-others-Linux-support/td-p/835604").

---

### Post by nLinked on 2012-05-20
> **ldd said:**
> The issue is that the default resolution is at 800 (or so) DPI, when the mouse can do 1500. There is currently no way to change the DPI under any Linux distribution, as I've pointed out [here]("http://forums.logitech.com/t5/Mice-and-Pointing-Devices/Performance-Mouse-MX-and-others-Linux-support/td-p/835604").

This is getting quite some attention, news article [here]("http://www.omgubuntu.co.uk/2012/05/linux-users-ask-logitech-for-better-mouse-support").

---

### Post by 0815user on 2012-08-28
Here's some reverse engineered (rather hackish) code to set DPI values on the Performance MX.

It works here but, yeah, ymmv. Executable for x64 is attached for your convenience, you should rather compile it yourself and not trust some random stranger on some random message board though.


I'm using xbindkeys to switch to highest DPI value after pressing the zoom button:
```
"/usr/local/bin/performance_mx_dpi 16"
  m:0x0 + b:13 + release
```



Source at:
[http://derhofbauer.at/blog/blog/2012/08/28/logitech-performance-mx/]("http://derhofbauer.at/blog/blog/2012/08/28/logitech-performance-mx/")


Have fun!

---

