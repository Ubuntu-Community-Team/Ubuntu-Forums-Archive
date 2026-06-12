---
title: "Support for Logitech G19 Keyboard"
date: 2009-07-26
forum: Hardware
---

### Post by IceRayn on 2009-07-26
Hello, I am contemplating buying a Logitech G19 Gaming Keyboard for it's screen, and was wondering about Ubuntu support. 8.10 is my main OS, Windows only booted once in a blue moon to play games. I was wondering about the support of the advanced things this keyboard can do on Linux. When searching for G19 Linux drivers, G19 Linux, and more, all I found was that the keyboard's LCD ran embedded Linux. I was wondering if Wine could do such  thing, or if I need to use something else such as Cedega or CrossOver to do it, or if it's impossible to use a "not emulator" to run it, and if it needs to be a native Linux application. If anyone can find an API of sorts that can be used to get support running, I would be happy to use what little knowledge of programming that I have to get it running.

Thank you,
IceRayn

---

### Post by Firebirdy on 2009-08-08
Hi IceRayn,

I have a G19 and I can tell you that right now it's not worth it for linux :(. You can also read what I wrote here: [http://www.linuxcompatible.org/g19_c14051.html](http://www.linuxcompatible.org/g19_c14051.html) - the only thing I can say is that as long as there are no drivers for it, it works as a normal keyboard and that you can get a default white backlight if you want.

There are G15 drivers but they're not compatible.

---

### Post by IceRayn on 2009-08-08
Thanks for your reply. I just might get it anyway, but probably not as I rarely boot into Windows.

---

### Post by MultiCoreNOP on 2010-04-18
there is a Python script

Using it (must have pyusb installed) you can control everything on your keyboard from setting backlight color to uploading images to your display.

[http://github.com/MultiCoreNop/Logitech-G19-Linux-Daemon](http://github.com/MultiCoreNop/Logitech-G19-Linux-Daemon)

Have fun!

---

### Post by sblatt on 2010-06-11
Also check out my fork of MulticoreNOP's driver:

[http://github.com/sblatt/Logitech-G19-Linux-Daemon](http://github.com/sblatt/Logitech-G19-Linux-Daemon)

and send me some feedback

---

### Post by Antebios on 2010-07-11
Woo-hoo!

---

### Post by tanktarta on 2010-10-10
Here is another project that wouldn't have been possible without MultiCoreNop's code :)

 [Gnome15]("http://www.tanktarta.pwp.blueyonder.co.uk/gnome15/") is a panel applet, macro recorder and set of plugins (media player, system monitor, rss reader and lots more) for the G15 and G19.

---

### Post by balta on 2010-11-20
Man this is great! hope it works well! 
if id does i'll sure donate something! i just keep getting blue screen of death on windows due the incompatibility of g19 and my processor (omg)
thanks thanks thanks

---

### Post by tanktarta on 2010-11-20
Glad you're giving it a try :)

One thing you should try and avoid using though is the multimedia keys (i.e. all those in the top right of the keyboard, including the volume control). 

Although support for these was added, there is a serious bug that will crash your entire system (to the point where powering off is the only option). This is being worked on.

There is no need for donation, other than code donations of course! If you have any skill in python, new plugins are welcome and there is a full plugin tutorial on the web site. If coding is not your thing, reporting bugs or requesting features help me out too.

Thanks

Brett

---

