---
title: "sixaxis controllers recognised but not working (bluetooth or USB)"
date: 2008-03-23
forum: Hardware &amp; Laptops
---

### Post by qirtaiba on 2008-03-23
I am running Gutsy with the stock kernel 2.6.22-14.  I have sixaxis controllers from a PS3 and am trying to use them either as USB or bluetooth joysticks.  There is ample documentation about this which I have followed.  However although the controllers are recognised by the kernel and respond to the device file /dev/input/js0, none of the buttons work.

For example: I have run jsconfigurator, which should show me the buttons that I am pressing on the controller as I press them, but it doesn't. Similarly there is a program called js2key which ought to respond to a button press but won't (see [http://ubuntuforums.org/archive/index.php/t-646564.html](http://ubuntuforums.org/archive/index.php/t-646564.html)).  Finally when I run jstest --event which should show button presses as I make them, it doesn't.

Having said that, when I run Planet Penguin Racer, TuX spirals around like a loon, so obviously it thinks that I am pressing something even though I'm not, but nothing that I do press makes any difference.

Have searched the mailing list and Web archives to no avail.  Can anyone suggest what might be going on here?  Needless to say the controllers work on the PS3.

TIA

---

