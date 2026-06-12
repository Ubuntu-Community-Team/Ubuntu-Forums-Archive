---
title: "Apple Bluetooth Keyboard: Function key not recognised"
date: 2011-10-07
forum: Hardware
---

### Post by jafurther on 2011-10-07
Yesterday I bought a new Apple Wireless Keyboard. It connected easily via Bluetooth, but the function key doesn't work.

F1-F12 all function correctly as normal keys but can't be used as multimedia keys due to the function key not working. I'm using Maverick and have looked around for a solution but can't find one which works for me.

I've also tried this, but it didn't work for me: [https://help.ubuntu.com/community/AppleKeyboard]("https://help.ubuntu.com/community/AppleKeyboard"). I think I may have a new model which doesn't work with that method.

Thanks everyone. Hope there's a solution out there :)

EDIT: I am now using Oneiric, but the problem remains.

---

### Post by jafurther on 2011-10-09
Bump :/

---

### Post by hansdown on 2011-10-09
Hi jafurther.

Try the first link in this.

[http://www.google.com/search?client=ubuntu&channel=fs&q=Apple+Wireless+Keyboar+function+key+in+ubuntu+maverick&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=Apple+Wireless+Keyboar+function+key+in+ubuntu+maverick&ie=utf-8&oe=utf-8)

---

### Post by jafurther on 2011-10-09
You mean this? [http://ubuntuforums.org/showthread.php?t=224673&page=11](http://ubuntuforums.org/showthread.php?t=224673&page=11)

I've already tried putting hid_apple into my /etc/modules and rebooting, but I've had no luck. Thanks for your reply though.

---

### Post by hansdown on 2011-10-09
I was hoping, that this was the helpful solution, that would help.

Some of the other links, may be helpful.

*crosses fingers, and eyes, for good luck*

---

### Post by jafurther on 2011-10-09
I ran dmesg. Not sure if it'll be helpful, but this is what I thought relevant:
> [  577.107270] input: Apple Wireless Keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/bluetooth/hci0/hci0:32/input6
[  577.107534] generic-bluetooth 0005:05AC:0255.0003: input,hidraw2: BLUETOOTH HID v0.50 Keyboard [Apple Wireless Keyboard] on 00:15:83:15:A3:10
Every little bit counts, I guess.

---

### Post by hansdown on 2011-10-09
Yes, it does,jafurther.

Please see this.

[https://help.ubuntu.com/community/AppleKeyboard](https://help.ubuntu.com/community/AppleKeyboard)

---

### Post by jafurther on 2011-10-09
As I stated in my original post, I have tried the methods in that link. I'm not sure why it's not working.

Also, when I run xev in a Terminal, it doesn't detect that my function key being pressed at all but detects any other button I press.

---

### Post by jafurther on 2011-10-10
I found this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/227501](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/227501)

Following the instructions didn't work for me, maybe I read them wrong. If anyone could help me interpret them, that'd be great. I believe I have a similar problem to what's being described. Running hidd gives me this:
> Apple Wireless Keyboard [05ac:0255] connected

---

### Post by fmazanat on 2011-10-24
I bought one of those, too, can't make it work - tried to do the module compilation, but I'm not much of a kernel developer, so didn't get "make" to work...
Apparently, a new bug must be filled in order to get this new devide ID added to the module.

Cheers!

---

### Post by jafurther on 2011-10-24
Hey fmazanat,

It really is an annoying issue. Are you getting similar outputs to me?

---

### Post by codfather on 2011-12-11
Hi, which keyboard did you get , the little one?

I have literally just paired it via bluetooth and all the keys are working, including the multimedia and function keys, and I have done nothing except pair it. It is US keyboard, as I bought in Germany, and I couldn't get a UK versions. In fact this post is being written with it.

This is on a Dell E6400, with Ubuntu 11.10 fully patched up to today.

I did have a little fun and games getting it to initially pair, and it only worked when I told it to use pin options 0000, otherwise it was offering a custom number to pair.

Hope this helps your quest a little.

---

### Post by jafurther on 2011-12-11
Thanks for the reply codfather.

I'm using Oneiric now and I have paired the keyboard as per usual. The keyboard works perfectly except for the function + multimedia keys. The eject button works well though.

I live in Australia and that's where I bought the keyboard. However I don't imagine they could be too different. This is exactly what it looks like: [http://thebest-computers.com/wp-content/uploads/2011/06/apple-wireless-keyboards.jpg](http://thebest-computers.com/wp-content/uploads/2011/06/apple-wireless-keyboards.jpg)

Could you have installed a different version of something important like bluez that could have added the functionality?

---

### Post by Jasev on 2011-12-19
Hi all,

I can add some more info. I have a macbook from around early 2010 (running Ubuntu 11.10). The fn-keys work fine (ie multimedia work, fn-right = end, fn-left = home etc).

At the same time I purchased an Apple bluetooth keyboard. Again the fn keys work fine.

About 3 months ago I purchased a 2nd Apple blutooth keyboard for use at work and the fn key doesn't work properly. As mentioned here f1-f12 works, but not as multimedia keys. fn-arrow combinations etc also do not work.

By all outward appearance the 2 keyboards are the same, but Apple has obviously changed something internally and Ubuntu doesn't recongnise the fn-key on the new keyboards.

Hope this helps someone come up with a solution. I'm not a programmer but am happy to troubleshoot with both keyboards if required.

Cheers

Jase

PS I also purchased this keyboard from an Apple reseller in Australia.

---

### Post by Jasev on 2012-01-08
I have filed a bug report regarding this issue. See [https://bugs.launchpad.net/ubuntu/+bug/911064](https://bugs.launchpad.net/ubuntu/+bug/911064)

Similar bugs suggest the device ID has changed and the new ID needs to be added to the Kernel.

---

