---
title: "Apple keyboard on Dell PC"
date: 2010-03-05
forum: Hardware
---

### Post by dafi on 2010-03-05
I bought an Apple Aluminum wired keyboard for my Dell PC and everything works fine but I've two little issue.

I'm using Ubuntu Karmic Koala

First issue involves the function keys behavior

For example pressing F12 the volume is incremented and Ubuntu visually display the operation (very cool), to have the normal F12 key I need to press the Apple fn key.

Is it possible to invert this mapping?
Press fn+F12 increment volume
Press F12 normal behavior

Second issue

Scroll Lock and Print Screen keys are not available, I've read this document [http://support.apple.com/kb/HT1216](http://support.apple.com/kb/HT1216) but without success.

Any idea how to detect and then map these keys?

---

### Post by coffeecat on 2010-03-05
For the Fn-key issue, have a look here:

[https://help.ubuntu.com/community/AppleKeyboard](https://help.ubuntu.com/community/AppleKeyboard)

I've not tried the bit under "[SIZE=1]Change Function Key  behavior[/SIZE]" myself, and the page is a bit dated, but it might work.

There's also a method to assign scroll-lock to F15  and PrintScr to F14  in Intrepid. Whether that works for later versions, I don't know. Tbh,  until you posted I had forgotten about that link. I shall try it  forthwith! Alternatively, for Print Screen (and print window) you can  map your own preference with System > Preferences > Keyboard  Shortcuts.

> **dafi said:**
> I've read this document [http://support.apple.com/kb/HT1216](http://support.apple.com/kb/HT1216)  but without success.

If you look carefully they say "Apple Keyboard Support driver" which is a  Windows only driver so, unfortunately, it's not relevant to Linux. The  chart is for Windows running on a Mac under Bootcamp. The Windows  drivers are on the Apple DVD. I wanted to use an aluminium keyboard with  my Vista/Ubuntu multiboot and needed a Windows driver for Vista, and I  happen to have a Leopard DVD which I had purchased (legally) to upgrade  my Mac Mini. Windows couldn't detect the Windows drivers folder on the  Apple disc, MacOS wouldn't show it to me, but Ubuntu came to the rescue,  both showing and copying the relevant files for me quite happily. :cool:

> **dafi said:**
> For example pressing F12 the volume is incremented  and Ubuntu visually  display the operation (very cool),

You've obviously not yet accidentally hit the key immediately adjacent -  the CD eject key. I keep catching it every time I use the back delete  key and the optical drive tray pops out and hits me on the knee. :(

:wink:

---

### Post by dafi on 2010-03-05
> **coffeecat said:**
> For the Fn-key issue, have a look here:

[https://help.ubuntu.com/community/AppleKeyboard](https://help.ubuntu.com/community/AppleKeyboard)

I've not tried the bit under "[SIZE=1]Change Function Key  behavior[/SIZE]" myself, and the page is a bit dated, but it might work.



Wow it works fine

> 
There's also a method to assign scroll-lock to F15  and PrintScr to F14  in Intrepid. Whether that works for later versions, I don't know. Tbh,  until you posted I had forgotten about that link. I shall try it  forthwith! Alternatively, for Print Screen (and print window) you can  map your own preference with System > Preferences > Keyboard  Shortcuts.

Very strange but from System > Preferences > Keyboard  Shortcuts I can assign keys but they don't work also after logout and login again (but it should be not necessary)
I see the keycode 0xc0 assigned.

> 
If you look carefully they say "Apple Keyboard Support driver" which is a  Windows only driver so, unfortunately, it's not relevant to Linux. The  chart is for Windows running on a Mac under Bootcamp. The Windows  drivers are on the Apple DVD. I wanted to use an aluminium keyboard with  my Vista/Ubuntu multiboot and needed a Windows driver for Vista, and I  happen to have a Leopard DVD which I had purchased (legally) to upgrade  my Mac Mini. Windows couldn't detect the Windows drivers folder on the  Apple disc, MacOS wouldn't show it to me, but Ubuntu came to the rescue,  both showing and copying the relevant files for me quite happily. :cool:


I've a MacBookPro with SnowLeopard but I don't use any Windows version


> 
You've obviously not yet accidentally hit the key immediately adjacent -  the CD eject key. I keep catching it every time I use the back delete  key and the optical drive tray pops out and hits me on the knee. :(

:wink:

Honestly I've already accidentally pressed the eject key :P :P 

thanks a lot for your help

---

