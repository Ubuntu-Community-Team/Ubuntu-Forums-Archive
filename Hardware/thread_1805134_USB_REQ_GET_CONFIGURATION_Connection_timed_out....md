---
title: "USB_REQ_GET_CONFIGURATION: Connection timed out..."
date: 2011-07-15
forum: Hardware
---

### Post by villnn on 2011-07-15
I'd hope to not have any problems with Ubuntu, but at least I'm learning more about the operating system.

Well, like most PC gamers, I own a console. I happen to own a PS3. I can play very well with the controller, however, I've been interested in using my mouse and keyboard to play.
So when I heard that something called the *[sixaxis emu]("http://diy-machine.blogspot.com/")* was released. I decided to check it out since it ran on Ubuntu.

After installing the program, everything went along smoothly until... my computer can't see my PS3 controller via USB.

I did a quick Google search, and I found out that the problem could be fixed by launching the application from the Terminal.

When I did that, I got *this* result:

 ```

 $ sixemugui
 USB_REQ_GET_CONFIGURATION: Connection timed out
 
```So I figured that I didn't install the controller drivers.

To remedy this, I thought installing  QtSixA would do the trick.

I attempt to pair the controller with the computer within the program, however, I receive *this* error:
```

USB_REQ_GET_CONFIGURATION: Connection timed out
USB_REQ_SET_CONFIGURATION: Connection timed out

```[I]Note: I was able to get the controller to work through USB in  Windows. In Mac OS X, I was able to get the controller to connect using  USB, and then bluetooth. I am on an iMac (early 2006).


[/I]EDIT: It turns out that it was my controller that wasn't working... I may have to spend $50 just to get it working, but the controller using functioning properly anyhow.

Uh-oh, another problem... Can't change the dongle's address, although all of the specifications are met...

---

